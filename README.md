Build the project:

```bash
$ mvn install
```

Start Jetty Server:

```bash
$ mvn jetty:run
```

And it will throw exception:

```bash
Caused by: java.lang.RuntimeException: RESTEASY003935: Unable to instantiate InjectorFactory implementation.
    at org.jboss.resteasy.core.ResteasyDeploymentImpl.startInternal (ResteasyDeploymentImpl.java:229)
    at org.jboss.resteasy.core.ResteasyDeploymentImpl.start (ResteasyDeploymentImpl.java:90)
    at org.jboss.resteasy.plugins.server.servlet.ServletContainerDispatcher.init (ServletContainerDispatcher.java:144)
    at org.jboss.resteasy.plugins.server.servlet.FilterDispatcher.init (FilterDispatcher.java:47)
    at org.eclipse.jetty.servlet.FilterHolder.initialize (FilterHolder.java:134)
    at org.eclipse.jetty.servlet.ServletHandler.lambda$initialize$0 (ServletHandler.java:751)
    at org.eclipse.jetty.servlet.ServletHandler$$Lambda$367.0000000000000000.accept (Unknown Source)
    at java.util.Spliterators$ArraySpliterator.forEachRemaining (Spliterators.java:948)
    at java.util.stream.Streams$ConcatSpliterator.forEachRemaining (Streams.java:739)
    at java.util.stream.Streams$ConcatSpliterator.forEachRemaining (Streams.java:739)
    at java.util.stream.ReferencePipeline$Head.forEach (ReferencePipeline.java:658)
    at org.eclipse.jetty.servlet.ServletHandler.initialize (ServletHandler.java:744)
    at org.eclipse.jetty.servlet.ServletContextHandler.startContext (ServletContextHandler.java:360)
    at org.eclipse.jetty.webapp.WebAppContext.startWebapp (WebAppContext.java:1445)
    at org.eclipse.jetty.maven.plugin.JettyWebAppContext.startWebapp (JettyWebAppContext.java:328)
    at org.eclipse.jetty.webapp.WebAppContext.startContext (WebAppContext.java:1409)
    at org.eclipse.jetty.server.handler.ContextHandler.doStart (ContextHandler.java:822)
    at org.eclipse.jetty.servlet.ServletContextHandler.doStart (ServletContextHandler.java:275)
    at org.eclipse.jetty.webapp.WebAppContext.doStart (WebAppContext.java:524)
    at org.eclipse.jetty.maven.plugin.JettyWebAppContext.doStart (JettyWebAppContext.java:397)
    at org.eclipse.jetty.util.component.AbstractLifeCycle.start (AbstractLifeCycle.java:72)
    at org.eclipse.jetty.util.component.ContainerLifeCycle.start (ContainerLifeCycle.java:169)
    at org.eclipse.jetty.util.component.ContainerLifeCycle.doStart (ContainerLifeCycle.java:117)
    at org.eclipse.jetty.server.handler.AbstractHandler.doStart (AbstractHandler.java:100)
    at org.eclipse.jetty.util.component.AbstractLifeCycle.start (AbstractLifeCycle.java:72)
    at org.eclipse.jetty.util.component.ContainerLifeCycle.start (ContainerLifeCycle.java:169)
    at org.eclipse.jetty.util.component.ContainerLifeCycle.doStart (ContainerLifeCycle.java:117)
    at org.eclipse.jetty.server.handler.AbstractHandler.doStart (AbstractHandler.java:100)
    at org.eclipse.jetty.util.component.AbstractLifeCycle.start (AbstractLifeCycle.java:72)
    at org.eclipse.jetty.util.component.ContainerLifeCycle.start (ContainerLifeCycle.java:169)
    at org.eclipse.jetty.server.Server.start (Server.java:407)
    at org.eclipse.jetty.util.component.ContainerLifeCycle.doStart (ContainerLifeCycle.java:110)
    at org.eclipse.jetty.server.handler.AbstractHandler.doStart (AbstractHandler.java:100)
    at org.eclipse.jetty.server.Server.doStart (Server.java:371)
    at org.eclipse.jetty.util.component.AbstractLifeCycle.start (AbstractLifeCycle.java:72)
    at org.eclipse.jetty.maven.plugin.AbstractJettyMojo.startJetty (AbstractJettyMojo.java:450)
    at org.eclipse.jetty.maven.plugin.AbstractJettyMojo.execute (AbstractJettyMojo.java:311)
    at org.eclipse.jetty.maven.plugin.JettyRunMojo.execute (JettyRunMojo.java:152)
    at org.apache.maven.plugin.DefaultBuildPluginManager.executeMojo (DefaultBuildPluginManager.java:137)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:210)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:156)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:148)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject (LifecycleModuleBuilder.java:117)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject (LifecycleModuleBuilder.java:81)
    at org.apache.maven.lifecycle.internal.builder.singlethreaded.SingleThreadedBuilder.build (SingleThreadedBuilder.java:56)
    at org.apache.maven.lifecycle.internal.LifecycleStarter.execute (LifecycleStarter.java:128)
    at org.apache.maven.DefaultMaven.doExecute (DefaultMaven.java:305)
    at org.apache.maven.DefaultMaven.doExecute (DefaultMaven.java:192)
    at org.apache.maven.DefaultMaven.execute (DefaultMaven.java:105)
    at org.apache.maven.cli.MavenCli.execute (MavenCli.java:956)
    at org.apache.maven.cli.MavenCli.doMain (MavenCli.java:288)
    at org.apache.maven.cli.MavenCli.main (MavenCli.java:192)
    at jdk.internal.reflect.NativeMethodAccessorImpl.invoke0 (Native Method)
    at jdk.internal.reflect.NativeMethodAccessorImpl.invoke (NativeMethodAccessorImpl.java:62)
    at jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke (DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke (Method.java:566)
    at org.codehaus.plexus.classworlds.launcher.Launcher.launchEnhanced (Launcher.java:282)
    at org.codehaus.plexus.classworlds.launcher.Launcher.launch (Launcher.java:225)
    at org.codehaus.plexus.classworlds.launcher.Launcher.mainWithExitCode (Launcher.java:406)
    at org.codehaus.plexus.classworlds.launcher.Launcher.main (Launcher.java:347)
Caused by: java.lang.RuntimeException: RESTEASY010605: Unable to lookup BeanManager.
    at org.jboss.resteasy.cdi.CdiInjectorFactory.lookupBeanManager (CdiInjectorFactory.java:176)
    at org.jboss.resteasy.cdi.CdiInjectorFactory.<init> (CdiInjectorFactory.java:47)
...
```

