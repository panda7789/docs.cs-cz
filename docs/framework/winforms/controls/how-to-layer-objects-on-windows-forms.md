---
title: 'Postupy: Vrstvení objektů ve formulářích Windows'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5b8f6c00e70df94ae3a82c2c195fa781f0840a53
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458352"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Postupy: vrstvení objektů na model Windows Forms

Když vytváříte složité uživatelské rozhraní nebo pracujete s formulářem MDI (Multiple Document Interface), často budete chtít navrstvit ovládací prvky i podřízené formuláře pro vytváření složitějších uživatelských rozhraní (UI). Chcete-li přesunout a sledovat ovládací prvky a okna v kontextu skupiny, budete pracovat s jejich *pořadím z*. Pořadí vykreslování je vizuální vrstvení ovládacích prvků na formuláři podél osy z (hloubka) formuláře. Okno v horní části pořadí vykreslování překrývá všechna ostatní okna. Všechna ostatní okna překrývají okno v dolní části pořadí vykreslování.

## <a name="to-layer-controls-at-design-time"></a>Do vrstev ovládacích prvků v době návrhu

1. V aplikaci Visual Studio vyberte ovládací prvek, který chcete vytvořit do vrstvy.

2. V nabídce **Formát** vyberte možnost **pořadí**a potom vyberte možnost **přenést do popředí** nebo **přenést do pozadí**.

## <a name="to-layer-controls-programmatically"></a>Pro ovládací prvky vrstev programově

Použijte metody <xref:System.Windows.Forms.Control.BringToFront%2A> a <xref:System.Windows.Forms.Control.SendToBack%2A> k manipulaci s pořadím z ovládacích prvků.

Například pokud <xref:System.Windows.Forms.TextBox> ovládací prvek `txtFirstName`, je pod jiným ovládacím prvkem a chcete jej použít jako horní, použijte následující kód:

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
> Model Windows Forms podporuje *omezení ovládacího prvku*. Ovládací prvek zahrnutí zahrnuje umístění řady ovládacích prvků v rámci obsahujícího ovládacího prvku, jako je například počet ovládacích prvků <xref:System.Windows.Forms.RadioButton> v rámci <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Ovládací prvky lze následně rozvrstvit v rámci nadřazeného ovládacího prvku. Přesunutím skupinového pole se přesunou i ovládací prvky, protože jsou uvnitř ní obsažené.

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
