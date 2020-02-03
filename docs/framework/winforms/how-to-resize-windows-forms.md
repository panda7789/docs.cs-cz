---
title: Změnit velikost formuláře
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 8d4ce46ada505f952fc3090d10c5d893338d19f2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739300"
---
# <a name="how-to-resize-windows-forms"></a>Postupy: Změna velikosti Windows Forms

Velikost formuláře Windows můžete zadat několika způsoby. Můžete změnit výšku i šířku formuláře programově tak, že nastavíte novou hodnotu vlastnosti <xref:System.Windows.Forms.Form.Size%2A> nebo upravíte vlastnosti <xref:System.Windows.Forms.Control.Height%2A> nebo <xref:System.Windows.Forms.Control.Width%2A> individuálně. Pokud používáte aplikaci Visual Studio, můžete změnit velikost pomocí Návrhář formulářů. Viz také [Postupy: Změna velikosti model Windows Forms pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).

## <a name="resize-a-form-programmatically"></a>Změna velikosti formuláře prostřednictvím kódu programu

Určete velikost formuláře v době běhu nastavením vlastnosti <xref:System.Windows.Forms.Form.Size%2A> formuláře.

Následující příklad kódu ukazuje velikost formuláře nastavenou na 100 × 100 pixelů.

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a>Změna šířky a výšky formuláře prostřednictvím kódu programu

Po definování <xref:System.Windows.Forms.Form.Size%2A> můžete změnit výšku nebo šířku formuláře pomocí vlastností <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A>.

Následující příklad kódu ukazuje šířku formuláře nastavenou na 300 pixelů od levého okraje formuláře, zatímco výška zůstane konstantní.

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

-nebo-

Změňte <xref:System.Drawing.Size.Width%2A> nebo <xref:System.Drawing.Size.Height%2A> nastavením vlastnosti <xref:System.Windows.Forms.Form.Size%2A>.

Jak ukazuje následující příklad kódu, je tento přístup mnohem náročný, než stačí nastavit <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A> vlastnosti.

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a>Změnit velikost formuláře pomocí přírůstků kódu

Chcete-li zvýšit velikost formuláře, nastavte vlastnosti <xref:System.Drawing.Size.Width%2A> a <xref:System.Drawing.Size.Height%2A>.

Následující příklad kódu ukazuje šířku formuláře nastavenou na 200 pixelů širší než aktuální nastavení.

```vb
Form1.Width += 200
```

```csharp
Form1.Width += 200;
```

```cpp
Form1->Width += 200;
```

> [!CAUTION]
> Chcete-li změnit rozměr formuláře, vždy použijte vlastnost <xref:System.Drawing.Size.Height%2A> nebo <xref:System.Drawing.Size.Width%2A>, Pokud nenastavujete současně velikost a šířku dimenzí nastavením vlastnosti <xref:System.Windows.Forms.Form.Size%2A> na novou strukturu <xref:System.Drawing.Size>. Vlastnost <xref:System.Windows.Forms.Form.Size%2A> vrací strukturu <xref:System.Drawing.Size>, což je typ hodnoty. Nelze přiřadit novou hodnotu k vlastnosti typu hodnoty. Následující příklad kódu proto nebude zkompilován.

```vb
' NOTE: CODE WILL NOT COMPILE
Dim f As New Form()
f.Size.Width += 100
```

```csharp
// NOTE: CODE WILL NOT COMPILE
Form f = new Form();
f.Size.Width += 100;
```

```cpp
// NOTE: CODE WILL NOT COMPILE
Form^ f = gcnew Form();
f->Size->X += 100;
```

## <a name="see-also"></a>Viz také

- [Začínáme s Windows Forms](getting-started-with-windows-forms.md)
- [Rozšiřování formulářových aplikací Windows](./advanced/index.md)
