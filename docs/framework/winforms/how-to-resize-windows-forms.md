---
title: 'Postupy: Změna velikosti Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 57a75cf07e3487c5a115e57c068b412c33538bce
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664533"
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="5d2c3-102">Postupy: Změna velikosti Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d2c3-102">How to: Resize Windows Forms</span></span>
<span data-ttu-id="5d2c3-103">Velikost formuláře Windows můžete zadat několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-103">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="5d2c3-104">Můžete změnit výšku a šířku formuláře programově tak, že nastavíte novou hodnotu <xref:System.Windows.Forms.Form.Size%2A> vlastnost, nebo upravte <xref:System.Windows.Forms.Control.Height%2A> nebo <xref:System.Windows.Forms.Control.Width%2A> vlastnosti jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-104">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="5d2c3-105">Pokud používáte Visual Studio, můžete změnit velikost pomocí Návrháře formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-105">If you are using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="5d2c3-106">Viz také [jak: Změna velikosti Windows Forms pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5d2c3-106">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>  
  
### <a name="to-resize-a-form-programmatically"></a><span data-ttu-id="5d2c3-107">Změnit velikost formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="5d2c3-107">To resize a form programmatically</span></span>  
  
-   <span data-ttu-id="5d2c3-108">Definovat tak, že nastavíte velikost formuláře v době běhu <xref:System.Windows.Forms.Form.Size%2A> vlastnost formuláře.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-108">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>  
  
     <span data-ttu-id="5d2c3-109">Následující příklad kódu ukazuje velikost formuláře nastavte na 100 × 100 pixelů.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-109">The following code example shows the form size set to 100 × 100 pixels.</span></span>  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### <a name="to-change-form-width-and-height-programmatically"></a><span data-ttu-id="5d2c3-110">Chcete-li změnit výšku a šířku formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="5d2c3-110">To change form width and height programmatically</span></span>  
  
-   <span data-ttu-id="5d2c3-111">Po <xref:System.Windows.Forms.Form.Size%2A> je definován, změnit šířka nebo výška formuláře pomocí <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-111">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>  
  
     <span data-ttu-id="5d2c3-112">Následující příklad kódu ukazuje šířku formuláře nastavte na 300 pixelů od levého okraje formuláře, zatímco výška zůstává konstantní.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-112">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>  
  
    ```vb  
    Form1.Width = 300  
    ```  
  
    ```csharp  
    Form1.Width = 300;  
    ```  
  
    ```cpp  
    Form1->Width = 300;  
    ```  
  
     <span data-ttu-id="5d2c3-113">-nebo-</span><span class="sxs-lookup"><span data-stu-id="5d2c3-113">-or-</span></span>  
  
     <span data-ttu-id="5d2c3-114">Změna <xref:System.Drawing.Size.Width%2A> nebo <xref:System.Drawing.Size.Height%2A> nastavením <xref:System.Windows.Forms.Form.Size%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-114">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>  
  
     <span data-ttu-id="5d2c3-115">Jak ukazuje následující příklad kódu, tento přístup je však náročnější než pouhé nastavení <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-115">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### <a name="to-change-form-size-by-increments-programmatically"></a><span data-ttu-id="5d2c3-116">Chcete-li změnit velikost formuláře o kousek prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="5d2c3-116">To change form size by increments programmatically</span></span>  
  
-   <span data-ttu-id="5d2c3-117">Chcete-li zvýšit velikost formuláře, nastavte <xref:System.Drawing.Size.Width%2A> a <xref:System.Drawing.Size.Height%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-117">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>  
  
     <span data-ttu-id="5d2c3-118">Následující příklad kódu ukazuje šířku formuláře nastavena na hodnotu 200 pixelů širší než aktuální nastavení.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-118">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>  
  
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
    >  <span data-ttu-id="5d2c3-119">Vždy používat <xref:System.Drawing.Size.Height%2A> nebo <xref:System.Drawing.Size.Width%2A> změnit rozměr formuláře, pokud nastavíte výšku a šířku ve stejnou dobu tak, že nastavíte vlastnost <xref:System.Windows.Forms.Form.Size%2A> vlastnost do nového <xref:System.Drawing.Size> struktury.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-119">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="5d2c3-120"><xref:System.Windows.Forms.Form.Size%2A> Vrátí vlastnost <xref:System.Drawing.Size> struktury, což je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-120">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="5d2c3-121">Nelze přiřadit novou hodnotu pro vlastnost typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-121">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="5d2c3-122">Následující příklad kódu proto nebude kompilovat.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-122">Therefore, the following code example will not compile.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d2c3-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d2c3-123">See also</span></span>
- [<span data-ttu-id="5d2c3-124">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d2c3-124">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
- [<span data-ttu-id="5d2c3-125">Rozšiřování aplikací Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d2c3-125">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)
