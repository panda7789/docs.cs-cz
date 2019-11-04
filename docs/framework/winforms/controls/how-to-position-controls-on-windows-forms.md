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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bb57d14397a4626e01c41dd687dfed7331282a10
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458326"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="482a4-102">Postupy: umístění ovládacích prvků na model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="482a4-102">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="482a4-103">Chcete-li umístit ovládací prvky, použijte Návrhář formulářů v aplikaci Visual Studio nebo zadejte vlastnost <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="482a4-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="482a4-104">Umístění ovládacího prvku na návrhovou plochu Návrhář formulářů</span><span class="sxs-lookup"><span data-stu-id="482a4-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="482a4-105">V aplikaci Visual Studio přetáhněte ovládací prvek na příslušné místo pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="482a4-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="482a4-106">Vyberte ovládací prvek a přesuňte ho pomocí kláves se šipkami, abyste ho přesně umístili.</span><span class="sxs-lookup"><span data-stu-id="482a4-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="482a4-107">*Zarovnávacím čárám* vám také pomůže přesně umístit ovládací prvky do formuláře.</span><span class="sxs-lookup"><span data-stu-id="482a4-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="482a4-108">Další informace najdete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="482a4-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="482a4-109">Umístění ovládacího prvku pomocí okno Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="482a4-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="482a4-110">V aplikaci Visual Studio vyberte ovládací prvek, který chcete umístit.</span><span class="sxs-lookup"><span data-stu-id="482a4-110">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="482a4-111">V okně **vlastnosti** zadejte hodnoty vlastnosti <xref:System.Windows.Forms.Control.Location%2A> oddělené čárkou pro umístění ovládacího prvku v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="482a4-111">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="482a4-112">První číslo (X) je vzdálenost od levého ohraničení kontejneru; druhé číslo (Y) je vzdálenost od horního ohraničení oblasti kontejneru měřená v pixelech.</span><span class="sxs-lookup"><span data-stu-id="482a4-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="482a4-113">Můžete rozbalit vlastnost <xref:System.Windows.Forms.Control.Location%2A> a zadat hodnoty **X** a **Y** jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="482a4-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="482a4-114">Programové umístění ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="482a4-114">Position a control programmatically</span></span>

1. <span data-ttu-id="482a4-115">Nastavte vlastnost <xref:System.Windows.Forms.Control.Location%2A> ovládacího prvku na <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="482a4-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="482a4-116">Změňte souřadnici X umístění ovládacího prvku pomocí podvlastnosti <xref:System.Windows.Forms.Control.Left%2A>.</span><span class="sxs-lookup"><span data-stu-id="482a4-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="482a4-117">Zvýšení polohy ovládacího prvku prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="482a4-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="482a4-118">Nastavte podvlastnost <xref:System.Windows.Forms.Control.Left%2A> pro zvýšení souřadnic X ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="482a4-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="482a4-119">Vlastnost <xref:System.Windows.Forms.Control.Location%2A> použijte k nastavení polohy X a Y ovládacího prvku současně.</span><span class="sxs-lookup"><span data-stu-id="482a4-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="482a4-120">Chcete-li nastavit pozici jednotlivě, použijte podvlastnost <xref:System.Windows.Forms.Control.Left%2A> (**X**) nebo <xref:System.Windows.Forms.Control.Top%2A> (**Y**) ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="482a4-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="482a4-121">Nepokoušejte se implicitně nastavit souřadnice X a Y <xref:System.Drawing.Point> struktury, která představuje umístění tlačítka, protože tato struktura obsahuje kopii souřadnic tlačítka.</span><span class="sxs-lookup"><span data-stu-id="482a4-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="482a4-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="482a4-122">See also</span></span>

- [<span data-ttu-id="482a4-123">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="482a4-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="482a4-124">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="482a4-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="482a4-125">Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="482a4-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="482a4-126">Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="482a4-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="482a4-127">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="482a4-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="482a4-128">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="482a4-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="482a4-129">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="482a4-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="482a4-130">[Postupy: nastavení umístění obrazovky model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="482a4-130">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