Remove the `resteasy-client-microprofile` dependency in `pom.xml`:

```xml
<dependency>
    <groupId>org.jboss.resteasy</groupId>
    <artifactId>resteasy-client-microprofile</artifactId>
    <version>${resteasy.version}</version>
</dependency>
``` 

Re-run the Jetty server and everything goes fine:

```bash
...
WARN: RESTEASY002155: Provider class org.jboss.resteasy.plugins.providers.MultiValuedParamConverterProvider is already registered.  2nd registration is being ignored.
12月 20, 2019 4:30:47 下午 org.jboss.resteasy.core.providerfactory.ResteasyProviderFactoryImpl registerProvider
WARN: RESTEASY002155: Provider class org.jboss.resteasy.plugins.providers.DocumentProvider is already registered.  2nd registration is being ignored.
[INFO] Started o.e.j.m.p.JettyWebAppContext@-4d040aa9{Archetype Created Web Application,/,file:///Users/weli/works/Resteasy2461Reproducer/src/main/webapp/,AVAILABLE}{file:///Users/weli/works/Resteasy2461Reproducer/src/main/webapp/}
[INFO] Started ServerConnector@aeca7f4a{HTTP/1.1,[http/1.1]}{0.0.0.0:8080}
[INFO] Started @2125ms
[INFO] Started Jetty Server
``` 


