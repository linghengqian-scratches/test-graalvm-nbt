### Just for test https://github.com/apache/shardingsphere/pull/21109

## Also, as a validation of https://github.com/graalvm/native-build-tools/issues/213

- Just execute `./mvnw org.graalvm.buildtools:native-maven-plugin:compile-no-fork -Pnative -DskipTests` on the command line, or after uploading this git repository to GitHub, run GitHub Actions.

- There is no need to start the built native image, because the startup requires additional parameters. Just observe the build process to reproduce the error log.

- It should be noted that the mainclass `org.apache.shardingsphere.proxy.Bootstrap` has been located in `target/apache-shardingsphere-5.2.1-SNAPSHOT-shardingsphere-proxy-bin/lib/shardingsphere-proxy-bootstrap-5.2.1-SNAPSHOT.jar`

```shell
Executing [
/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/bin/java \
-XX:+UseParallelGC \
-XX:+UnlockExperimentalVMOptions \
-XX:+EnableJVMCI \
-Dtruffle.TrustAllTruffleRuntimeProviders=true \
-Dtruffle.TruffleRuntime=com.oracle.truffle.api.impl.DefaultTruffleRuntime \
-Dgraalvm.ForcePolyglotInvalid=true \
-Dgraalvm.locatorDisabled=true \
-Dsubstratevm.IgnoreGraalVersionCheck=true \
--add-exports=java.base/com.sun.crypto.provider=org.graalvm.nativeimage.builder \
--add-exports=java.base/jdk.internal.access.foreign=org.graalvm.nativeimage.builder \
--add-exports=java.base/jdk.internal.event=org.graalvm.nativeimage.builder \
--add-exports=java.base/jdk.internal.loader=org.graalvm.nativeimage.builder,org.graalvm.truffle \
--add-exports=java.base/jdk.internal.logger=org.graalvm.nativeimage.builder \
--add-exports=java.base/jdk.internal.misc=org.graalvm.nativeimage.builder,org.graalvm.nativeimage.objectfile \
--add-exports=java.base/jdk.internal.module=jdk.internal.vm.compiler,org.graalvm.nativeimage.base,org.graalvm.nativeimage.builder \
--add-exports=java.base/jdk.internal.org.objectweb.asm=org.graalvm.nativeimage.builder \
--add-exports=java.base/jdk.internal.perf=org.graalvm.nativeimage.builder \
--add-exports=java.base/jdk.internal.platform=org.graalvm.nativeimage.builder \
--add-exports=java.base/jdk.internal.ref=org.graalvm.nativeimage.builder,org.graalvm.nativeimage.objectfile \
--add-exports=java.base/jdk.internal.reflect=org.graalvm.nativeimage.builder \
--add-exports=java.base/jdk.internal.vm.annotation=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.invoke.util=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.net=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.nio.ch=org.graalvm.nativeimage.builder,org.graalvm.nativeimage.objectfile \
--add-exports=java.base/sun.reflect.annotation=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.reflect.generics.factory=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.reflect.generics.reflectiveObjects=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.reflect.generics.repository=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.reflect.generics.scope=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.reflect.generics.tree=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.security.jca=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.security.provider=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.security.ssl=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.security.util=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.security.x509=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.text.spi=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.util.calendar=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.util.cldr=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.util.locale.provider=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.util.locale=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.util.resources=org.graalvm.nativeimage.builder \
--add-exports=java.base/sun.util=org.graalvm.nativeimage.builder \
--add-exports=java.desktop/sun.java2d.pipe=org.graalvm.nativeimage.builder \
--add-exports=java.desktop/sun.java2d=org.graalvm.nativeimage.builder \
--add-exports=java.management/com.sun.jmx.mbeanserver=org.graalvm.nativeimage.builder \
--add-exports=java.management/sun.management=org.graalvm.nativeimage.builder,org.graalvm.nativeimage.pointsto \
--add-exports=java.xml.crypto/org.jcp.xml.dsig.internal.dom=org.graalvm.nativeimage.builder \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.aarch64=jdk.internal.vm.compiler,org.graalvm.nativeimage.builder,org.graalvm.nativeimage.objectfile \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.amd64=jdk.internal.vm.compiler,org.graalvm.nativeimage.builder,org.graalvm.nativeimage.objectfile \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.code.site=jdk.internal.vm.compiler,org.graalvm.nativeimage.builder,org.graalvm.nativeimage.llvm \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.code.stack=jdk.internal.vm.compiler,org.graalvm.nativeimage.builder \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.code=jdk.internal.vm.compiler,org.graalvm.nativeimage.builder,org.graalvm.nativeimage.llvm,org.graalvm.nativeimage.objectfile,org.graalvm.nativeimage.pointsto \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.common=jdk.internal.vm.compiler,org.graalvm.nativeimage.builder,org.graalvm.nativeimage.pointsto \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.hotspot.aarch64=jdk.internal.vm.compiler \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.hotspot.amd64=jdk.internal.vm.compiler \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.hotspot.riscv64=jdk.internal.vm.compiler \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.hotspot=jdk.internal.vm.compiler,org.graalvm.nativeimage.builder \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.meta=jdk.internal.vm.compiler,org.graalvm.nativeimage.builder,org.graalvm.nativeimage.llvm,org.graalvm.nativeimage.objectfile,org.graalvm.nativeimage.pointsto \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.riscv64=jdk.internal.vm.compiler \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.runtime=jdk.internal.vm.compiler,org.graalvm.nativeimage.builder,org.graalvm.nativeimage.pointsto \
--add-exports=jdk.internal.vm.ci/jdk.vm.ci.services=jdk.internal.vm.compiler,org.graalvm.nativeimage.builder \
--add-exports=jdk.jfr/jdk.jfr.events=org.graalvm.nativeimage.builder \
--add-exports=jdk.jfr/jdk.jfr.internal.handlers=org.graalvm.nativeimage.builder \
--add-exports=jdk.jfr/jdk.jfr.internal.jfc=org.graalvm.nativeimage.builder \
--add-exports=jdk.jfr/jdk.jfr.internal=org.graalvm.nativeimage.builder \
--add-exports=jdk.management/com.sun.management.internal=org.graalvm.nativeimage.builder \
-XX:+UseJVMCINativeLibrary \
-Xss10m \
-Xms1g \
-Xmx5825052672 \
-Djava.awt.headless=true \
-Dorg.graalvm.version=22.2.0 \
-Dcom.oracle.graalvm.isaot=true \
-Djava.system.class.loader=com.oracle.svm.hosted.NativeImageSystemClassLoader \
-Xshare:off \
-Djdk.internal.lambda.disableEagerInitialization=true \
-Djdk.internal.lambda.eagerlyInitialize=false \
-Djava.lang.invoke.InnerClassLambdaMetafactory.initializeLambdas=false \
-javaagent:/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/builder/svm.jar \
--module-path \
/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/truffle/truffle-api.jar:/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/builder/objectfile.jar:/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/builder/svm.jar:/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/builder/javacpp-shadowed.jar:/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/builder/javacpp-platform-specific-shadowed.jar:/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/builder/pointsto.jar:/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/builder/llvm-wrapper-shadowed.jar:/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/builder/svm-llvm.jar:/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/builder/llvm-platform-specific-shadowed.jar:/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/builder/native-image-base.jar \
--module \
org.graalvm.nativeimage.builder/com.oracle.svm.hosted.NativeImageGeneratorRunner \
-watchpid \
2593 \
-imagecp \
/home/runner/work/shardingsphere/shardingsphere \
-imagemp \
/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/library-support.jar \
-H:CLibraryPath=/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/clibraries/linux-amd64 \
-H:Path=/home/runner/work/shardingsphere/shardingsphere \
-H:FallbackThreshold=0 \
-H:Path=/home/runner/work/shardingsphere/shardingsphere/shardingsphere-distribution/shardingsphere-proxy-distribution/target \
-H:Name=apache-shardingsphere-proxy \
-H:Class=org.apache.shardingsphere.proxy.Bootstrap \
-H:+ReportExceptionStackTraces
]
WARNING: Unknown module: org.graalvm.nativeimage.llvm specified to --add-exports
WARNING: Unknown module: org.graalvm.nativeimage.llvm specified to --add-exports
WARNING: Unknown module: org.graalvm.nativeimage.llvm specified to --add-exports
========================================================================================================================
GraalVM Native Image: Generating 'apache-shardingsphere-proxy' (executable)...
========================================================================================================================
[1/7] Initializing...                                                                                    (0.0s @ 0.28GB)
Error: Main entry point class 'org.apache.shardingsphere.proxy.Bootstrap' neither found on the classpath nor on the modulepath.
classpath: '/home/runner/work/shardingsphere/shardingsphere'
modulepath: '/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/library-support.jar'
com.oracle.svm.core.util.UserError$UserException: Main entry point class 'org.apache.shardingsphere.proxy.Bootstrap' neither found on the classpath nor on the modulepath.
classpath: '/home/runner/work/shardingsphere/shardingsphere'
modulepath: '/opt/hostedtoolcache/graalvm-ce-java17-linux/22.2.0/x64/graalvm-ce-java17-22.2.0/lib/svm/library-support.jar'
	at org.graalvm.nativeimage.builder/com.oracle.svm.core.util.UserError.abort(UserError.java:72)
	at org.graalvm.nativeimage.builder/com.oracle.svm.hosted.NativeImageGeneratorRunner.buildImage(NativeImageGeneratorRunner.java:348)
	at org.graalvm.nativeimage.builder/com.oracle.svm.hosted.NativeImageGeneratorRunner.build(NativeImageGeneratorRunner.java:585)
	at org.graalvm.nativeimage.builder/com.oracle.svm.hosted.NativeImageGeneratorRunner.main(NativeImageGeneratorRunner.java:128)
Error: Image build request failed with exit status 1
com.oracle.svm.driver.NativeImage$NativeImageError: Image build request failed with exit status 1
	at com.oracle.svm.driver.NativeImage.showError(NativeImage.java:1716)
	at com.oracle.svm.driver.NativeImage.build(NativeImage.java:1413)
	at com.oracle.svm.driver.NativeImage.performBuild(NativeImage.java:1374)
	at com.oracle.svm.driver.NativeImage.main(NativeImage.java:1361)
```