---
layout: post
title: Unity 5 Retrospective
---
Over the past four months, I put around 25 hours a week in to my first formal Unity game.  During this time, I slowly came to the realization that some of Unity's biggest features aren't all that great.

<!--more-->

To give you some background, I've been using Unity for hobby ideas for a couple of years now and I've loved every minute of it.  Unity excels at making things both quick and easy.  It's prefab system coupled with it's component based architecture allow for some pretty complex behaviour with even the simplest of scripts.  I've also found that components help me organize my code better and result in a more "DRY" codebase.  That said, once you move past cool, interactive ideas, Unity starts to fall a little short.  Sadly, I can't help but feel this comes one of Unity's best qualities - it's heritage as an indie game development tool.

For example, Unity's prefab system is really great for establishing quick and dirty object configurations, but as things get more complex, you begin to realize that all prefabs are serialized and don't propagate changes once modified.  I'll give you a scenario: You create PrefabA.  You have an instance in a scene, but you need it to be a tad different than the version in the library, so you change it's scale and modify a property.  At this point, the relationship between the PrefabA instance and it's source have been broken.  You can then unknownlingy make configuration changes and find that they don't propagate to the slightly edited instances.  As you can imagine, large games end up having pretty complex scenes / hierarchies, leaving plenty of opportunities for the prefab system to fall apart.

Beyond that, Unity's UI system doesn't feel particularly robust either.  When it came to the initial setup, things were simple enough.  A slider here, text there, all was well.  As I delved farther, however, I found I have many issues layout out scene UI's based on UI prefabs similar to the issues above.  On top of that, instantiation, parenting, and position of UI prefabs is particularly complex.  Unity's new anchoring system makes for strange behaviours when using a code-first approach and I often found myself pretty frustrated.  Traditionally, UI's are a pain.  But some of this pain is relieved with familiarity.  Things like 'auto sizing', or standard width, height, aspect ratio boilerplate code that we're all used to seeing, however verbose, make things simple and clear.

Finally, peformance was abysmal when relying to heavily on costly instantiation operations.  I managed to alleviate instantiation issues with object queues that recycled intances when no longer in use.  Personally, I couldn't help but feel that Unity's prefabs encouraged costly instantiations and feel apart at doing so efficiently.

Overall, I couldn't help but feel like Unity is a bit myopic.  In my next game development adventures, I'll be taking a look at UE4 with hopes of broadening my game engine experience.

**tl;dr;**

+ Prefabs encourage delicate object compositions that break way too easily.
+ The UI system leaves much to be desired.
+ Prefab instantiation is costly.