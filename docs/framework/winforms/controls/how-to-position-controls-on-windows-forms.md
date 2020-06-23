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
# <a name="how-to-position-controls-on-windows-forms"></a>Postupy: umístění ovládacích prvků na model Windows Forms

Chcete-li umístit ovládací prvky, použijte Návrhář formulářů v aplikaci Visual Studio nebo zadejte <xref:System.Windows.Forms.Control.Location%2A> vlastnost.

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Umístění ovládacího prvku na návrhovou plochu Návrhář formulářů

V aplikaci Visual Studio přetáhněte ovládací prvek na příslušné místo pomocí myši.

> [!NOTE]
> Vyberte ovládací prvek a přesuňte ho pomocí kláves se šipkami, abyste ho přesně umístili. *Zarovnávacím čárám* vám také pomůže přesně umístit ovládací prvky do formuláře. Další informace najdete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

## <a name="position-a-control-using-the-properties-window"></a>Umístění ovládacího prvku pomocí okno Vlastnosti

1. V aplikaci Visual Studio vyberte ovládací prvek, který chcete umístit.

2. V okně **vlastnosti** zadejte hodnoty <xref:System.Windows.Forms.Control.Location%2A> vlastnosti oddělené čárkou pro umístění ovládacího prvku v kontejneru.

   První číslo (X) je vzdálenost od levého ohraničení kontejneru; druhé číslo (Y) je vzdálenost od horního ohraničení oblasti kontejneru měřená v pixelech.

   > [!NOTE]
   > Můžete rozbalit vlastnost a <xref:System.Windows.Forms.Control.Location%2A> zadat hodnoty **X** a **Y** jednotlivě.

## <a name="position-a-control-programmatically"></a>Programové umístění ovládacího prvku

1. Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost ovládacího prvku na <xref:System.Drawing.Point> .

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. Změňte souřadnici X umístění ovládacího prvku pomocí <xref:System.Windows.Forms.Control.Left%2A> podvlastnosti.

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a>Zvýšení polohy ovládacího prvku prostřednictvím kódu programu

Nastavte <xref:System.Windows.Forms.Control.Left%2A> podvlastnost na hodnotu, chcete-li zvýšit souřadnici X ovládacího prvku.

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
> Vlastnost použijte <xref:System.Windows.Forms.Control.Location%2A> k nastavení umístění X a Y ovládacího prvku současně. Chcete-li nastavit pozici jednotlivě, použijte <xref:System.Windows.Forms.Control.Left%2A> podvlastnost ovládacího prvku (**X**) nebo <xref:System.Windows.Forms.Control.Top%2A> (**Y**). Nepokoušejte se implicitně nastavit souřadnice X a Y <xref:System.Drawing.Point> struktury, které představují umístění tlačítka, protože tato struktura obsahuje kopii souřadnic tlačítka.

## <a name="see-also"></a>Viz také

- [Ovládací prvky model Windows Forms](index.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
- [Postupy: nastavení umístění obrazovky model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
