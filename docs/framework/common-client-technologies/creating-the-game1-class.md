---
title: Vytvoření třídy Game1
ms.date: 03/30/2017
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
ms.openlocfilehash: ad3c8bc46bec137d0baf4eeec09bcd5ec277e71a
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086658"
---
# <a name="creating-the-game1-class"></a>Vytvoření třídy Game1
Jak se všechny projekty Microsoft XNA třídy Game1 je odvozena z [Microsoft.Xna.Framework.Game](/previous-versions/windows/xna/bb197040%28v%3dxnagamestudio.41%29) třídu, která poskytuje základní grafické zařízení inicializace, logika hry a vykreslení kódu pro architekturu XNA hry. Třídy Game1 je poměrně jednoduchý, protože většina práce v GamePiece a GamePieceCollection třídy.  
  
## <a name="creating-the-code"></a>Vytváření kódu  
 Soukromé členy třídy, které jsou tvořeny **GamePieceCollection** objekt pro uložení kameny, [GraphicsDeviceManager](/previous-versions/windows/xna/bb197317%28v%3dxnagamestudio.41%29) objektu a [SpriteBatch](/previous-versions/windows/xna/bb199034%28v%3dxnagamestudio.41%29) objektu se používá vykreslit kameny.  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 Během inicializace her tyto objekty jsou vytvořena instance.  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 Když [LoadContent](/previous-versions/windows/xna/bb975766%28v%3dxnagamestudio.41%29) metoda je volána, herní kusů jsou vytvořeny a přiřazeny **GamePieceCollection** objektu. Existují dva druhy kameny. Měřítko pro kusy se mírně změní, takže existují některé větší a některé menší kousky.  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 [Aktualizace](/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) metoda je volána opakovaně rozhraním XNA Framework během hry. [Aktualizace](/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) volání metod **ProcessInertia** a **UpdateFromMouse** metody na hry část kolekce. Tyto metody jsou popsané v [vytvoření třídy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 [Nakreslit](/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) metoda zkratka opakovaně rozhraním XNA Framework během hry. [Nakreslit](/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) metoda provádí vykreslování kameny voláním **nakreslit** metodu **GamePieceCollection** objektu. Tato metoda je popsaná v[vytvoření třídy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>Viz také  
 [Manipulace a nečinnost](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Použití manipulace a nečinnosti v aplikaci XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Vytvoření třídy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Vytvoření třídy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Výpis úplného kódu](../../../docs/framework/common-client-technologies/full-code-listings.md)
