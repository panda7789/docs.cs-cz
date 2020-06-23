---
title: Umístění ovládacích prvků
description: Naučte se používat Návrhář formulářů v aplikaci Visual Studio nebo vlastnost Location k umístění ovládacích prvků.
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
ms.openlocfilehash: 0aa3faade71e0f7e0a9d5e676327a80747524b8c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904296"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="5dcb5-103">Postupy: umístění ovládacích prvků na model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5dcb5-103">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="5dcb5-104">Chcete-li umístit ovládací prvky, použijte Návrhář formulářů v aplikaci Visual Studio nebo zadejte <xref:System.Windows.Forms.Control.Location%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5dcb5-104">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="5dcb5-105">Umístění ovládacího prvku na návrhovou plochu Návrhář formulářů</span><span class="sxs-lookup"><span data-stu-id="5dcb5-105">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="5dcb5-106">V aplikaci Visual Studio přetáhněte ovládací prvek na příslušné místo pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="5dcb5-106">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="5dcb5-107">Vyberte ovládací prvek a přesuňte ho pomocí kláves se šipkami, abyste ho přesně umístili.</span><span class="sxs-lookup"><span data-stu-id="5dcb5-107">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="5dcb5-108">*Zarovnávacím čárám* vám také pomůže přesně umístit ovládací prvky do formuláře.</span><span class="sxs-lookup"><span data-stu-id="5dcb5-108">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="5dcb5-109">Další informace najdete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="5dcb5-109">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="5dcb5-110">Umístění ovládacího prvku pomocí okno Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5dcb5-110">Position a control using the Properties window</span></span>

1. <span data-ttu-id="5dcb5-111">V aplikaci Visual Studio vyberte ovládací prvek, který chcete umístit.</span><span class="sxs-lookup"><span data-stu-id="5dcb5-111">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="5dcb5-112">V okně **vlastnosti** zadejte hodnoty <xref:System.Windows.Forms.Control.Location%2A> vlastnosti oddělené čárkou pro umístění ovládacího prvku v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5dcb5-112">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="5dcb5-113">První číslo (X) je vzdálenost od levého ohraničení kontejneru; druhé číslo (Y) je vzdálenost od horního ohraničení oblasti kontejneru měřená v pixelech.</span><span class="sxs-lookup"><span data-stu-id="5dcb5-113">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="5dcb5-114">Můžete rozbalit vlastnost a <xref:System.Windows.Forms.Control.Location%2A> zadat hodnoty **X** a **Y** jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="5dcb5-114">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="5dcb5-115">Programové umístění ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="5dcb5-115">Position a control programmatically</span></span>

1. <span data-ttu-id="5dcb5-116">Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost ovládacího prvku na <xref:System.Drawing.Point> .</span><span class="sxs-lookup"><span data-stu-id="5dcb5-116">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="5dcb5-117">Změňte souřadnici X umístění ovládacího prvku pomocí <xref:System.Windows.Forms.Control.Left%2A> podvlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5dcb5-117">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="5dcb5-118">Zvýšení polohy ovládacího prvku prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="5dcb5-118">Increment a control's location programmatically</span></span>

<span data-ttu-id="5dcb5-119">Nastavte <xref:System.Windows.Forms.Control.Left%2A> podvlastnost na hodnotu, chcete-li zvýšit souřadnici X ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5dcb5-119">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="5dcb5-120">Vlastnost použijte <xref:System.Windows.Forms.Control.Location%2A> k nastavení umístění X a Y ovládacího prvku současně.</span><span class="sxs-lookup"><span data-stu-id="5dcb5-120">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="5dcb5-121">Chcete-li nastavit pozici jednotlivě, použijte <xref:System.Windows.Forms.Control.Left%2A> podvlastnost ovládacího prvku (**X**) nebo <xref:System.Windows.Forms.Control.Top%2A> (**Y**).</span><span class="sxs-lookup"><span data-stu-id="5dcb5-121">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="5dcb5-122">Nepokoušejte se implicitně nastavit souřadnice X a Y <xref:System.Drawing.Point> struktury, které představují umístění tlačítka, protože tato struktura obsahuje kopii souřadnic tlačítka.</span><span class="sxs-lookup"><span data-stu-id="5dcb5-122">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="5dcb5-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="5dcb5-123">See also</span></span>

- [<span data-ttu-id="5dcb5-124">Ovládací prvky model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5dcb5-124">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="5dcb5-125">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="5dcb5-125">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="5dcb5-126">Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5dcb5-126">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="5dcb5-127">Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5dcb5-127">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="5dcb5-128">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="5dcb5-128">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="5dcb5-129">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5dcb5-129">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="5dcb5-130">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="5dcb5-130">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="5dcb5-131">[Postupy: nastavení umístění obrazovky model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5dcb5-131">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
