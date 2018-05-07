---
title: Poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: ffeecc1dfe52f1703fc201ef196644afbcc4708c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows
Usnadnění jsou specializované programy a zařízení, které pomáhají osoby s postižením efektivněji využívat počítače. Mezi příklady patří čtečky obrazovky pro uživatele, kteří jsou blind a hlasové vstupní nástrojů pro uživatele, kteří poskytují ústní příkazy místo pomocí myši a klávesnice. Tyto usnadnění komunikovat s vlastnostmi usnadnění vystavené ovládací prvky Windows Forms. Tyto vlastnosti jsou:  
  
-   **AccessibilityObject**  
  
-   **AccessibleDefaultActionDescription**  
  
-   **AccessibleDescription**  
  
-   **AccessibleName**  
  
-   **AccessibleRole**  
  
## <a name="accessibilityobject-property"></a>Vlastnost AccessibilityObject  
 Tato vlastnost jen pro čtení obsahuje <xref:System.Windows.Forms.AccessibleObject> instance. **Třída AccessibleObject** implementuje <xref:Accessibility.IAccessible> rozhraní, která poskytuje informace o popis ovládacího prvku, umístění na obrazovce, navigační dalo a hodnoty. Návrháře nastavuje tuto hodnotu, když je ovládací prvek přidán do formuláře.  
  
## <a name="accessibledefaultactiondescription-property"></a>Vlastnost AccessibleDefaultActionDescription  
 Tento řetězec popisuje akci ovládacího prvku. Se nezobrazí v okně vlastností a lze nastavit pouze v kódu. Tato vlastnost pro ovládací prvek tlačítko nastaví v následujícím příkladu:  
  
```  
' Visual Basic  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
  
// C#  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
  
// C++  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a>Vlastnost AccessibleDescription  
 Tento řetězec popisuje ovládacího prvku. Může být nastaveno v okně Vlastnosti, nebo v kódu následujícím způsobem:  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>Vlastnost AccessibleName  
 Toto je název ovládacího prvku oznamovány usnadnění. Může být nastaveno v okně Vlastnosti, nebo v kódu následujícím způsobem:  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a>Vlastnost AccessibleRole  
 Tato vlastnost, která obsahuje <xref:System.Windows.Forms.AccessibleRole> výčtu, popisuje roli uživatele rozhraní ovládacího prvku. Nový ovládací prvek je nastavena hodnota `Default`. To by znamenají, že ve výchozím nastavení, **tlačítko** řízení funguje jako **tlačítko**. Chcete resetovat tuto vlastnost, pokud se ovládací prvek obsahuje jiné role. Například je možné, že používáte **PictureBox** řízení jako **grafu**, a může být vhodné usnadnění nahlásit roli jako **grafu**, ne jako **PictureBox** . Můžete také zadat tato vlastnost pro vlastní ovládací prvky, kterou jste vytvořili. Tuto vlastnost lze nastavit v okně Vlastnosti, nebo v kódu následujícím způsobem:  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.AccessibleObject>  
 <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.AccessibleRole>
