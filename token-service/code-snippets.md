# Code Snippets

### Generating the access token

```
public Object generateToken() throws Exception {
	try {
		String client_id = clientId;
		String client_secret = clientSecret;
		String grant_type = "client_credentials";
		URL url = null;
		InputStream stream = null;
		HttpURLConnection urlConnection = null;
		url = new URL(generateTokenUrl);
		urlConnection = (HttpURLConnection) url.openConnection();
		urlConnection.setRequestMethod("POST");
		urlConnection.setDoOutput(true);
		String data = URLEncoder.encode("client_id", "UTF-8") + "=" + URLEncoder.encode(client_id, "UTF-8");
		data += "&" + URLEncoder.encode("client_secret", "UTF-8") + "=" + URLEncoder.encode(client_secret, "UTF-8");
		data += "&" + URLEncoder.encode("grant_type", "UTF-8") + "=" + URLEncoder.encode(grant_type, "UTF-8");
		urlConnection.connect();
		OutputStreamWriter wr = new OutputStreamWriter(urlConnection.getOutputStream());
		wr.write(data);
		wr.flush();
		stream = urlConnection.getInputStream();
		BufferedReader reader = new BufferedReader(new InputStreamReader(stream, "UTF-8"), 8);
		String result = reader.readLine();
		if (!NullOrEmptyUtil.isNullOrEmpty(result)) {
			return result;
		}
		return null;
	} catch (Exception e) {
		throw e;
	}
}
```

### **Decoding the access token**

```
String jwtToken = "eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJaWWVIMnR2UmtLS3o2dFhYRVo0R2RaQjh5a0FXOHNLWnoyUXlULU1vUEVFIn0.eyJleHAiOjE2MDA0MjYyNTksImlhdCI6MTYwMDMzOTg1OSwianRpIjoiYmI3MDQ0MmItYjcyYy00MTQ5LWE1OTYtMDc2ZDkyMTg5OTE0IiwiaXNzIjoiaHR0cHM6Ly90b2tlbnMuc2FoYW1hdGkub3JnLmluL2F1dGgvcmVhbG1zL3NhaGFtYXRoaSIsImF1ZCI6ImFjY291bnQiLCJzdWIiOiI4NjlkMmMxMC04MzBlLTQ1ZGYtYTQ1MS02MGIzYzExZWVmMDQiLCJ0eXAiOiJCZWFyZXIiLCJhenAiOiJ5b2RsZWVmaW5zb2Z0LWFhLXVhdCIsInNlc3Npb25fc3RhdGUiOiI3YTM1OWMwZS0zODYwLTQ4NjgtYjZhOS1hZGNhZmJjOGJjYjciLCJhY3IiOiIxIiwicmVhbG1fYWNjZXNzIjp7InJvbGVzIjpbIm9mZmxpbmVfYWNjZXNzIiwidW1hX2F1dGhvcml6YXRpb24iXX0sInJlc291cmNlX2FjY2VzcyI6eyJhY2NvdW50Ijp7InJvbGVzIjpbIm1hbmFnZS1hY2NvdW50IiwibWFuYWdlLWFjY291bnQtbGlua3MiLCJ2aWV3LXByb2ZpbGUiXX19LCJzY29wZSI6Im9wZW5pZCBlbWFpbCBwcm9maWxlIiwic3ViIjoiL2xvY2FsaG9zdCIsImVtYWlsX3ZlcmlmaWVkIjpmYWxzZSwibmJmIjoxNjAwMzM2Mzk1LCJjbGllbnRJZCI6InlvZGxlZWZpbnNvZnQtYWEtdWF0IiwiY2xpZW50SG9zdCI6IjQ5LjM3LjE5NS4zMiIsInJvbGVzIjoiQUEiLCJuYW1lIjoieW9kbGVlZmluc29mdC1hYS11YXQiLCJjeHAiOjE2MDgxOTg3OTUsInByZWZlcnJlZF91c2VybmFtZSI6InNlcnZpY2UtYWNjb3VudC15b2RsZWVmaW5zb2Z0LWFhLXVhdCIsImNsaWVudEFkZHJlc3MiOiI0OS4zNy4xOTUuMzIifQ.C5EYKFeTZs96vsaGMWix5ewYeh01TTMxCDJRYBY9Oh8_TgMMAjw7hyKYDcRTDoQNkEpf6W8O7BPkApMM9S9Ty3MGcbsAldKgNiLVtJy2cjvrLkUK0K98Vwy6M4NZNSHAPU7kWYb3-YOrCYJtC97JMJnSCNpcqKvscW0Lvbu6FvYvVZGrdFxi68aYK47pIWB9SaqG5SNs2HboVA_nYSSftDUKz9amNJNKWdy_UfOB1SSvIITylAdXkjVTabO3hS35GoruoBM07gIcIoItTgB7kc81pfuaOpSE9gc7MVRRoxS8AwE0ZiqA2h3Pui4UP-0PsgOI_ZgqGGrbwe7Hr1__vw";

System.out.println("------------ Decode JWT ------------");

String[] split_string = jwtToken.split("\\.");
String base64EncodedHeader = split_string[0];
String base64EncodedBody = split_string[1];
String base64EncodedSignature = split_string[2];

System.out.println("~~~~~~~~~ JWT Header ~~~~~~~");
Base64 base64Url = new Base64(true);
String header = new String(base64Url.decode(base64EncodedHeader));
System.out.println("JWT Header : " + header);

System.out.println("~~~~~~~~~ JWT Body ~~~~~~~");
String body = new String(base64Url.decode(base64EncodedBody));
System.out.println("JWT Body : " + body);
```
