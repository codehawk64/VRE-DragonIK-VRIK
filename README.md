[NOTE : This project runs in UE 5.3 in it's latest build but older engine examples are available in separate branches.]

A detailed gdoc write up to help with understanding the project structure and migrations. [A WIP document to be updated frequently]
https://docs.google.com/document/d/1lBZXVa9KB47oCXRmiiz43ZfMsmGO3EzsZ_RnlbxDPyE/edit?usp=sharing


Download and play with the executable windows build here : https://drive.google.com/file/d/1ErjLQvJfe0Fzi9ypqu5ptEJ7S7QFo9Jq/view?usp=share_link (Playing the demo doesn't require the DragonIK plugin, but running the project requires it)
How do I get set up?

Here is a raw video recording of me copying the relevant features from the vre-dragonik project into a fresh new vre sample project.[ https://drive.google.com/file/d/159t-Lt8ze5wIYDAjYoMmFCBBqOVnqXZ7/view?usp=share_link](https://www.youtube.com/watch?v=KZ9sqaCqjKY) But as a warning it's a bit outdated since it's recording. The gdoc will be more up to date in comparison.

Current compatible versions for template: Latest Engine Version (Template is not kept to as many compatible versions as the plugin itself).

    Right click on VRExpPluginExample.uproject and switch to your preferred (compatible) engine version.
    If project files did not automatically generate after switching, right click again and select "Generate Visual Studio Files"
    Open Solution and build - Or download the pre-built binary package from the forum thread for the engine version and place into the plugins directory.
    Run

You need to have visual studio installed and follow the UE4 setup guide for it: https://docs.unrealengine.com/latest/INT/Programming/Development/VisualStudioSetup/

This project is essentially the VRE example project but with a full body IK character added in. The arms and heads make use of the DragonIK solvers. There are other non-DragonIK related modifications to get a good final result. The tips listed down should help one get started.

Extra tips relevant to this project :

    All the relevant 3-point full body IK assets are put up in the "FullbodyIK" folder

    This project is just the VRE sample project with the VR IK added on top of it. Any VRE related problems and queries are best communicated with the VRE dev at discord.

    This project has 3-point IK, leg animations based on HMD movement, crouching adjustment, speed warping and height adjustment. This is the main reason it looks like there is a lot of things here.

    The actual 3-point IK is just done through the aim solver provided by the DragonIK plugin. In case your character uses the epic skeleton, you can use pretty much the same settings. If not, just renaming the bone names in the aim solver is enough.

    Apart from the fullbodyIK folder, the main blueprint side modifications are done in the BP_VR_Character (or the Vive_PawnCharacter in 4.27). The core events are present inside the "DragonIK related modifications" comment section. The relevant variabls and functions are put inside the DragonIK category.

    A minor modification is done in the GraspingHand blueprint (just adding the DragonIK_Hand_AnchorPoint empty component).

    The Yin_Skeleton_Animblueprint does the bulk of the dragonIK related work. You can even just copy this animbp directly into your project and change the skeleton to your own skeleton. Especially best if your character uses the epic skeleton.
