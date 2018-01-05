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
# <a name="creating-the-gamepiececollection-class"></a><span data-ttu-id="e7349-102">Vytvoření třídy GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="e7349-102">Creating the GamePieceCollection Class</span></span>
<span data-ttu-id="e7349-103">**GamePieceCollection** třídy je odvozena ze třídy obecné seznamu a zavádí metody pro snazší správu více **GamePiece** objekty.</span><span class="sxs-lookup"><span data-stu-id="e7349-103">The **GamePieceCollection** class derives from the generic List class, and introduces methods to more easily manage multiple **GamePiece** objects.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="e7349-104">Vytváření kódu</span><span class="sxs-lookup"><span data-stu-id="e7349-104">Creating the Code</span></span>  
 <span data-ttu-id="e7349-105">Konstruktoru **GamePieceCollection** třída inicializuje privátního člena *capturedIndex*.</span><span class="sxs-lookup"><span data-stu-id="e7349-105">The constructor of the **GamePieceCollection** class initializes the private member *capturedIndex*.</span></span> <span data-ttu-id="e7349-106">V tomto poli se používá ke sledování který herní kusů má v současné době zachycení myši.</span><span class="sxs-lookup"><span data-stu-id="e7349-106">This field is used to track which of the game pieces currently has the mouse capture.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 <span data-ttu-id="e7349-107">**ProcessInertia** a **kreslení** metody zjednodušit kód, je potřeba v hra [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) a [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metody pomocí vytváření výčtu všechny kameny v kolekci a volání metody odpovídající na každém **GamePiece** objektu.</span><span class="sxs-lookup"><span data-stu-id="e7349-107">The **ProcessInertia** and the **Draw** methods simplify the code needed in the game [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) and [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) methods by enumerating all of the game pieces in the collection and calling the respective method on each **GamePiece** object.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 <span data-ttu-id="e7349-108">**UpdateFromMouse** metoda je volána také během herní aktualizace.</span><span class="sxs-lookup"><span data-stu-id="e7349-108">The **UpdateFromMouse** method is also called during game update.</span></span> <span data-ttu-id="e7349-109">Umožňuje jenom jednu část herní tak, aby měl myši zaznamenat nejdříve zkontrolujete, jestli aktuální zachytávání (pokud existuje) je stále v platnosti.</span><span class="sxs-lookup"><span data-stu-id="e7349-109">It enables only one game piece to have the mouse capture by first checking to see if the current capture (if any) is still in effect.</span></span> <span data-ttu-id="e7349-110">Pokud ano, žádné další část je povoleno vyhledávat zachycení.</span><span class="sxs-lookup"><span data-stu-id="e7349-110">If so, no other piece is allowed to check for capture.</span></span>  
  
 <span data-ttu-id="e7349-111">Pokud žádné část má v současné době zachycení, **UpdateFromMouse** metoda výčet každého jednotlivého herní z poslední první a zkontroluje, pokud tuto část sestavy myši zachycení.</span><span class="sxs-lookup"><span data-stu-id="e7349-111">If no piece currently has the capture, the **UpdateFromMouse** method enumerates each game piece from last to first, and checks to see if that piece reports a mouse capture.</span></span> <span data-ttu-id="e7349-112">Pokud ano, že jeden stane aktuální zaznamenané část a žádné další zpracování probíhá.</span><span class="sxs-lookup"><span data-stu-id="e7349-112">If so, that piece becomes the current captured piece, and no further processing takes place.</span></span> <span data-ttu-id="e7349-113">**UpdateFromMouse** metoda poslední položky v kolekci nejprve hledá tak, že pokud jsou dva kusy překryté, jeden s vyšší pořadí Z-order obdrží zachytávání.</span><span class="sxs-lookup"><span data-stu-id="e7349-113">The **UpdateFromMouse** method checks the last item in the collection first so that if two pieces are overlapped, the one with the higher Z-order will obtain the capture.</span></span> <span data-ttu-id="e7349-114">Pořadí Z-order není explicitní ani změnit; ho se řídí jednoduše tak, že pořadí, ve kterém jsou kameny přidány do kolekce.</span><span class="sxs-lookup"><span data-stu-id="e7349-114">Z-order is not explicit nor changeable; it is governed simply by the order in which game pieces are added to the collection.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a><span data-ttu-id="e7349-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7349-115">See Also</span></span>  
 [<span data-ttu-id="e7349-116">Manipulace a nečinnost</span><span class="sxs-lookup"><span data-stu-id="e7349-116">Manipulations and Inertia</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [<span data-ttu-id="e7349-117">Použití manipulace a nečinnosti v aplikaci XNA</span><span class="sxs-lookup"><span data-stu-id="e7349-117">Using Manipulations and Inertia in an XNA Application</span></span>](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [<span data-ttu-id="e7349-118">Vytvoření třídy GamePiece</span><span class="sxs-lookup"><span data-stu-id="e7349-118">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [<span data-ttu-id="e7349-119">Vytvoření třídy Game1</span><span class="sxs-lookup"><span data-stu-id="e7349-119">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
 [<span data-ttu-id="e7349-120">Výpis úplného kódu</span><span class="sxs-lookup"><span data-stu-id="e7349-120">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)
