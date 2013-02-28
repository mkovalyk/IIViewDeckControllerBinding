BTOUCH=/Developer/MonoTouch/usr/bin/btouch
BINDDIR=/src/bindingXBUILD=/Applications/Xcode.app/Contents/Developer/usr/bin/xcodebuildPROJECT_ROOT=IIViewDeckControllerSamplePROJECT=$(PROJECT_ROOT)/IIViewDeckController.xcodeprojTARGET=IIViewDeckController

all: IIViewDeckController.dll
libIIViewDeckController-i386.a:	$(XBUILD) -project $(PROJECT) -target $(TARGET) -sdk iphonesimulator -configuration Release clean build	-mv $(PROJECT_ROOT)/build/Release-iphonesimulator/lib$(TARGET).a $@libIIViewDeckController-armv7.a:	$(XBUILD) -project $(PROJECT) -target $(TARGET) -sdk iphoneos -arch armv7 -configuration Release clean build	-mv $(PROJECT_ROOT)/build/Release-iphoneos/lib$(TARGET).a $@libIIViewDeckControllerUniversal.a: libIIViewDeckController-armv7.a libIIViewDeckController-i386.a	lipo -create -output $@ $^IIViewDeckController.dll: AssemblyInfo.cs StructsAndEnums.cs APIDefinition.cs libIIViewDeckControllerUniversal.a	/Applications/Xcode.app/Contents/Developer/usr/bin/xcodebuild -unsafe --outdir=tmp -out:$@ APIDefinition.cs  StructsAndEnums.cs -x=AssemblyInfo.cs --link-with=libIIViewDeckControllerUniversal.a,libIIViewDeckControllerUniversal.a

clean:
	-rm -f *.a *.dll

