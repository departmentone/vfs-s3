

```
        DefaultFileSystemManager defaultFileSystemManager = new DefaultFileSystemManager();
        VFS.setManager(defaultFileSystemManager);

        SS3FileProvider ss3FileProvider = new SS3FileProvider();

        defaultFileSystemManager.addProvider(SS3Constants.S3SCHEME, ss3FileProvider);

        defaultFileSystemManager.init();

        StaticUserAuthenticator auth = new StaticUserAuthenticator("", "<acces-key-ID>",
                "<secret-access-key>");
        FileSystemOptions opts = new FileSystemOptions();
        DefaultFileSystemConfigBuilder.getInstance().setUserAuthenticator(opts, auth);

        FileObject fileObject = defaultFileSystemManager
                .resolveFile(SS3Constants.S3SCHEME + "://<s3-host-amazonaws>/<bucket-name>/<file>.<ext>", opts);
```
