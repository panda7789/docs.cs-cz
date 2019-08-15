---
title: 'Postupy: Vrstvení objektů ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 80973e16445079876e01c89f20b5ecbdca602eb8
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039728"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Postupy: Vrstvení objektů ve Windows Forms
Když vytváříte složité uživatelské rozhraní nebo pracujete s formulářem MDI (Multiple Document Interface), často budete chtít navrstvit ovládací prvky i podřízené formuláře pro vytváření složitějších uživatelských rozhraní (UI). Chcete-li přesunout a sledovat ovládací prvky a okna v kontextu skupiny, budete pracovat s jejich pořadím z. *Pořadí vykreslování* je vizuální vrstvení ovládacích prvků na formuláři podél osy z (hloubka) formuláře. Okno v horní části pořadí vykreslování překrývá všechna ostatní okna. Všechna ostatní okna překrývají okno v dolní části pořadí vykreslování.

## <a name="to-layer-controls-at-design-time"></a>Do vrstev ovládacích prvků v době návrhu

1. Vyberte ovládací prvek, který chcete vytvořit do vrstvy.

2. V nabídce **Formát** ukažte na **Seřadit**a potom klikněte na **přenést do popředí** nebo **přenést do pozadí**.

## <a name="to-layer-controls-programmatically"></a>Pro ovládací prvky vrstev programově

- Použijte metody <xref:System.Windows.Forms.Control.SendToBack%2A> a k manipulaci s pořadím z ovládacích prvků. <xref:System.Windows.Forms.Control.BringToFront%2A>

     Například pokud <xref:System.Windows.Forms.TextBox> ovládací prvek, `txtFirstName`, je pod jiným ovládacím prvkem a chcete jej použít nahoře, použijte následující kód:

    ```vb
    txtFirstName.BringToFront()
    ```

    ```csharp
    txtFirstName.BringToFront();
    ```

    ```cpp
    txtFirstName->BringToFront();
    ```

> [!NOTE]
>  Model Windows Forms podporuje *omezení ovládacího prvku*. Zahrnutí ovládacího prvku zahrnuje vložení řady ovládacích prvků v rámci obsahujícího ovládacího prvku, jako je například počet <xref:System.Windows.Forms.RadioButton> ovládacích prvků <xref:System.Windows.Forms.GroupBox> v rámci ovládacího prvku. Ovládací prvky lze následně rozvrstvit v rámci nadřazeného ovládacího prvku. Přesunutím skupinového pole se přesunou i ovládací prvky, protože jsou uvnitř ní obsažené.

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
