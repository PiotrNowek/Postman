## JavaScript Skills Showcase

This repository contains selected projects demonstrating my JavaScript expertise, including practical examples from the 15-day Postman challenge. It aims to highlight my ability to write clean, efficient, and maintainable code. 

## Example 1
```javascript
"item": [
		{
			"name": "More tests",
			"item": [
				{
					"name": "xkcd",
					"event": [
						{
							"listen": "test",
							"script": {
								"exec": [
									"const skipTest = true;\r",
									"\r",
									"pm.test(\"Status code is 200\", function () {\r",
									"    pm.response.to.have.status(200);\r",
									"    pm.execution.setNextRequest(\"xkcd\");\r",
									"});\r",
									"\r",
									"(skipTest ? pm.test.skip : pm.test)(\"Check status code is not 404\", () => {\r",
									"    pm.expect(pm.response.code).to.be.equal(404);\r",
									"\t\tpm.test.skip(\"Status code is 404 - skip test\")\r",
									"});\r",
									""
								],
								"type": "text/javascript",
								"packages": {}
							}
						}
					],
					"request": {
						"method": "GET",
						"header": [],
						"url": {
							"raw": "https://xkcd.com/:page/info.0.json",
							"protocol": "https",
							"host": [
								"xkcd",
								"com"
							],
							"path": [
								":page",
								"info.0.json"
							],
							"variable": [
								{
									"key": "page",
									"value": "{{$randomAlphaNumeric}}"
								}
							]
						}
					},
					"response": []
				}
			],
```
## Example 2
```javascript
"item": [
		{
			"name": "Output test results",
			"item": [
				{
					"name": "Variables and scripts",
					"item": [
						{
							"name": "get Canadian user",
							"event": [
								{
									"listen": "test",
									"script": {
										"exec": [
											"let jsonData = pm.response.json();\r",
											"\r",
											"let firstName = jsonData.results[0].name.first;\r",
											"pm.collectionVariables.set(\"firstName\", firstName);\r",
											"\r",
											"let lastName = jsonData.results[0].name.last;\r",
											"pm.collectionVariables.set(\"lastName\", lastName);\r",
											"\r",
											"let fullName = firstName + \" \" + lastName;\r",
											"pm.collectionVariables.set(\"firstuser\", fullName);\r",
											"\r",
											"let email = jsonData.results[0].email;\r",
											"pm.collectionVariables.set(\"email\", email);\r",
											"\r",
											"let uuid = jsonData.results[0].login.uuid;\r",
											"pm.collectionVariables.set(\"uuid\", uuid);"
										],
										"type": "text/javascript",
										"packages": {}
									}
								}
							],
							"request": {
								"method": "GET",
								"header": [],
								"url": {
									"raw": "https://randomuser.me/api?nat=CA",
									"protocol": "https",
									"host": [
										"randomuser",
										"me"
									],
									"path": [
										"api"
									],
									"query": [
										{
											"key": "nat",
											"value": "CA"
										}
									]
								}
							},
							"response": []
						},
						{
							"name": "echo the user",
							"event": [
								{
									"listen": "test",
									"script": {
										"exec": [
											"pm.test(`Returns correct email: ${pm.collectionVariables.get('email')}`, function () {\r",
											"let jsonData = pm.response.json();\r",
											"let email = jsonData.email;\r",
											"\r",
											"pm.expect(email).to.eql(pm.collectionVariables.get(\"{{email}}\"));\r",
											"\r",
											"console.log(pm.collectionVariables.get(\"firstName\"));\r",
											"console.log(pm.collectionVariables.get(\"lastName\"));\r",
											"\r",
											"if (pm.response.code === 200) {\r",
											"pm.collectionVariables.unset(\"firstuser\");\r",
											"pm.collectionVariables.unset(\"firstName\"); \r",
											"pm.collectionVariables.unset(\"lastName\"); \r",
											"pm.collectionVariables.unset(\"email\");\r",
											"pm.collectionVariables.unset(\"uuid\");\r",
											"}\r",
											"})"
										],
										"type": "text/javascript",
										"packages": {}
									}
								}
							],
							"request": {
								"method": "POST",
								"header": [],
								"body": {
									"mode": "raw",
									"raw": "    {\r\n    \"name\": \"{{firstuser}}\",\r\n    \"email\": \"{{email}}\",\r\n    \"uuid\": \"{{uuid}}\"\r\n    }",
									"options": {
										"raw": {
											"language": "json"
										}
									}
								},
								"url": {
									"raw": "https://postman-echo.com/post",
									"protocol": "https",
									"host": [
										"postman-echo",
										"com"
									],
									"path": [
										"post"
									]
								}
							},
							"response": []
						}
					],
```

If you have any feedback or suggestions, feel free to reach out. I'm always open to refining my skills and improving the quality of my work. 

I’m excited to explore new opportunities and collaborate on innovative projects!

