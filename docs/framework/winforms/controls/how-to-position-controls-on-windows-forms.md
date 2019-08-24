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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1cc2cb4c749b7290a6edf914a8e6a697006ef43c
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987072"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="e3f5a-102">Postupy: Umístit ovládací prvky na model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3f5a-102">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="e3f5a-103">Chcete-li umístit ovládací prvky, použijte Návrhář formulářů v aplikaci Visual Studio <xref:System.Windows.Forms.Control.Location%2A> nebo zadejte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="e3f5a-104">Umístění ovládacího prvku na návrhovou plochu Návrhář formulářů</span><span class="sxs-lookup"><span data-stu-id="e3f5a-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="e3f5a-105">V aplikaci Visual Studio přetáhněte ovládací prvek na příslušné místo pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="e3f5a-106">Vyberte ovládací prvek a přesuňte ho pomocí kláves se šipkami, abyste ho přesně umístili.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="e3f5a-107">*Zarovnávacím čárám* vám také pomůže přesně umístit ovládací prvky do formuláře.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="e3f5a-108">Další informace najdete v tématu [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)zarovnávacím čárám.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="e3f5a-109">Umístění ovládacího prvku pomocí okno Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e3f5a-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="e3f5a-110">V aplikaci Visual Studio vyberte ovládací prvek, který chcete umístit.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-110">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="e3f5a-111">V okně **vlastnosti** zadejte hodnoty <xref:System.Windows.Forms.Control.Location%2A> vlastnosti oddělené čárkou pro umístění ovládacího prvku v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-111">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="e3f5a-112">První číslo (X) je vzdálenost od levého ohraničení kontejneru; druhé číslo (Y) je vzdálenost od horního ohraničení oblasti kontejneru měřená v pixelech.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e3f5a-113">Můžete rozbalit <xref:System.Windows.Forms.Control.Location%2A> vlastnost a zadat hodnoty **X** a **Y** jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="e3f5a-114">Programové umístění ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e3f5a-114">Position a control programmatically</span></span>

1. <span data-ttu-id="e3f5a-115">Nastavte vlastnost ovládacího prvku <xref:System.Drawing.Point>na. <xref:System.Windows.Forms.Control.Location%2A></span><span class="sxs-lookup"><span data-stu-id="e3f5a-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="e3f5a-116">Změňte souřadnici X umístění ovládacího prvku pomocí <xref:System.Windows.Forms.Control.Left%2A> podvlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="e3f5a-117">Zvýšení polohy ovládacího prvku prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="e3f5a-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="e3f5a-118"><xref:System.Windows.Forms.Control.Left%2A> Nastavte podvlastnost na hodnotu, chcete-li zvýšit souřadnici X ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="e3f5a-119"><xref:System.Windows.Forms.Control.Location%2A> Vlastnost použijte k nastavení umístění X a Y ovládacího prvku současně.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="e3f5a-120">Chcete-li nastavit pozici jednotlivě, použijte podvlastnost <xref:System.Windows.Forms.Control.Left%2A> ovládacího prvku (**X**) nebo <xref:System.Windows.Forms.Control.Top%2A> (**Y**).</span><span class="sxs-lookup"><span data-stu-id="e3f5a-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="e3f5a-121">Nepokoušejte se implicitně nastavit souřadnice <xref:System.Drawing.Point> X a Y struktury, které představují umístění tlačítka, protože tato struktura obsahuje kopii souřadnic tlačítka.</span><span class="sxs-lookup"><span data-stu-id="e3f5a-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3f5a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3f5a-122">See also</span></span>

- [<span data-ttu-id="e3f5a-123">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="e3f5a-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="e3f5a-124">Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám</span><span class="sxs-lookup"><span data-stu-id="e3f5a-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="e3f5a-125">Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e3f5a-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="e3f5a-126">Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e3f5a-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="e3f5a-127">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="e3f5a-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="e3f5a-128">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3f5a-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="e3f5a-129">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="e3f5a-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="e3f5a-130">[Postupy: Nastavit umístění obrazovky model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e3f5a-130">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
