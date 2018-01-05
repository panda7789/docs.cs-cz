---
title: "Použití manipulace a nečinnosti v aplikaci XNA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7452a6001742bc9e0456ccb6339f13596a2ab72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="09105-102">Použití manipulace a nečinnosti v aplikaci XNA</span><span class="sxs-lookup"><span data-stu-id="09105-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="09105-103">Tento článek popisuje, jak můžete použít manipulace a nečinnosti zpracování v aplikaci Microsoft XNA ovládat pohyb herní částí.</span><span class="sxs-lookup"><span data-stu-id="09105-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="09105-104">Předtím, než se pustíte do čtení tohoto článku, měli byste se seznámit s [přehled manipulace a nečinnosti](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) tématu a znát základní XNA koncepce programování.</span><span class="sxs-lookup"><span data-stu-id="09105-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="09105-105">Úkoly popsané v tomto článku projektu XNA musí odkazovat <xref:System.Windows.Input.Manipulations> sestavení a musí mít [XNA herní Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([Stáhnout](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) v počítači nainstalován, který vaše Projekt může odkazovat XNA sestavení.</span><span class="sxs-lookup"><span data-stu-id="09105-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([download](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="09105-106">Přehled funkcí</span><span class="sxs-lookup"><span data-stu-id="09105-106">Overview of Functionality</span></span>  
 <span data-ttu-id="09105-107">Tento článek ukazuje, jak vytvořit vlastní třídu, která představuje herní část, která používá manipulace a nečinnosti zpracování.</span><span class="sxs-lookup"><span data-stu-id="09105-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="09105-108">Tato třída umožňuje manipulaci s herní po obrazovce pomocí přetahování myší a pak ho uvolněním.</span><span class="sxs-lookup"><span data-stu-id="09105-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="09105-109">Po vydání, nečinnosti zpracování udržuje herní část postupný přechod jak zpomalí.</span><span class="sxs-lookup"><span data-stu-id="09105-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="09105-110">Pohyb je lineární a úhlová.</span><span class="sxs-lookup"><span data-stu-id="09105-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="09105-111">![Jednoduchý manipulace a nečinnosti aplikace. ] (../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="09105-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="09105-112">Kromě toho je vytvořen vlastní kolekce, který spravuje herní na více místech.</span><span class="sxs-lookup"><span data-stu-id="09105-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="09105-113">Tato funkce zjednodušuje zpracování požadované ze třídy XNA hra.</span><span class="sxs-lookup"><span data-stu-id="09105-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="09105-114">Vytvoření třídy GamePiece</span><span class="sxs-lookup"><span data-stu-id="09105-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="09105-115">Vytvoření třídy GamePieceCollection</span><span class="sxs-lookup"><span data-stu-id="09105-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="09105-116">Vytvoření třídy Game1</span><span class="sxs-lookup"><span data-stu-id="09105-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="09105-117">Výpis úplného kódu</span><span class="sxs-lookup"><span data-stu-id="09105-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="09105-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="09105-118">See Also</span></span>  
 <xref:System.Windows.Input.Manipulations>  
 [<span data-ttu-id="09105-119">Přehled manipulace a nečinnosti</span><span class="sxs-lookup"><span data-stu-id="09105-119">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
