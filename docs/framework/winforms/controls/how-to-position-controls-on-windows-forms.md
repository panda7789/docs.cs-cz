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
# <a name="how-to-position-controls-on-windows-forms"></a>Postupy: Umístit ovládací prvky na model Windows Forms

Chcete-li umístit ovládací prvky, použijte Návrhář formulářů v aplikaci Visual Studio <xref:System.Windows.Forms.Control.Location%2A> nebo zadejte vlastnost.

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Umístění ovládacího prvku na návrhovou plochu Návrhář formulářů

V aplikaci Visual Studio přetáhněte ovládací prvek na příslušné místo pomocí myši.

> [!NOTE]
> Vyberte ovládací prvek a přesuňte ho pomocí kláves se šipkami, abyste ho přesně umístili. *Zarovnávacím čárám* vám také pomůže přesně umístit ovládací prvky do formuláře. Další informace najdete v tématu [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)zarovnávacím čárám.

## <a name="position-a-control-using-the-properties-window"></a>Umístění ovládacího prvku pomocí okno Vlastnosti

1. V aplikaci Visual Studio vyberte ovládací prvek, který chcete umístit.

2. V okně **vlastnosti** zadejte hodnoty <xref:System.Windows.Forms.Control.Location%2A> vlastnosti oddělené čárkou pro umístění ovládacího prvku v kontejneru.

   První číslo (X) je vzdálenost od levého ohraničení kontejneru; druhé číslo (Y) je vzdálenost od horního ohraničení oblasti kontejneru měřená v pixelech.

   > [!NOTE]
   > Můžete rozbalit <xref:System.Windows.Forms.Control.Location%2A> vlastnost a zadat hodnoty **X** a **Y** jednotlivě.

## <a name="position-a-control-programmatically"></a>Programové umístění ovládacího prvku

1. Nastavte vlastnost ovládacího prvku <xref:System.Drawing.Point>na. <xref:System.Windows.Forms.Control.Location%2A>

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

<xref:System.Windows.Forms.Control.Left%2A> Nastavte podvlastnost na hodnotu, chcete-li zvýšit souřadnici X ovládacího prvku.

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
> <xref:System.Windows.Forms.Control.Location%2A> Vlastnost použijte k nastavení umístění X a Y ovládacího prvku současně. Chcete-li nastavit pozici jednotlivě, použijte podvlastnost <xref:System.Windows.Forms.Control.Left%2A> ovládacího prvku (**X**) nebo <xref:System.Windows.Forms.Control.Top%2A> (**Y**). Nepokoušejte se implicitně nastavit souřadnice <xref:System.Drawing.Point> X a Y struktury, které představují umístění tlačítka, protože tato struktura obsahuje kopii souřadnic tlačítka.

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
- [Postupy: Nastavit umístění obrazovky model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
