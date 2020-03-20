---
title: Poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 672104db94826cfbe113a7ae0ea29546b0c3b9da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182003"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows
Pomůcky pro usnadnění přístupu jsou specializované programy a zařízení, které pomáhají postiženým osobám používat počítače efektivněji. Mezi příklady patří programy pro čtení z obrazovky pro nevidomé a hlasové vstupní nástroje pro osoby, které poskytují verbální příkazy namísto používání myši nebo klávesnice. Tyto pomůcky pro usnadnění přístupu interagují s vlastnostmi usnadnění, které jsou vystaveny ovládacím prvkům windows forms. Tyto vlastnosti jsou:  
  
- **Objekt přístupnosti**  
  
- **AccessibleDefaultActionDescription**  
  
- **Přístupný popis**  
  
- **AccessibleName**  
  
- **AccessibleRole**  
  
## <a name="accessibilityobject-property"></a>Vlastnost AccessibilityObject  
 Tato vlastnost jen pro <xref:System.Windows.Forms.AccessibleObject> čtení obsahuje instanci. **AccessibleObject** implementuje <xref:Accessibility.IAccessible> rozhraní, které poskytuje informace o popis ovládacího prvku, umístění obrazovky, navigační schopnosti a hodnotu. Návrhář nastaví tuto hodnotu při přidání ovládacího prvku do formuláře.  
  
## <a name="accessibledefaultactiondescription-property"></a>Vlastnost AccessibleDefaultActionDescription  
 Tento řetězec popisuje akci ovládacího prvku. Nezobrazí se v okně Vlastnosti a může být nastavena pouze v kódu. Následující příklad nastaví tuto vlastnost pro ovládací prvek tlačítka:  
  
```vb  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
```

```csharp  
Button1.AccessibleDefaultActionDescription =
   "Closes the application.";  
```

```cpp  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a>Vlastnost AccessibleDescription  
 Tento řetězec popisuje ovládací prvek. Může být nastavena v okně Vlastnosti nebo v kódu takto:  
  
```vb  
Button1.AccessibleDescription = "A button with text 'Exit'."  
```

```csharp  
Button1.AccessibleDescription = "A button with text 'Exit'";  
```

```cpp  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>Vlastnost AccessibleName  
 Toto je název ovládacího prvku nahlášeného pomůcek usnadnění přístupu. Může být nastavena v okně Vlastnosti nebo v kódu takto:  
  
```vb  
Button1.AccessibleName = "Order"  
```

```csharp  
Button1.AccessibleName = "Order";  
```

```cpp  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a>Vlastnost AccessibleRole  
 Tato vlastnost, která <xref:System.Windows.Forms.AccessibleRole> obsahuje výčet, popisuje roli uživatelského rozhraní ovládacího prvku. Nový ovládací prvek má `Default`hodnotu nastavenou na . To by znamenalo, že ve výchozím nastavení **button** ovládací prvek funguje jako **Button**. Tuto vlastnost můžete obnovit, pokud má ovládací prvek jinou roli. Můžete například používat ovládací prvek **PictureBox** jako **graf**a můžete chtít, aby pomůcky pro usnadnění přístupu hlásily roli jako **graf**, nikoli jako **PictureBox**. Můžete také zadat tuto vlastnost pro vlastní ovládací prvky, které jste vyvinuli. Tato vlastnost může být nastavena v okně Vlastnosti nebo v kódu následujícím způsobem:  
  
```vb
PictureBox1.AccessibleRole = AccessibleRole.Chart  
```

```csharp  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
```

```cpp  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
