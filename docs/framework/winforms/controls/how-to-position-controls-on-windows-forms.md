---
title: 'Postupy: Umístění ovládacích prvků ve Windows Forms'
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
ms.openlocfilehash: 241edbe60c327493c9123c6cf7bdc19b7ba2b724
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211651"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="148d9-102">Postupy: Umístění ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="148d9-102">How to: Position Controls on Windows Forms</span></span>

<span data-ttu-id="148d9-103">Umístit ovládací prvky, použijte Návrhář formulářů Windows v sadě Visual Studio nebo zadat <xref:System.Windows.Forms.Control.Location%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="148d9-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="148d9-104">Pozice ovládacího prvku na návrhové ploše Návrháře formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="148d9-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="148d9-105">V sadě Visual Studio přetáhněte ovládací prvek pomocí myši do příslušného umístění.</span><span class="sxs-lookup"><span data-stu-id="148d9-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="148d9-106">Vyberte ovládací prvek a přesunout že ho s šipkou klíče na pozici přesněji.</span><span class="sxs-lookup"><span data-stu-id="148d9-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="148d9-107">Navíc *zarovnávacích čar* vám pomohou při uvádění ovládací prvky měly ve správnou chvíli na formuláři.</span><span class="sxs-lookup"><span data-stu-id="148d9-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="148d9-108">Další informace najdete v tématu [názorný postup: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="148d9-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="148d9-109">Pozice ovládacího prvku pomocí okna Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="148d9-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="148d9-110">V sadě Visual Studio klikněte na ovládací prvek, který chcete umístit.</span><span class="sxs-lookup"><span data-stu-id="148d9-110">In Visual Studio, click the control you want to position.</span></span>

2. <span data-ttu-id="148d9-111">V **vlastnosti** okno, zadejte hodnoty <xref:System.Windows.Forms.Control.Location%2A> vlastnost oddělené čárkou, pokud chcete umístit ovládací prvek v rámci jeho kontejneru.</span><span class="sxs-lookup"><span data-stu-id="148d9-111">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

     <span data-ttu-id="148d9-112">První číslo (X) je vzdálenost od levého ohraničení kontejneru; druhé číslo (Y) je vzdálenost mezi horním okrajem oblasti kontejnerů, měřeno v pixelech.</span><span class="sxs-lookup"><span data-stu-id="148d9-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

    > [!NOTE]
    > <span data-ttu-id="148d9-113">Můžete rozšířit <xref:System.Windows.Forms.Control.Location%2A> vlastnosti na typ **X** a **Y** hodnoty jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="148d9-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="148d9-114">Umístit ovládací prvek prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="148d9-114">Position a control programmatically</span></span>

1. <span data-ttu-id="148d9-115">Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost ovládacího prvku <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="148d9-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="148d9-116">Změnit souřadnici X polohy ovládacího prvku pomocí <xref:System.Windows.Forms.Control.Left%2A> podvlastností.</span><span class="sxs-lookup"><span data-stu-id="148d9-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="148d9-117">Umístění ovládacího prvku zvýšit prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="148d9-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="148d9-118">Nastavte <xref:System.Windows.Forms.Control.Left%2A> podvlastností postupně souřadnici X ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="148d9-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="148d9-119">Použití <xref:System.Windows.Forms.Control.Location%2A> vlastnosti chcete nastavit ovládací prvek X a Y pozice současně.</span><span class="sxs-lookup"><span data-stu-id="148d9-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="148d9-120">Chcete-li nastavení pozice jednotlivě, použijte ovládací prvek <xref:System.Windows.Forms.Control.Left%2A> (**X**) nebo <xref:System.Windows.Forms.Control.Top%2A> (**Y**) podvlastností.</span><span class="sxs-lookup"><span data-stu-id="148d9-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="148d9-121">Nepokoušejte se implicitně nastavena souřadnice X a Y <xref:System.Drawing.Point> strukturu, která představuje tlačítka umístění, protože tato struktura obsahuje kopii souřadnice na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="148d9-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="148d9-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="148d9-122">See also</span></span>

- [<span data-ttu-id="148d9-123">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="148d9-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="148d9-124">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="148d9-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="148d9-125">Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="148d9-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="148d9-126">Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="148d9-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="148d9-127">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="148d9-127">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="148d9-128">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="148d9-128">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="148d9-129">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="148d9-129">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="148d9-130">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="148d9-130">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="148d9-131">[Postupy: Nastavit polohu na obrazovce formulářů Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="148d9-131">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
