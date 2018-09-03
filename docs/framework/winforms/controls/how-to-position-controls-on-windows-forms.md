---
title: 'Postupy: Umisťování ovládacích prvků ve formulářích Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
ms.openlocfilehash: 6843c22fec964de92c41760f1108d1c83e1f5bf8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43476076"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="bf7f3-102">Postupy: Umisťování ovládacích prvků ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="bf7f3-102">How to: Position Controls on Windows Forms</span></span>
<span data-ttu-id="bf7f3-103">Umístit ovládací prvky, použijte Návrhář formulářů Windows nebo zadat <xref:System.Windows.Forms.Control.Location%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-103">To position controls, use the Windows Forms Designer, or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf7f3-104">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="bf7f3-105">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="bf7f3-106">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="bf7f3-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="bf7f3-107">Pokud chcete umístit ovládací prvek na návrhové ploše Návrháře formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="bf7f3-107">To position a control on the design surface of the Windows Forms Designer</span></span>  
  
-   <span data-ttu-id="bf7f3-108">Přetáhněte ovládací prvek pomocí myši do příslušného umístění.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-108">Drag the control to the appropriate location with the mouse.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf7f3-109">Vyberte ovládací prvek a přesunout že ho s šipkou klíče na pozici přesněji.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-109">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="bf7f3-110">Navíc *zarovnávacích čar* vám pomohou při uvádění ovládací prvky měly ve správnou chvíli na formuláři.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-110">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="bf7f3-111">Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="bf7f3-111">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
### <a name="to-position-a-control-using-the-properties-window"></a><span data-ttu-id="bf7f3-112">Na pozici ovládacího prvku pomocí okna Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bf7f3-112">To position a control using the Properties window</span></span>  
  
1.  <span data-ttu-id="bf7f3-113">Klikněte na ovládací prvek, který chcete umístit.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-113">Click the control you want to position.</span></span>  
  
2.  <span data-ttu-id="bf7f3-114">V **vlastnosti** okno, zadejte hodnoty <xref:System.Windows.Forms.Control.Location%2A> vlastnost oddělené čárkou, pokud chcete umístit ovládací prvek v rámci jeho kontejneru.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-114">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>  
  
     <span data-ttu-id="bf7f3-115">První číslo (X) je vzdálenost od levého ohraničení kontejneru; druhé číslo (Y) je vzdálenost mezi horním okrajem oblasti kontejnerů, měřeno v pixelech.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-115">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf7f3-116">Můžete rozšířit <xref:System.Windows.Forms.Control.Location%2A> vlastnosti na typ **X** a **Y** hodnoty jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-116">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>  
  
### <a name="to-position-a-control-programmatically"></a><span data-ttu-id="bf7f3-117">Pokud chcete umístit ovládací prvek prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="bf7f3-117">To position a control programmatically</span></span>  
  
1.  <span data-ttu-id="bf7f3-118">Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost ovládacího prvku <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-118">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  <span data-ttu-id="bf7f3-119">Změnit souřadnici X polohy ovládacího prvku pomocí <xref:System.Windows.Forms.Control.Left%2A> podvlastností.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-119">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a><span data-ttu-id="bf7f3-120">Umístění ovládacího prvku postupně prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="bf7f3-120">To increment a control's location programmatically</span></span>  
  
1.  <span data-ttu-id="bf7f3-121">Nastavte <xref:System.Windows.Forms.Control.Left%2A> podvlastností postupně souřadnici X ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-121">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="bf7f3-122">Použití <xref:System.Windows.Forms.Control.Location%2A> vlastnosti chcete nastavit ovládací prvek X a Y pozice současně.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-122">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="bf7f3-123">Chcete-li nastavení pozice jednotlivě, použijte ovládací prvek <xref:System.Windows.Forms.Control.Left%2A> (**X**) nebo <xref:System.Windows.Forms.Control.Top%2A> (**Y**) podvlastností.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-123">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="bf7f3-124">Nepokoušejte se implicitně nastavena souřadnice X a Y <xref:System.Drawing.Point> strukturu, která představuje tlačítka umístění, protože tato struktura obsahuje kopii souřadnice na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bf7f3-124">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf7f3-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf7f3-125">See Also</span></span>  
 [<span data-ttu-id="bf7f3-126">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="bf7f3-126">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="bf7f3-127">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="bf7f3-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="bf7f3-128">Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bf7f3-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="bf7f3-129">Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bf7f3-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="bf7f3-130">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf7f3-130">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="bf7f3-131">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="bf7f3-131">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="bf7f3-132">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf7f3-132">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="bf7f3-133">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="bf7f3-133">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="bf7f3-134">Postupy: nastavit polohu na obrazovce formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="bf7f3-134">How to: Set the Screen Location of Windows Forms</span></span>](https://msdn.microsoft.com/library/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
