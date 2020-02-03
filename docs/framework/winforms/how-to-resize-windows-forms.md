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
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="b9968-102">Postupy: Změna velikosti Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9968-102">How to: Resize Windows Forms</span></span>

<span data-ttu-id="b9968-103">Velikost formuláře Windows můžete zadat několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="b9968-103">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="b9968-104">Můžete změnit výšku i šířku formuláře programově tak, že nastavíte novou hodnotu vlastnosti <xref:System.Windows.Forms.Form.Size%2A> nebo upravíte vlastnosti <xref:System.Windows.Forms.Control.Height%2A> nebo <xref:System.Windows.Forms.Control.Width%2A> individuálně.</span><span class="sxs-lookup"><span data-stu-id="b9968-104">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="b9968-105">Pokud používáte aplikaci Visual Studio, můžete změnit velikost pomocí Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="b9968-105">If you're using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="b9968-106">Viz také [Postupy: Změna velikosti model Windows Forms pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b9968-106">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>

## <a name="resize-a-form-programmatically"></a><span data-ttu-id="b9968-107">Změna velikosti formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="b9968-107">Resize a form programmatically</span></span>

<span data-ttu-id="b9968-108">Určete velikost formuláře v době běhu nastavením vlastnosti <xref:System.Windows.Forms.Form.Size%2A> formuláře.</span><span class="sxs-lookup"><span data-stu-id="b9968-108">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>

<span data-ttu-id="b9968-109">Následující příklad kódu ukazuje velikost formuláře nastavenou na 100 × 100 pixelů.</span><span class="sxs-lookup"><span data-stu-id="b9968-109">The following code example shows the form size set to 100 × 100 pixels.</span></span>

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a><span data-ttu-id="b9968-110">Změna šířky a výšky formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="b9968-110">Change form width and height programmatically</span></span>

<span data-ttu-id="b9968-111">Po definování <xref:System.Windows.Forms.Form.Size%2A> můžete změnit výšku nebo šířku formuláře pomocí vlastností <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="b9968-111">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

<span data-ttu-id="b9968-112">Následující příklad kódu ukazuje šířku formuláře nastavenou na 300 pixelů od levého okraje formuláře, zatímco výška zůstane konstantní.</span><span class="sxs-lookup"><span data-stu-id="b9968-112">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

<span data-ttu-id="b9968-113">-nebo-</span><span class="sxs-lookup"><span data-stu-id="b9968-113">-or-</span></span>

<span data-ttu-id="b9968-114">Změňte <xref:System.Drawing.Size.Width%2A> nebo <xref:System.Drawing.Size.Height%2A> nastavením vlastnosti <xref:System.Windows.Forms.Form.Size%2A>.</span><span class="sxs-lookup"><span data-stu-id="b9968-114">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>

<span data-ttu-id="b9968-115">Jak ukazuje následující příklad kódu, je tento přístup mnohem náročný, než stačí nastavit <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b9968-115">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a><span data-ttu-id="b9968-116">Změnit velikost formuláře pomocí přírůstků kódu</span><span class="sxs-lookup"><span data-stu-id="b9968-116">Change form size by increments programmatically</span></span>

<span data-ttu-id="b9968-117">Chcete-li zvýšit velikost formuláře, nastavte vlastnosti <xref:System.Drawing.Size.Width%2A> a <xref:System.Drawing.Size.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="b9968-117">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>

<span data-ttu-id="b9968-118">Následující příklad kódu ukazuje šířku formuláře nastavenou na 200 pixelů širší než aktuální nastavení.</span><span class="sxs-lookup"><span data-stu-id="b9968-118">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>

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
> <span data-ttu-id="b9968-119">Chcete-li změnit rozměr formuláře, vždy použijte vlastnost <xref:System.Drawing.Size.Height%2A> nebo <xref:System.Drawing.Size.Width%2A>, Pokud nenastavujete současně velikost a šířku dimenzí nastavením vlastnosti <xref:System.Windows.Forms.Form.Size%2A> na novou strukturu <xref:System.Drawing.Size>.</span><span class="sxs-lookup"><span data-stu-id="b9968-119">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="b9968-120">Vlastnost <xref:System.Windows.Forms.Form.Size%2A> vrací strukturu <xref:System.Drawing.Size>, což je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b9968-120">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="b9968-121">Nelze přiřadit novou hodnotu k vlastnosti typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b9968-121">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="b9968-122">Následující příklad kódu proto nebude zkompilován.</span><span class="sxs-lookup"><span data-stu-id="b9968-122">Therefore, the following code example will not compile.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b9968-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9968-123">See also</span></span>

- [<span data-ttu-id="b9968-124">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9968-124">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="b9968-125">Rozšiřování formulářových aplikací Windows</span><span class="sxs-lookup"><span data-stu-id="b9968-125">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
