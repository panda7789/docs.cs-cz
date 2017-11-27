---
title: "Postupy: Umisťování ovládacích prvků ve formulářích Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ff1096e6397f4422e0fbf6400a87041cfac6470
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="df960-102">Postupy: Umisťování ovládacích prvků ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="df960-102">How to: Position Controls on Windows Forms</span></span>
<span data-ttu-id="df960-103">Umisťování ovládacích prvků, Návrhář formulářů Windows, nebo zadejte <xref:System.Windows.Forms.Control.Location%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="df960-103">To position controls, use the Windows Forms Designer, or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df960-104">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="df960-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="df960-105">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="df960-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="df960-106">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="df960-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="df960-107">Na pozici ovládacího prvku na plochu návrháře Návrhář formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="df960-107">To position a control on the design surface of the Windows Forms Designer</span></span>  
  
-   <span data-ttu-id="df960-108">Přetáhněte ovládací prvek na požadované místo pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="df960-108">Drag the control to the appropriate location with the mouse.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df960-109">Vyberte ovládací prvek a přesunout že ho s šipku klíče na místo, přesněji.</span><span class="sxs-lookup"><span data-stu-id="df960-109">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="df960-110">Navíc *zarovnávacích čar* vám pomůže v umístění ovládacích prvků přesněji do formuláře.</span><span class="sxs-lookup"><span data-stu-id="df960-110">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="df960-111">Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="df960-111">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
### <a name="to-position-a-control-using-the-properties-window"></a><span data-ttu-id="df960-112">Na pozici ovládacího prvku pomocí vlastnosti okna</span><span class="sxs-lookup"><span data-stu-id="df960-112">To position a control using the Properties window</span></span>  
  
1.  <span data-ttu-id="df960-113">Klikněte na ovládací prvek, který chcete umístit.</span><span class="sxs-lookup"><span data-stu-id="df960-113">Click the control you want to position.</span></span>  
  
2.  <span data-ttu-id="df960-114">V **vlastnosti** okno, zadejte hodnoty <xref:System.Windows.Forms.Control.Location%2A> vlastnost, oddělených čárkou, na pozici v rámci příslušného kontejneru ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="df960-114">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>  
  
     <span data-ttu-id="df960-115">První číslo (X) je vzdálenost od levého ohraničení kontejneru; druhé číslo (Y) je vzdálenost od horního ohraničení oblasti kontejneru měřená v pixelech.</span><span class="sxs-lookup"><span data-stu-id="df960-115">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df960-116">Můžete rozbalit <xref:System.Windows.Forms.Control.Location%2A> vlastnosti na typ **X** a **Y** hodnoty jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="df960-116">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>  
  
### <a name="to-position-a-control-programmatically"></a><span data-ttu-id="df960-117">Na pozici ovládacího prvku prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="df960-117">To position a control programmatically</span></span>  
  
1.  <span data-ttu-id="df960-118">Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnosti do ovládacího prvku <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="df960-118">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  <span data-ttu-id="df960-119">Změnit souřadnici X umístění ovládacího prvku pomocí <xref:System.Windows.Forms.Control.Left%2A> dílčí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="df960-119">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a><span data-ttu-id="df960-120">Se zvýší umístění ovládacího prvku prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="df960-120">To increment a control's location programmatically</span></span>  
  
1.  <span data-ttu-id="df960-121">Nastavte <xref:System.Windows.Forms.Control.Left%2A> dílčí vlastnosti se zvýší souřadnici X ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="df960-121">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>  
  
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
    >  <span data-ttu-id="df960-122">Použití <xref:System.Windows.Forms.Control.Location%2A> vlastnost nastavující X a Y ovládacího prvku umisťuje současně.</span><span class="sxs-lookup"><span data-stu-id="df960-122">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="df960-123">Chcete-li nastavit pozici jednotlivě, použijte ovládací prvek <xref:System.Windows.Forms.Control.Left%2A> (**X**) nebo <xref:System.Windows.Forms.Control.Top%2A> (**Y**) dílčí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="df960-123">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="df960-124">Nepokoušejte se implicitně nastavit souřadnice X a Y <xref:System.Drawing.Point> struktura, která představuje tlačítka umístění, protože tato struktura obsahuje kopii na tlačítko souřadnice.</span><span class="sxs-lookup"><span data-stu-id="df960-124">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df960-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="df960-125">See Also</span></span>  
 [<span data-ttu-id="df960-126">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="df960-126">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="df960-127">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="df960-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="df960-128">Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="df960-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="df960-129">Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="df960-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="df960-130">Uspořádání ovládacích prvků ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="df960-130">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="df960-131">Popisování jednotlivých Windows Forms – ovládací prvky a zajišťování zástupců pro tyto</span><span class="sxs-lookup"><span data-stu-id="df960-131">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="df960-132">Ovládací prvky používané ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="df960-132">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="df960-133">Windows Forms – ovládací prvky podle funkce</span><span class="sxs-lookup"><span data-stu-id="df960-133">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="df960-134">Postupy: nastavení umístění obrazovce Windows Forms</span><span class="sxs-lookup"><span data-stu-id="df960-134">How to: Set the Screen Location of Windows Forms</span></span>](http://msdn.microsoft.com/en-us/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
