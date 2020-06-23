---
title: Změnit velikost formuláře
description: Zjistěte, jak změnit výšku a šířku formuláře nastavením nové hodnoty vlastnosti Size, nebo můžete vlastnosti výšky nebo šířky upravit jednotlivě.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 0d6383e4d29d9407d3da97bf8b94761f06d99748
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903269"
---
# <a name="how-to-resize-windows-forms"></a>Postupy: Změna velikosti Windows Forms

Velikost formuláře Windows můžete zadat několika způsoby. Můžete změnit výšku i šířku formuláře programově tak, že nastavíte novou hodnotu <xref:System.Windows.Forms.Form.Size%2A> vlastnosti nebo upravíte <xref:System.Windows.Forms.Control.Height%2A> <xref:System.Windows.Forms.Control.Width%2A> vlastnosti nebo jednotlivě. Pokud používáte aplikaci Visual Studio, můžete změnit velikost pomocí Návrhář formulářů. Viz také [Postupy: Změna velikosti model Windows Forms pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).

## <a name="resize-a-form-programmatically"></a>Změna velikosti formuláře prostřednictvím kódu programu

Určete velikost formuláře v době běhu nastavením <xref:System.Windows.Forms.Form.Size%2A> vlastnosti formuláře.

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

Po <xref:System.Windows.Forms.Form.Size%2A> Definování je buď Změňte výšku nebo šířku formuláře, pomocí <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.Control.Height%2A> vlastností nebo.

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

Změnit <xref:System.Drawing.Size.Width%2A> nebo <xref:System.Drawing.Size.Height%2A> nastavením <xref:System.Windows.Forms.Form.Size%2A> Vlastnosti.

Jak ukazuje následující příklad kódu, je tento přístup náročný než pouze nastavení <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A> Vlastnosti.

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

Chcete-li zvýšit velikost formuláře, nastavte <xref:System.Drawing.Size.Width%2A> <xref:System.Drawing.Size.Height%2A> vlastnosti a.

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
> Vždy použijte <xref:System.Drawing.Size.Height%2A> vlastnost nebo <xref:System.Drawing.Size.Width%2A> pro změnu rozměru formuláře, Pokud nenastavujete současně rozměry výšky i šířky, nastavením <xref:System.Windows.Forms.Form.Size%2A> vlastnosti na novou <xref:System.Drawing.Size> strukturu. <xref:System.Windows.Forms.Form.Size%2A>Vlastnost vrací <xref:System.Drawing.Size> strukturu, což je hodnotový typ. Nelze přiřadit novou hodnotu k vlastnosti typu hodnoty. Následující příklad kódu proto nebude zkompilován.

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
