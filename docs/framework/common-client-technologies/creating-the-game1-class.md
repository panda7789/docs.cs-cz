---
title: Vytvoření třídy Game1
ms.date: 03/30/2017
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
ms.openlocfilehash: 368da9df4dffc7017abb02888bc2eb2641f04b8b
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46472175"
---
# <a name="creating-the-game1-class"></a>Vytvoření třídy Game1
Jak se všechny projekty Microsoft XNA třídy Game1 je odvozena z [Microsoft.Xna.Framework.Game](https://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) třídu, která poskytuje základní grafické zařízení inicializace, logika hry a vykreslení kódu pro architekturu XNA hry. Třídy Game1 je poměrně jednoduchý, protože většina práce v GamePiece a GamePieceCollection třídy.  
  
## <a name="creating-the-code"></a>Vytváření kódu  
 Soukromé členy třídy, které jsou tvořeny **GamePieceCollection** objekt pro uložení kameny, [GraphicsDeviceManager](https://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) objektu a [SpriteBatch](https://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) objektu se používá vykreslit kameny.  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 Během inicializace her tyto objekty jsou vytvořena instance.  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 Když [LoadContent](https://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) metoda je volána, herní kusů jsou vytvořeny a přiřazeny **GamePieceCollection** objektu. Existují dva druhy kameny. Měřítko pro kusy se mírně změní, takže existují některé větší a některé menší kousky.  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 [Aktualizace](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) metoda je volána opakovaně rozhraním XNA Framework během hry. [Aktualizace](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) volání metod **ProcessInertia** a **UpdateFromMouse** metody na hry část kolekce. Tyto metody jsou popsané v [vytvoření třídy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 [Nakreslit](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metoda zkratka opakovaně rozhraním XNA Framework během hry. [Nakreslit](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metoda provádí vykreslování kameny voláním **nakreslit** metodu **GamePieceCollection** objektu. Tato metoda je popsaná v[vytvoření třídy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>Viz také  
 [Manipulace a nečinnost](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Použití manipulace a nečinnosti v aplikaci XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Vytvoření třídy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Vytvoření třídy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Výpis úplného kódu](../../../docs/framework/common-client-technologies/full-code-listings.md)
