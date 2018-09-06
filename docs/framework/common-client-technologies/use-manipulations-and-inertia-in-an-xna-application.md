---
title: Použití manipulace a nečinnosti v aplikaci XNA
ms.date: 03/30/2017
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
ms.openlocfilehash: 70b8d0c5c098089b6f16ef817ff86698f68cf7c3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871041"
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="1e0c9-102">Použití manipulace a nečinnosti v aplikaci XNA</span><span class="sxs-lookup"><span data-stu-id="1e0c9-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="1e0c9-103">Tento článek popisuje, jak řídit přesun kameny můžete manipulace a nečinnosti v aplikaci Microsoft XNA zpracování.</span><span class="sxs-lookup"><span data-stu-id="1e0c9-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="1e0c9-104">Předtím, než se pustíte do čtení tohoto článku, měli byste se seznámit s [přehled manipulace a nečinnosti](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) tématu a znáte základní koncepty programování XNA.</span><span class="sxs-lookup"><span data-stu-id="1e0c9-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="1e0c9-105">K provedení úloh popsaných v tomto článku, váš projekt XNA musí odkazovat <xref:System.Windows.Input.Manipulations> sestavení a musí mít [sadu XNA Game Studio](https://msdn.microsoft.com/library/bb200104.aspx) ([Stáhnout](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) nainstalovaný ve vašem počítači tak vaše Projekt může odkazovat na sestavení XNA.</span><span class="sxs-lookup"><span data-stu-id="1e0c9-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](https://msdn.microsoft.com/library/bb200104.aspx) ([download](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="1e0c9-106">Přehled funkcí</span><span class="sxs-lookup"><span data-stu-id="1e0c9-106">Overview of Functionality</span></span>  
 <span data-ttu-id="1e0c9-107">V tomto článku se dozvíte, jak vytvořit vlastní třídu, která představuje her část, která používá manipulace a nečinnost zpracování.</span><span class="sxs-lookup"><span data-stu-id="1e0c9-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="1e0c9-108">Tato třída umožňuje manipulaci s her napříč obrazovkou pomocí přetahování myší a pak uvolníte.</span><span class="sxs-lookup"><span data-stu-id="1e0c9-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="1e0c9-109">Po vydání nečinnost zpracování udržuje her část, protože postupný přechod může zpomalit.</span><span class="sxs-lookup"><span data-stu-id="1e0c9-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="1e0c9-110">Přesun je lineární a angular.</span><span class="sxs-lookup"><span data-stu-id="1e0c9-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="1e0c9-111">![Jednoduchý manipulace a nečinnost aplikace. ](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="1e0c9-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="1e0c9-112">Kromě toho se vytvoří vlastní kolekce, která spravuje her na více místech.</span><span class="sxs-lookup"><span data-stu-id="1e0c9-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="1e0c9-113">Tato funkce usnadňuje zpracování, které je nutné ze třídy přenos hry XNA.</span><span class="sxs-lookup"><span data-stu-id="1e0c9-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="1e0c9-114">Vytvoření třídy GamePiece</span><span class="sxs-lookup"><span data-stu-id="1e0c9-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="1e0c9-115">Vytvoření třídy GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="1e0c9-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="1e0c9-116">Vytvoření třídy Game1</span><span class="sxs-lookup"><span data-stu-id="1e0c9-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="1e0c9-117">Výpis úplného kódu</span><span class="sxs-lookup"><span data-stu-id="1e0c9-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="1e0c9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e0c9-118">See Also</span></span>  
 <xref:System.Windows.Input.Manipulations>  
 [<span data-ttu-id="1e0c9-119">Přehled manipulace a nečinnosti</span><span class="sxs-lookup"><span data-stu-id="1e0c9-119">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
