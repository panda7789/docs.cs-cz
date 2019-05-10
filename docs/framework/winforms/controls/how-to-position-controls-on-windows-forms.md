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
# <a name="how-to-position-controls-on-windows-forms"></a>Postupy: Umístění ovládacích prvků ve Windows Forms

Umístit ovládací prvky, použijte Návrhář formulářů Windows v sadě Visual Studio nebo zadat <xref:System.Windows.Forms.Control.Location%2A> vlastnost.

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Pozice ovládacího prvku na návrhové ploše Návrháře formulářů Windows

V sadě Visual Studio přetáhněte ovládací prvek pomocí myši do příslušného umístění.

> [!NOTE]
> Vyberte ovládací prvek a přesunout že ho s šipkou klíče na pozici přesněji. Navíc *zarovnávacích čar* vám pomohou při uvádění ovládací prvky měly ve správnou chvíli na formuláři. Další informace najdete v tématu [názorný postup: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

## <a name="position-a-control-using-the-properties-window"></a>Pozice ovládacího prvku pomocí okna Vlastnosti

1. V sadě Visual Studio klikněte na ovládací prvek, který chcete umístit.

2. V **vlastnosti** okno, zadejte hodnoty <xref:System.Windows.Forms.Control.Location%2A> vlastnost oddělené čárkou, pokud chcete umístit ovládací prvek v rámci jeho kontejneru.

     První číslo (X) je vzdálenost od levého ohraničení kontejneru; druhé číslo (Y) je vzdálenost mezi horním okrajem oblasti kontejnerů, měřeno v pixelech.

    > [!NOTE]
    > Můžete rozšířit <xref:System.Windows.Forms.Control.Location%2A> vlastnosti na typ **X** a **Y** hodnoty jednotlivě.

## <a name="position-a-control-programmatically"></a>Umístit ovládací prvek prostřednictvím kódu programu

1. Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost ovládacího prvku <xref:System.Drawing.Point>.

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. Změnit souřadnici X polohy ovládacího prvku pomocí <xref:System.Windows.Forms.Control.Left%2A> podvlastností.

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a>Umístění ovládacího prvku zvýšit prostřednictvím kódu programu

Nastavte <xref:System.Windows.Forms.Control.Left%2A> podvlastností postupně souřadnici X ovládacího prvku.

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
> Použití <xref:System.Windows.Forms.Control.Location%2A> vlastnosti chcete nastavit ovládací prvek X a Y pozice současně. Chcete-li nastavení pozice jednotlivě, použijte ovládací prvek <xref:System.Windows.Forms.Control.Left%2A> (**X**) nebo <xref:System.Windows.Forms.Control.Top%2A> (**Y**) podvlastností. Nepokoušejte se implicitně nastavena souřadnice X a Y <xref:System.Drawing.Point> strukturu, která představuje tlačítka umístění, protože tato struktura obsahuje kopii souřadnice na tlačítko.

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
- [Postupy: Nastavit polohu na obrazovce formulářů Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
