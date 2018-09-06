---
title: Použití manipulace a nečinnosti v aplikaci XNA
ms.date: 03/30/2017
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
ms.openlocfilehash: 70b8d0c5c098089b6f16ef817ff86698f68cf7c3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734600"
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="02ff4-102">Použití manipulace a nečinnosti v aplikaci XNA</span><span class="sxs-lookup"><span data-stu-id="02ff4-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="02ff4-103">Tento článek popisuje, jak řídit přesun kameny můžete manipulace a nečinnosti v aplikaci Microsoft XNA zpracování.</span><span class="sxs-lookup"><span data-stu-id="02ff4-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="02ff4-104">Předtím, než se pustíte do čtení tohoto článku, měli byste se seznámit s [přehled manipulace a nečinnosti](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) tématu a znáte základní koncepty programování XNA.</span><span class="sxs-lookup"><span data-stu-id="02ff4-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="02ff4-105">K provedení úloh popsaných v tomto článku, váš projekt XNA musí odkazovat <xref:System.Windows.Input.Manipulations> sestavení a musí mít [sadu XNA Game Studio](https://msdn.microsoft.com/library/bb200104.aspx) ([Stáhnout](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) nainstalovaný ve vašem počítači tak vaše Projekt může odkazovat na sestavení XNA.</span><span class="sxs-lookup"><span data-stu-id="02ff4-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](https://msdn.microsoft.com/library/bb200104.aspx) ([download](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="02ff4-106">Přehled funkcí</span><span class="sxs-lookup"><span data-stu-id="02ff4-106">Overview of Functionality</span></span>  
 <span data-ttu-id="02ff4-107">V tomto článku se dozvíte, jak vytvořit vlastní třídu, která představuje her část, která používá manipulace a nečinnost zpracování.</span><span class="sxs-lookup"><span data-stu-id="02ff4-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="02ff4-108">Tato třída umožňuje manipulaci s her napříč obrazovkou pomocí přetahování myší a pak uvolníte.</span><span class="sxs-lookup"><span data-stu-id="02ff4-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="02ff4-109">Po vydání nečinnost zpracování udržuje her část, protože postupný přechod může zpomalit.</span><span class="sxs-lookup"><span data-stu-id="02ff4-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="02ff4-110">Přesun je lineární a angular.</span><span class="sxs-lookup"><span data-stu-id="02ff4-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="02ff4-111">![Jednoduchý manipulace a nečinnost aplikace. ](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="02ff4-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="02ff4-112">Kromě toho se vytvoří vlastní kolekce, která spravuje her na více místech.</span><span class="sxs-lookup"><span data-stu-id="02ff4-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="02ff4-113">Tato funkce usnadňuje zpracování, které je nutné ze třídy přenos hry XNA.</span><span class="sxs-lookup"><span data-stu-id="02ff4-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="02ff4-114">Vytvoření třídy GamePiece</span><span class="sxs-lookup"><span data-stu-id="02ff4-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="02ff4-115">Vytvoření třídy GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="02ff4-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="02ff4-116">Vytvoření třídy Game1</span><span class="sxs-lookup"><span data-stu-id="02ff4-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="02ff4-117">Výpis úplného kódu</span><span class="sxs-lookup"><span data-stu-id="02ff4-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="02ff4-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="02ff4-118">See Also</span></span>  
 <xref:System.Windows.Input.Manipulations>  
 [<span data-ttu-id="02ff4-119">Přehled manipulace a nečinnosti</span><span class="sxs-lookup"><span data-stu-id="02ff4-119">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
