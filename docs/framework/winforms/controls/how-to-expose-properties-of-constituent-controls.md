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
ms.openlocfilehash: 8f7b5c44a5cb20b5da10df5fd630b371cc959fa8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532630"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Postupy: Vystavení vlastností základních ovládacích prvků
Ovládací prvky, které tvoří složeného ovládacího prvku se nazývají *základních ovládacích prvků*. Tyto ovládací prvky jsou obvykle deklarovány privátní a proto nelze získat přístup, vývojáři. Pokud chcete zpřístupnit vlastnosti těchto ovládacích prvků pro budoucí uživatele, umístěte je pro uživatele. Vlastnost základní ovládacího prvku je vytvářena při vytvoření vlastnosti v uživatelského ovládacího prvku a pomocí `get` a `set` přístupové objekty této vlastnosti k ovlivnění změnu v hodnotě soukromá vlastnost základní ovládacího prvku.  
  
 Zvažte hypotetický uživatelského ovládacího prvku s základní tlačítko s názvem `MyButton`. V tomto příkladu, když uživatel požádá `ConstituentButtonBackColor` vlastnost, s hodnotou uloženou v <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost `MyButton` doručuje. Když uživatel přiřazuje hodnotu této vlastnosti, je tato hodnota automaticky předaný <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost `MyButton` a `set` kód bude spuštěn, změnit barvu `MyButton`.  
  
 Následující příklad ukazuje, jak vystavit <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost základní tlačítka:  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>Aby se zveřejnily vlastnost základní ovládacího prvku  
  
1.  Vytvoření veřejné vlastnosti pro váš uživatelský ovládací prvek.  
  
2.  V `get` části vlastnost napsat kód, který načte hodnotu vlastnosti, kterou chcete vystavit.  
  
3.  V `set` části vlastnost napsat kód, který předá hodnotu vlastnosti vlastnost zveřejněné základní ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.UserControl>  
 [Vlastnosti v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
