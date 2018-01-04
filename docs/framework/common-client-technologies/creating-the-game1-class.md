---
title: "Vytvoření třídy Game1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7453c4f650e2dcadd3b8fac27b66f4db97fa0136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-the-game1-class"></a>Vytvoření třídy Game1
Jak se všechny projekty Microsoft XNA Game1 třída odvozená z [Microsoft.Xna.Framework.Game](http://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) třídy, která poskytuje základní grafické zařízení inicializace, herní logiku a generování kódu pro XNA hry. Třídy Game1 je docela jednoduchá, protože většinu práce v GamePiece a GamePieceCollection třídy.  
  
## <a name="creating-the-code"></a>Vytváření kódu  
 Soukromé členy pro třídu obsahovat **GamePieceCollection** objekt pro uložení herní částí [GraphicsDeviceManager](http://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) objekt a [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) objekt použitý k vykreslení herní částí.  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 Během inicializace herní instalace těchto objektů.  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 Když [LoadContent](http://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) metoda je volána, herní součásti jsou vytvořeny a přiřazeny **GamePieceCollection** objektu. Existují dva typy herní částí. Měřítko pro vytvořené se mírně změní, které existují některé menší a některé větší částí.  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 [Aktualizace](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) metoda je volána opakovaně rozhraním XNA Framework spuštěného příslušnou hru. [Aktualizace](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) volání metod **ProcessInertia** a **UpdateFromMouse** metody na příslušnou hru část kolekce. Tyto metody jsou popsané v [vytvoření třídy Gamepiececollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 [Kreslení](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metoda zkratka opakovaně rozhraním XNA Framework spuštěného příslušnou hru. [Kreslení](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metoda provádí vykreslování kameny voláním **kreslení** metodu **GamePieceCollection** objektu. Tato metoda je popsaná v[vytvoření třídy Gamepiececollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>Viz také  
 [Manipulace a nečinnost](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Použití manipulace a nečinnosti v aplikaci XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Vytvoření třídy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Vytvoření třídy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Výpis úplného kódu](../../../docs/framework/common-client-technologies/full-code-listings.md)
