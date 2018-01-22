---
title: "Postupy: Uspořádání ovládacích prvků pomocí zarovnávacích čar a mřížky ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: GridSize
helpviewer_keywords:
- snap to grid [Windows Forms], Windows Forms Designer
- Windows Forms, grid options in designer
- controls [Windows Forms], aligning
ms.assetid: bb54bce5-880f-4a36-af68-8cf92058dc1c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 166ccba959bd9facb8e24d580d47577a0c8746a8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-arrange-controls-with-snaplines-and-the-grid-in-windows-forms"></a><span data-ttu-id="b2d3c-102">Postupy: Uspořádání ovládacích prvků pomocí zarovnávacích čar a mřížky ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2d3c-102">How to: Arrange Controls with Snaplines and the Grid in Windows Forms</span></span>
<span data-ttu-id="b2d3c-103">Pomocí funkce rozložení [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], přesněji můžete nastavit umístění ovládacích prvků na formuláři.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-103">Using the layout features of [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], you can precisely direct where controls are placed on a form.</span></span> <span data-ttu-id="b2d3c-104">Ovládací prvky přidány do formuláře nebo přesunout na formuláři mohou být automaticky zarovnány řádků a sloupců mřížky Návrhář formulářů Windows, nebo můžete zarovnat ovládacích prvků pomocí zarovnávacích čar funkce.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-104">Controls added to a form or moved on a form can be automatically aligned to the rows and columns of the Windows Forms Designer's grid, or you can align controls by using the snaplines feature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2d3c-105">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b2d3c-106">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b2d3c-107">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="b2d3c-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-snap-all-controls-to-the-grid"></a><span data-ttu-id="b2d3c-108">Přichytit všech ovládacích prvků k mřížce.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-108">To snap all controls to the grid</span></span>  
  
-   <span data-ttu-id="b2d3c-109">Vyberte **SnapToGrid** režimu rozložení v Návrháři formulářů **možnosti** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-109">Select the **SnapToGrid** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="b2d3c-110">Další informace najdete v tématu [Návrhář formulářů Windows Obecné, dialogové okno Možnosti](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834).</span><span class="sxs-lookup"><span data-stu-id="b2d3c-110">For more information, see [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834).</span></span> <span data-ttu-id="b2d3c-111">Všechny ovládací prvky vlastní teď vyrovnání podél body v mřížce.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-111">All controls now align themselves along the points on the grid.</span></span>  
  
     <span data-ttu-id="b2d3c-112">Je možné přichytit jednotlivých ovládacích prvků k mřížce blokováním je na místě.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-112">You can snap individual controls to the grid by locking them in place.</span></span> <span data-ttu-id="b2d3c-113">Ale když jsou zamčené, budou se nedá přesunout ani změnit.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-113">However, while they are locked, they cannot be moved or resized.</span></span> <span data-ttu-id="b2d3c-114">Další informace o uzamykání ovládacích prvcích najdete v tématu [postup: Zámek ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b2d3c-114">For more information about locking controls, see [How to: Lock Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span></span>  
  
### <a name="to-align-controls-using-snaplines"></a><span data-ttu-id="b2d3c-115">Chcete-li zarovnat ovládacích prvků pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="b2d3c-115">To align controls using snaplines</span></span>  
  
-   <span data-ttu-id="b2d3c-116">Vyberte **zarovnávacích čar** režimu rozložení v Návrháři formulářů **možnosti** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-116">Select the **SnapLines** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="b2d3c-117">Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="b2d3c-117">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span> <span data-ttu-id="b2d3c-118">Zarovnávací čáry nyní slouží k zarovnání a uspořádání ovládacích prvků formuláře.</span><span class="sxs-lookup"><span data-stu-id="b2d3c-118">You can now use snaplines to align and arrange controls on your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d3c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2d3c-119">See Also</span></span>  
 [<span data-ttu-id="b2d3c-120">Obecné, Návrhář formulářů Windows, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="b2d3c-120">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="b2d3c-121">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="b2d3c-121">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="b2d3c-122">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="b2d3c-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="b2d3c-123">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2d3c-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="b2d3c-124">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2d3c-124">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="b2d3c-125">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="b2d3c-125">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="b2d3c-126">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2d3c-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="b2d3c-127">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="b2d3c-127">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
