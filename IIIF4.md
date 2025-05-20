# IIIF 3D on MorphoSource

This document describes the ways the [MorphoSource 3D Data Repository](https://www.morphosource.org/) supports [IIIF Presentation version 4](https://preview.iiif.io/api/prezi-4/presentation/4.0/model/). Presentation 4 enables flexible and powerful presentation of 3D assets with cameras, lights, and commenting annotations. If you are already using MorphoSource to upload 3D models, we also have documentation showing how to put this IIIF support into action by [creating and saving annotations](https://duke.atlassian.net/wiki/spaces/MD/pages/545259612/Creating+and+Saving+Annotations) and setting [initial model rotation](https://duke.atlassian.net/wiki/spaces/MD/pages/545357952/Initial+Model+Rotation). 

- [IIIF 3D on MorphoSource](#iiif-3d-on-morphosource)
  - [IIIF Feature Matrix and Examples](#iiif-feature-matrix-and-examples)
  - [Trying Out IIIF 4](#trying-out-iiif-4)
  - [IIIF 4 Manifests for MorphoSource Media](#iiif-4-manifests-for-morphosource-media)
  - [3D Viewer and Technical Details](#3d-viewer-and-technical-details)

## IIIF Feature Matrix and Examples

This table shows what IIIF 3D features are currently supported in MorphoSource's 3D viewer using the IIIF 3D TSG list of example 3D manifests. The manifest link will take you to the manifest JSON. The example link will take you to MorphoSource's 3D viewer and will display the content described by the manifest.

| Manifest | Supported? | Example
| :--- | :---: | :---: |
| 1. Basic model in scene | |
| [Single Model](https://raw.githubusercontent.com/IIIF/3d/main/manifests/1_basic_model_in_scene/model_origin.json) | ✅ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/1_basic_model_in_scene/model_origin.json)
| [Single Model with background color](https://raw.githubusercontent.com/IIIF/3d/main/manifests/1_basic_model_in_scene/model_origin_bgcolor) | ❌ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/1_basic_model_in_scene/model_origin_bgcolor.json)
| 4. Transform and position | |
| [Single Positioned Model](https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_position.json) | ✅ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_position.json)
| [Rotated Model](https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_rotate_position.json) | ✅ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_rotate_position.json)
| [Rotated Translated Model](https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_rotate_translate_position.json) | ✅ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_rotate_translate_position.json)
| [Translated Rotated Model](https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_translate_rotate_position.json) | ✅ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_translate_rotate_position.json)
| [Two Models with Scaling and Positioning](https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_translate_scale_position.json) | ✅ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_translate_scale_position.json)
| [Two Models with Translation, Scaling, and Positioning](https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_scale_position.json) | ✅ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_scale_position.json)
| [Two Models with Scaling, Translation, and Positioning](https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_scale_translate_position.json) | ✅ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_scale_translate_position.json)
| [Two Models with Left-Right Mirroring and Positioning](https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_negative_scale_position.json) | ✅ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/model_transform_negative_scale_position.json)
| [Whale Cranium and Mandible Positioned](https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/whale_cranium_and_mandible_position.json) | ✅ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/4_transform_and_position/whale_cranium_and_mandible_position.json)
| 9. Commenting Annotations | |
| [Single Model with Comment Annotations](https://raw.githubusercontent.com/IIIF/3d/main/manifests//9_commenting_annotations/astronaut_comment.json) | ✅ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/9_commenting_annotations/astronaut_comment.json)
| 10. Content State | |
| [Single Model with Comment Annotations and Custom Views Per Annotation](https://raw.githubusercontent.com/IIIF/3d/astronaut_comment_scope/manifests/10_content_state/astronaut_comment_scope.json) | ✅ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/astronaut_comment_scope/manifests/10_content_state/astronaut_comment_scope.json)
| [Whale Cranium and Mandible with Manifest-Level Comment Annotations](https://raw.githubusercontent.com/IIIF/3d/main/manifests/10_content_state/whale_comment_scope_content_state.json) | ❌ | [View](https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/main/manifests/10_content_state/whale_comment_scope_content_state.json)

✅ Works fully! &emsp;🟡 Some relevant features work &emsp;❌ Relevant feature(s) not yet supported

The full list of IIIF 3D TSG draft manifests is [here](https://github.com/IIIF/3d/tree/main/manifests). Groups of manifests not listed here aren't supported yet - for example, our viewer only supports cameras specified as part of custom annotation views and not for scenes overall. Some manifests have been excluded because they are malformed and need some improvements (see [this GitHub issue](https://github.com/IIIF/3d/issues/60)).

## Trying Out IIIF 4

You can view any IIIF 4 Presentation manifest with a URL in MorphoSource's viewer environment, which uses [Universal Viewer](https://github.com/UniversalViewer/universalviewer) and the 3D viewer [Aleph-R3F](https://github.com/aleph-viewer/aleph-r3f). In other words, you can use MorphoSource's viewer as a test sandbox to view your own IIIF 3D content. 

The MorphoSource viewer is publicly available at the URL:

https://www.morphosource.org/uv/uv.html

Viewing a manifest in the viewer is accomplished by appending a query parameter `#?manifest=` to the viewer URL above where the query parameter value is your manifest URL. As an example, if you have IIIF 3D content located at manifest URL:

https://raw.githubusercontent.com/IIIF/3d/astronaut_comment_scope/manifests/10_content_state/astronaut_comment_scope.json

Then the combined URL to view this manifest in the MorphoSource viewer environment is:

https://www.morphosource.org/uv/uv.html#?manifest=https://raw.githubusercontent.com/IIIF/3d/astronaut_comment_scope/manifests/10_content_state/astronaut_comment_scope.json

Clicking the above link will display the specified manifest content in MorphoSource's UV environment. If 3D content is detected, the Aleph-R3F viewer within UV will be loaded automatically. 

If you experience any issues, let us know by filing an issue or creating a discussion post. We are also active in the IIIF Slack, so reach out to us!  

## IIIF 4 Manifests for MorphoSource Media

MorphoSource serves IIIF Presentation 4 manifests for all preview content (3D models, CT scan volumes, 2D images, and video) hosted by the repository. For 3D content, MorphoSource supports [saving comment annotations](https://duke.atlassian.net/wiki/spaces/MD/pages/545259612/Creating+and+Saving+Annotations) for 3D models, with comment annotations included in the IIIF manifest for the 3D model. 

[Example MorphoSource media with comment annotations and interactive preview](https://www.morphosource.org/concern/media/000658129?locale=en)

[IIIF Presentation 4 manifest for media and comment annotations](https://www.morphosource.org/manifests/c255adf9-f3ee-49b0-b8ea-7cb64b670343?manifest=https://www.morphosource.org/manifests/c255adf9-f3ee-49b0-b8ea-7cb64b670343)

For more detail, see our documentation on on how MorphoSource [mobilizes preview content using IIIF](https://duke.atlassian.net/wiki/spaces/MD/pages/545128594/Mobilizing+Annotations+with+IIIF).

## 3D Viewer and Technical Details

MorphoSource uses the open source 3D viewer [Aleph-R3F](https://github.com/aleph-viewer/aleph-r3f) wrapped in [Universal Viewer](https://github.com/UniversalViewer/universalviewer) as a UV extension. Our support for IIIF 4 is in beta state, and we're using a few different experimental code branches to get there. Here are the relevant packages with links to GitHub code branches and experimental NPM package pages.

Aleph-R3F: [morphosource-prezi-4-beta branch on GitHub](https://github.com/aleph-viewer/aleph-r3f/tree/morphosource-prezi-4-beta)

Universal Viewer: [aleph-r3f-prezi-4-beta branch on GitHub](https://github.com/MorphoSource/universalviewer/tree/aleph-r3f-prezi-4-beta)

Manifesto.js: [get_more_content_and_transform_helpers branch on GitHub](https://github.com/IIIF-Commons/manifesto-3d/tree/get_more_content_and_transform_helpers) and [experimental 3d-manifesto-dev-test NPM package](https://www.npmjs.com/package/3d-manifesto-dev-test)

Manifold: [experimental manifold-3d-dev NPM package](https://www.npmjs.com/package/manifold-3d-dev)


