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
ms.openlocfilehash: 791944bd9e8f5520a571e6fb415d69022aa0bead
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991716"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows
Pomůcky pro usnadnění přístupu jsou specializované programy a zařízení, které lidem s postižením můžou efektivněji používat počítače. Mezi příklady patří čtečky obrazovky pro lidi, kteří jsou nevidomí a nástroje pro zadávání hlasu pro lidi, kteří poskytují ústní příkazy namísto použití myši nebo klávesnice. Tato pomůcka pro usnadnění práce spolupracuje s vlastnostmi přístupnosti vystavenými ovládacími prvky model Windows Forms. Tyto vlastnosti jsou:  
  
- **AccessibilityObject**  
  
- **AccessibleDefaultActionDescription**  
  
- **AccessibleDescription**  
  
- **Přístupný**  
  
- **AccessibleRole**  
  
## <a name="accessibilityobject-property"></a>Vlastnost AccessibilityObject  
 Tato vlastnost jen pro čtení obsahuje <xref:System.Windows.Forms.AccessibleObject> instanci. **Třída AccessibleObject** implementuje <xref:Accessibility.IAccessible> rozhraní, které poskytuje informace o popisu ovládacího prvku, umístění obrazovky, navigačních schopnostech a hodnotě. Návrhář tuto hodnotu nastaví při přidání ovládacího prvku do formuláře.  
  
## <a name="accessibledefaultactiondescription-property"></a>Vlastnost AccessibleDefaultActionDescription  
 Tento řetězec popisuje akci ovládacího prvku. Nezobrazuje se v okno Vlastnosti a lze ji nastavit pouze v kódu. Následující příklad nastaví tuto vlastnost pro ovládací prvek tlačítko:  
  
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
 Tento řetězec popisuje ovládací prvek. Může být nastavena v okno Vlastnosti nebo v kódu následujícím způsobem:  
  
```vb  
Button1.AccessibleDescription = "A button with text 'Exit'."  
```

```csharp  
Button1.AccessibleDescription = "A button with text 'Exit'";  
```

```cpp  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>Vlastnost s usnadněním  
 Toto je název ovládacího prvku nahlášený pro pomůcky přístupnosti. Může být nastavena v okno Vlastnosti nebo v kódu následujícím způsobem:  
  
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
 Tato vlastnost, která obsahuje <xref:System.Windows.Forms.AccessibleRole> výčet, popisuje roli uživatelského rozhraní ovládacího prvku. Nový ovládací prvek má hodnotu nastavenou na `Default`. To by znamenalo, že ve výchozím nastavení se ovládací prvek **tlačítko** chová jako **tlačítko**. Tuto vlastnost můžete chtít resetovat, pokud má ovládací prvek jinou roli. Například můžete použít ovládací prvek **PictureBox** jako **graf**a můžete chtít, aby pomůcky usnadnění nahlásily roli jako **graf**, nikoli jako **PictureBox**. Tuto vlastnost můžete také použít pro vlastní ovládací prvky, které jste vyvinuli. Tato vlastnost může být nastavena v okno Vlastnosti nebo v kódu následujícím způsobem:  
  
```vb 
PictureBox1.AccessibleRole = AccessibleRole.Chart  
```

```csharp  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
```

```cpp  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
