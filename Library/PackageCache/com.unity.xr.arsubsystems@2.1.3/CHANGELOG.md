# Changelog
All notable changes to this package will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [2.1.3] - 2020-10-06
### Fixes
- Fixed an issue which could throw an exception when subsystems were run in the Editor (e.g., for simulation or remoting). This could happen when a trackable (e.g., a plane or anchor) was removed. This did not affect Player builds (i.e., on device). This is an example of the exception and associated callstack:
<pre>
NullReferenceException: Object reference not set to an instance of an object
Unity.Collections.LowLevel.Unsafe.AtomicSafetyHandle.CheckReadAndThrow (Unity.Collections.LowLevel.Unsafe.AtomicSafetyHandle handle)
Unity.Collections.NativeArray`1[T].Copy (Unity.Collections.NativeArray`1[T] src, Unity.Collections.NativeArray`1[T] dst)
Unity.Collections.NativeArray`1[T].CopyFrom (Unity.Collections.NativeArray`1[T] array)
UnityEngine.XR.ARSubsystems.TrackableChanges`1[T]..ctor (System.Void* addedPtr, System.Int32 addedCount, System.Void* updatedPtr, System.Int32 updatedCount, System.Void* removedPtr, System.Int32 removedCount, UnityEngine.XR.ARSubsystems.XRReferencePoint defaultT, System.Int32 stride, Unity.Collections.Allocator allocator)
...
</pre>
- Fixed a bug in [`TrackableChanges`](https://docs.unity3d.com/Packages/com.unity.xr.arsubsystems@2.1/api/UnityEngine.XR.ARSubsystems.TrackableChanges-1.html) where [`isCreated`](https://docs.unity3d.com/Packages/com.unity.xr.arsubsystems@2.1/api/UnityEngine.XR.ARSubsystems.TrackableChanges-1.html#UnityEngine_XR_ARSubsystems_TrackableChanges_1_isCreated) remained `true` even after the container was [disposed](https://docs.unity3d.com/Packages/com.unity.xr.arsubsystems@2.1/api/UnityEngine.XR.ARSubsystems.TrackableChanges-1.html#UnityEngine_XR_ARSubsystems_TrackableChanges_1_Dispose).
- Fix [XRReferenceImageLibraries](xref:UnityEngine.XR.ARSubsystems.XRReferenceImageLibrary) when duplicated from an existing reference image library. Reference image libraries are assigned unique GUIDs on creation, so if you created one by duplicating an existing library, they would have identical GUIDs. The actual reference image library used at runtime was not well defined in this case. 

## [2.1.2] - 2020-03-03
### Improvements
- Added X icon to thumbnails of image tracking reference images.

## [2.1.1] - 2019-06-25
### Improvements
- Fix `CameraFocusMode` handling in `XRCameraSubsystem`.  This fixes an issue when running on a provider that does not set the default focus mode to `CameraFocusMode.Fixed`.

## [2.1.0] - 2019-06-25
- 2019.3 verified release

### New
- Add support for `NotTrackingReason`.

## [2.1.0-preview.3] - 2019-06-17
### Improvements
- Added functionality to the `XRSessionSubsystem` to enable synchronizing the Unity frame with the AR session update. See `XRSessionSubsystem.matchFrameRate` and `XRSessionSubsystem.frameRate`.

## [2.1.0-preview.2] - 2019-05-16
### Fixes
- Fix documentation links.

## [2.1.0-preview.1] - 2019-05-06
### New
- Add an image tracking subsystem.
- Add an environment probe subsystem.
- Add a face tracking subystem.
- Add an object tracking subsystem for detecting previously scanned 3D objects.

## [2.0.1] - 2019-03-12
- 2019.2 verified release

## [1.0.0-preview.1] - 2019-01-14
- This is the first release of *Unity Package com.unity.xr.subsystems.
