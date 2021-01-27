## From solution folder:


dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\somethingapi.pfx -p SomeCrypticPassword

dotnet dev-certs https --trust

docker build --pull -t somethingapi:https .

docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_Kestrel__Certificates__Default__Password="SomeCrypticPassword" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/somethingapi.pfx -v $env:USERPROFILE\.aspnet\https:/https/ somethingapi:https


> browse to https://localhost:8001/home/authenticate

> copy Bearer token string from JSON

> POST to https://localhost:8001//api/thingselse with Bearer token returned from previous service and x-www-form-url-encoded content e.g. name: example1, othername: example2

(Ctrl+C to stop)