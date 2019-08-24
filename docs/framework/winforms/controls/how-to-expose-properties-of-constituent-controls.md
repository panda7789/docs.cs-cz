---
title: 'Postupy: Vystavení vlastností základních ovládacích prvků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: f006e42771a5ecc71f6a508fd78d0e2dd8f2d2f2
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015881"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Postupy: Vystavení vlastností základních ovládacích prvků
Ovládací prvky, které tvoří složený ovládací prvek, se nazývají *ovládací prvky prvků*. Tyto ovládací prvky jsou obvykle deklarovány jako soukromé, a proto nejsou k dispozici vývojáři. Pokud chcete, aby byly vlastnosti těchto ovládacích prvků dostupné budoucím uživatelům, musíte je vystavit uživateli. Vlastnost ovládacího prvku prvku je vystavena vytvořením vlastnosti v uživatelském ovládacím prvku a použitím `get` přístupových objektů a `set` dané vlastnosti pro změnu vlastnosti Private ovládacího prvku prvek.

 Zvažte hypotetický uživatelský ovládací prvek s tlačítkem na prvku `MyButton`s názvem. V tomto příkladu, když uživatel požádá `ConstituentButtonBackColor` o vlastnost, hodnota uložená <xref:System.Windows.Forms.Control.BackColor%2A> ve vlastnosti `MyButton` je dodána. Když uživatel přiřadí k této vlastnosti hodnotu, tato hodnota se <xref:System.Windows.Forms.Control.BackColor%2A> automaticky předává `MyButton` vlastnosti a `set` `MyButton`kód se spustí, změna barvy.

 Následující příklad ukazuje, jak vystavit <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost tlačítka prvku:

```vb
Public Property ButtonColor() as System.Drawing.Color
   Get
      Return MyButton.BackColor
   End Get
   Set(Value as System.Drawing.Color)
      MyButton.BackColor = Value
   End Set
End Property
```

```csharp
public Color ButtonColor
{
   get
   {
      return(myButton.BackColor);
   }
   set
   {
      myButton.BackColor = value;
   }
}
```

### <a name="to-expose-a-property-of-a-constituent-control"></a>Vystavení vlastnosti ovládacího prvku prvků

1. Vytvořte veřejnou vlastnost pro uživatelský ovládací prvek.

2. `get` V části vlastnosti napište kód, který načte hodnotu vlastnosti, kterou chcete zveřejnit.

3. `set` V části vlastnosti napište kód, který předá hodnotu vlastnosti Vlastnosti vystavené vlastnosti ovládacího prvku prvek.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.UserControl>
- [Vlastnosti v ovládacích prvcích Windows Forms](properties-in-windows-forms-controls.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
