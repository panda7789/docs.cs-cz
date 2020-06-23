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
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="95a1b-103">Postupy: Změna velikosti Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95a1b-103">How to: Resize Windows Forms</span></span>

<span data-ttu-id="95a1b-104">Velikost formuláře Windows můžete zadat několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="95a1b-104">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="95a1b-105">Můžete změnit výšku i šířku formuláře programově tak, že nastavíte novou hodnotu <xref:System.Windows.Forms.Form.Size%2A> vlastnosti nebo upravíte <xref:System.Windows.Forms.Control.Height%2A> <xref:System.Windows.Forms.Control.Width%2A> vlastnosti nebo jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="95a1b-105">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="95a1b-106">Pokud používáte aplikaci Visual Studio, můžete změnit velikost pomocí Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="95a1b-106">If you're using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="95a1b-107">Viz také [Postupy: Změna velikosti model Windows Forms pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="95a1b-107">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>

## <a name="resize-a-form-programmatically"></a><span data-ttu-id="95a1b-108">Změna velikosti formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="95a1b-108">Resize a form programmatically</span></span>

<span data-ttu-id="95a1b-109">Určete velikost formuláře v době běhu nastavením <xref:System.Windows.Forms.Form.Size%2A> vlastnosti formuláře.</span><span class="sxs-lookup"><span data-stu-id="95a1b-109">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>

<span data-ttu-id="95a1b-110">Následující příklad kódu ukazuje velikost formuláře nastavenou na 100 × 100 pixelů.</span><span class="sxs-lookup"><span data-stu-id="95a1b-110">The following code example shows the form size set to 100 × 100 pixels.</span></span>

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a><span data-ttu-id="95a1b-111">Změna šířky a výšky formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="95a1b-111">Change form width and height programmatically</span></span>

<span data-ttu-id="95a1b-112">Po <xref:System.Windows.Forms.Form.Size%2A> Definování je buď Změňte výšku nebo šířku formuláře, pomocí <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.Control.Height%2A> vlastností nebo.</span><span class="sxs-lookup"><span data-stu-id="95a1b-112">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

<span data-ttu-id="95a1b-113">Následující příklad kódu ukazuje šířku formuláře nastavenou na 300 pixelů od levého okraje formuláře, zatímco výška zůstane konstantní.</span><span class="sxs-lookup"><span data-stu-id="95a1b-113">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

<span data-ttu-id="95a1b-114">-nebo-</span><span class="sxs-lookup"><span data-stu-id="95a1b-114">-or-</span></span>

<span data-ttu-id="95a1b-115">Změnit <xref:System.Drawing.Size.Width%2A> nebo <xref:System.Drawing.Size.Height%2A> nastavením <xref:System.Windows.Forms.Form.Size%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95a1b-115">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>

<span data-ttu-id="95a1b-116">Jak ukazuje následující příklad kódu, je tento přístup náročný než pouze nastavení <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95a1b-116">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a><span data-ttu-id="95a1b-117">Změnit velikost formuláře pomocí přírůstků kódu</span><span class="sxs-lookup"><span data-stu-id="95a1b-117">Change form size by increments programmatically</span></span>

<span data-ttu-id="95a1b-118">Chcete-li zvýšit velikost formuláře, nastavte <xref:System.Drawing.Size.Width%2A> <xref:System.Drawing.Size.Height%2A> vlastnosti a.</span><span class="sxs-lookup"><span data-stu-id="95a1b-118">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>

<span data-ttu-id="95a1b-119">Následující příklad kódu ukazuje šířku formuláře nastavenou na 200 pixelů širší než aktuální nastavení.</span><span class="sxs-lookup"><span data-stu-id="95a1b-119">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>

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
> <span data-ttu-id="95a1b-120">Vždy použijte <xref:System.Drawing.Size.Height%2A> vlastnost nebo <xref:System.Drawing.Size.Width%2A> pro změnu rozměru formuláře, Pokud nenastavujete současně rozměry výšky i šířky, nastavením <xref:System.Windows.Forms.Form.Size%2A> vlastnosti na novou <xref:System.Drawing.Size> strukturu.</span><span class="sxs-lookup"><span data-stu-id="95a1b-120">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="95a1b-121"><xref:System.Windows.Forms.Form.Size%2A>Vlastnost vrací <xref:System.Drawing.Size> strukturu, což je hodnotový typ.</span><span class="sxs-lookup"><span data-stu-id="95a1b-121">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="95a1b-122">Nelze přiřadit novou hodnotu k vlastnosti typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="95a1b-122">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="95a1b-123">Následující příklad kódu proto nebude zkompilován.</span><span class="sxs-lookup"><span data-stu-id="95a1b-123">Therefore, the following code example will not compile.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="95a1b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="95a1b-124">See also</span></span>

- [<span data-ttu-id="95a1b-125">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95a1b-125">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="95a1b-126">Rozšiřování formulářových aplikací Windows</span><span class="sxs-lookup"><span data-stu-id="95a1b-126">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
