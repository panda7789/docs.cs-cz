---
title: 'Postupy: Uspořádání ovládacích prvků pomocí zarovnávacích čar a mřížky ve Windows Forms'
ms.date: 03/30/2017
f1_keywords:
- GridSize
helpviewer_keywords:
- snap to grid [Windows Forms], Windows Forms Designer
- Windows Forms, grid options in designer
- controls [Windows Forms], aligning
ms.assetid: bb54bce5-880f-4a36-af68-8cf92058dc1c
ms.openlocfilehash: bbe6ae2adfe364e41f6627e6b067aa8e18e6e079
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517274"
---
# <a name="how-to-arrange-controls-with-snaplines-and-the-grid-in-windows-forms"></a><span data-ttu-id="c571b-102">Postupy: Uspořádání ovládacích prvků pomocí zarovnávacích čar a mřížky ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c571b-102">How to: Arrange Controls with Snaplines and the Grid in Windows Forms</span></span>
<span data-ttu-id="c571b-103">Použití funkcí rozložení sady Visual Studio, můžete přesně nastavit umístění ovládacích prvků ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="c571b-103">Using the layout features of Visual Studio, you can precisely direct where controls are placed on a form.</span></span> <span data-ttu-id="c571b-104">Ovládací prvky do formuláře přidán nebo přesunout na formuláři mohou být automaticky zarovnány řádků a sloupců mřížky v Návrháři formulářů Windows, nebo je možné zarovnat ovládacích prvků pomocí zarovnávacích čar funkce.</span><span class="sxs-lookup"><span data-stu-id="c571b-104">Controls added to a form or moved on a form can be automatically aligned to the rows and columns of the Windows Forms Designer's grid, or you can align controls by using the snaplines feature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c571b-105">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="c571b-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c571b-106">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c571b-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c571b-107">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c571b-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-snap-all-controls-to-the-grid"></a><span data-ttu-id="c571b-108">Přichytit k mřížce všechny ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="c571b-108">To snap all controls to the grid</span></span>  
  
-   <span data-ttu-id="c571b-109">Vyberte **SnapToGrid** režim rozložení v Návrháři formulářů Windows **možnosti** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c571b-109">Select the **SnapToGrid** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="c571b-110">Další informace najdete v tématu [Obecné, Návrhář formulářů Windows, dialogové okno Možnosti](https://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834).</span><span class="sxs-lookup"><span data-stu-id="c571b-110">For more information, see [General, Windows Forms Designer, Options Dialog Box](https://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834).</span></span> <span data-ttu-id="c571b-111">Všechny ovládací prvky se nyní připojily podél body v mřížce.</span><span class="sxs-lookup"><span data-stu-id="c571b-111">All controls now align themselves along the points on the grid.</span></span>  
  
     <span data-ttu-id="c571b-112">Je-li přichytit jednotlivých ovládacích prvků do mřížky, uzamčení na místě.</span><span class="sxs-lookup"><span data-stu-id="c571b-112">You can snap individual controls to the grid by locking them in place.</span></span> <span data-ttu-id="c571b-113">Ale když jsou zamčené, že se nedá přesunout ani se změněnou velikostí.</span><span class="sxs-lookup"><span data-stu-id="c571b-113">However, while they are locked, they cannot be moved or resized.</span></span> <span data-ttu-id="c571b-114">Další informace o uzamčení ovládacích prvků naleznete v tématu [jak: uzamknout ovládací prvky Windows Forms](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c571b-114">For more information about locking controls, see [How to: Lock Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span></span>  
  
### <a name="to-align-controls-using-snaplines"></a><span data-ttu-id="c571b-115">Zarovnání ovládacích prvků pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="c571b-115">To align controls using snaplines</span></span>  
  
-   <span data-ttu-id="c571b-116">Vyberte **zarovnávacích čar** režim rozložení v Návrháři formulářů Windows **možnosti** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c571b-116">Select the **SnapLines** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="c571b-117">Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="c571b-117">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span> <span data-ttu-id="c571b-118">Nyní můžete zarovnávacích čar na zarovnání a uspořádání ovládacích prvků na formuláři.</span><span class="sxs-lookup"><span data-stu-id="c571b-118">You can now use snaplines to align and arrange controls on your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c571b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c571b-119">See Also</span></span>  
 [<span data-ttu-id="c571b-120">Obecné, Návrhář formulářů Windows, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="c571b-120">General, Windows Forms Designer, Options Dialog Box</span></span>](https://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="c571b-121">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="c571b-121">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="c571b-122">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="c571b-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="c571b-123">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c571b-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="c571b-124">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c571b-124">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="c571b-125">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="c571b-125">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="c571b-126">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c571b-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="c571b-127">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="c571b-127">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
