# Dotnet Publish inconsistency support for DotNetPublishFiles

Using `DotNetPublishFiles` to add files does not work with `dotnet publish`, but works with `dotnet build` and `dotnet msbuild`.

Examples using the mybrand.pubxml, the image *branding/mybrand/brand.png* should go to *wwwroot/images/brand.png* overriding the default one.

``` powershell
dotnet publish -c Release /p:PublishProfile=mybrand
```

``` powershell
dotnet build -c Release /p:DeployOnBuild=true /p:PublishProfile=mybrand
```

``` powershell
dotnet msbuild /p:DeployOnBuild=true /p:PublishProfile=mybrand /p:Configuration=Release
```

The first example using `dotnet publish` is the only that does not work.