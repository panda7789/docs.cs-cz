---
title: "Vytvoření třídy GamePieceCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f000c1eed27acc16d158cb893cba876ea016277
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-the-gamepiececollection-class"></a>Vytvoření třídy GamePieceCollection
**GamePieceCollection** třídy je odvozena ze třídy obecné seznamu a zavádí metody pro snazší správu více **GamePiece** objekty.  
  
## <a name="creating-the-code"></a>Vytváření kódu  
 Konstruktoru **GamePieceCollection** třída inicializuje privátního člena *capturedIndex*. V tomto poli se používá ke sledování který herní kusů má v současné době zachycení myši.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 **ProcessInertia** a **kreslení** metody zjednodušit kód, je potřeba v hra [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) a [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metody pomocí vytváření výčtu všechny kameny v kolekci a volání metody odpovídající na každém **GamePiece** objektu.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 **UpdateFromMouse** metoda je volána také během herní aktualizace. Umožňuje jenom jednu část herní tak, aby měl myši zaznamenat nejdříve zkontrolujete, jestli aktuální zachytávání (pokud existuje) je stále v platnosti. Pokud ano, žádné další část je povoleno vyhledávat zachycení.  
  
 Pokud žádné část má v současné době zachycení, **UpdateFromMouse** metoda výčet každého jednotlivého herní z poslední první a zkontroluje, pokud tuto část sestavy myši zachycení. Pokud ano, že jeden stane aktuální zaznamenané část a žádné další zpracování probíhá. **UpdateFromMouse** metoda poslední položky v kolekci nejprve hledá tak, že pokud jsou dva kusy překryté, jeden s vyšší pořadí Z-order obdrží zachytávání. Pořadí Z-order není explicitní ani změnit; ho se řídí jednoduše tak, že pořadí, ve kterém jsou kameny přidány do kolekce.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a>Viz také  
 [Manipulace a nečinnost](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Použití manipulace a nečinnosti v aplikaci XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Vytvoření třídy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Vytvoření třídy Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
 [Výpis úplného kódu](../../../docs/framework/common-client-technologies/full-code-listings.md)
