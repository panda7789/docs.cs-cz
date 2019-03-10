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
ms.openlocfilehash: 75ee93b7a601b4fc1480dca708d78740664c9a85
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704514"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Postupy: Vystavení vlastností základních ovládacích prvků
Ovládací prvky, které tvoří složeného ovládacího prvku se nazývají *základní ovládací prvky*. Tyto ovládací prvky jsou obvykle deklarována jako soukromá a proto není přístupná vývojářem. Pokud chcete zpřístupnit vlastnosti těchto ovládacích prvků pro budoucí uživatele, musí zveřejnit uživatele. Vlastnost základní ovládacího prvku je zveřejněný prostřednictvím vytváření vlastnost do uživatelského ovládacího prvku a používání `get` a `set` přistupující objekty vlastnosti provést změnu v hodnotě privátní vlastnost základní ovládacího prvku.  
  
 Vezměte v úvahu hypotetické uživatelský ovládací prvek s základní tlačítko s názvem `MyButton`. V tomto příkladu, když uživatel požádá `ConstituentButtonBackColor` vlastnost, hodnotou uloženou v části <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost `MyButton` doručuje. Pokud uživatel přiřadí hodnotu této vlastnosti, je automaticky předat tuto hodnotu <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost `MyButton` a `set` bude kód spuštěn, změnou barvy `MyButton`.  
  
 Následující příklad ukazuje, jak vystavit <xref:System.Windows.Forms.Control.BackColor%2A> základní vlastnosti:  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>Vystavení vlastností základních ovládacího prvku  
  
1.  Vytvoření veřejné vlastnosti uživatelského ovládacího prvku.  
  
2.  V `get` část vlastnosti, psaní kódu, který načte hodnotu vlastnosti, kterou chcete zveřejnit.  
  
3.  V `set` část vlastnosti, psaní kódu, který se předá hodnotu vlastnosti na vlastnost vystavené základní ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.UserControl>
- [Vlastnosti v ovládacích prvcích Windows Forms](properties-in-windows-forms-controls.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
