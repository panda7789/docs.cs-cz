---
title: "Postupy: Změna velikosti Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc2e9f81094d16030dbe4595a8132569edab782a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="43528-102">Postupy: Změna velikosti Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43528-102">How to: Resize Windows Forms</span></span>
<span data-ttu-id="43528-103">Můžete zadat velikost formuláře Windows několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="43528-103">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="43528-104">Můžete změnit výška a šířka formuláře programově nastavením nové hodnoty pro <xref:System.Windows.Forms.Form.Size%2A> vlastnost, nebo upravit <xref:System.Windows.Forms.Control.Height%2A> nebo <xref:System.Windows.Forms.Control.Width%2A> vlastnosti jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="43528-104">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="43528-105">Pokud používáte [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], můžete změnit velikost pomocí Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="43528-105">If you are using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="43528-106">Viz také [postupy: Změna velikosti Windows Forms pomocí návrháře](http://msdn.microsoft.com/library/37k2zkwx\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="43528-106">Also see [How to: Resize Windows Forms Using the Designer](http://msdn.microsoft.com/library/37k2zkwx\(v=vs.110\)).</span></span>  
  
### <a name="to-resize-a-form-programmatically"></a><span data-ttu-id="43528-107">Chcete-li změnit velikost formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="43528-107">To resize a form programmatically</span></span>  
  
-   <span data-ttu-id="43528-108">Zadejte velikost formuláře v době běhu nastavením <xref:System.Windows.Forms.Form.Size%2A> vlastnost formuláře.</span><span class="sxs-lookup"><span data-stu-id="43528-108">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>  
  
     <span data-ttu-id="43528-109">Následující příklad kódu ukazuje velikost formuláře nastavena na 100 × 100 pixelů.</span><span class="sxs-lookup"><span data-stu-id="43528-109">The following code example shows the form size set to 100 × 100 pixels.</span></span>  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### <a name="to-change-form-width-and-height-programmatically"></a><span data-ttu-id="43528-110">Chcete-li změnit formuláře šířky a výšky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="43528-110">To change form width and height programmatically</span></span>  
  
-   <span data-ttu-id="43528-111">Po <xref:System.Windows.Forms.Form.Size%2A> je definován, změnit šířka nebo výška formuláře pomocí <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="43528-111">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>  
  
     <span data-ttu-id="43528-112">Následující příklad kódu ukazuje šířku formuláře nastavena na 300 pixelů od levého okraje formuláře, zatímco výška zůstává konstantní.</span><span class="sxs-lookup"><span data-stu-id="43528-112">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>  
  
    ```vb  
    Form1.Width = 300  
    ```  
  
    ```csharp  
    Form1.Width = 300;  
    ```  
  
    ```cpp  
    Form1->Width = 300;  
    ```  
  
     <span data-ttu-id="43528-113">-nebo-</span><span class="sxs-lookup"><span data-stu-id="43528-113">-or-</span></span>  
  
     <span data-ttu-id="43528-114">Změna <xref:System.Drawing.Size.Width%2A> nebo <xref:System.Drawing.Size.Height%2A> nastavením <xref:System.Windows.Forms.Form.Size%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="43528-114">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>  
  
     <span data-ttu-id="43528-115">Jak ukazuje následující příklad kódu, tento postup je však těžkopádnější než jenom nastavení <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="43528-115">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### <a name="to-change-form-size-by-increments-programmatically"></a><span data-ttu-id="43528-116">Chcete-li změnit velikost formuláře po přírůstcích prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="43528-116">To change form size by increments programmatically</span></span>  
  
-   <span data-ttu-id="43528-117">Chcete-li zvýšit velikost formuláře, nastavte <xref:System.Drawing.Size.Width%2A> a <xref:System.Drawing.Size.Height%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="43528-117">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>  
  
     <span data-ttu-id="43528-118">Následující příklad kódu ukazuje šířku formuláře nastavena na hodnotu 200 pixelů širší než aktuální nastavení.</span><span class="sxs-lookup"><span data-stu-id="43528-118">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>  
  
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
    >  <span data-ttu-id="43528-119">Vždy nutné použít <xref:System.Drawing.Size.Height%2A> nebo <xref:System.Drawing.Size.Width%2A> vlastnost změnit dimenze formuláře, pokud nastavujete výšku a šířku ve stejnou dobu nastavením <xref:System.Windows.Forms.Form.Size%2A> vlastnost na nový <xref:System.Drawing.Size> struktura.</span><span class="sxs-lookup"><span data-stu-id="43528-119">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="43528-120"><xref:System.Windows.Forms.Form.Size%2A> Vlastnost vrátí <xref:System.Drawing.Size> struktura, což je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="43528-120">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="43528-121">Nelze přiřadit novou hodnotu pro vlastnost typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="43528-121">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="43528-122">Proto nebude Zkompilujte následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="43528-122">Therefore, the following code example will not compile.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43528-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="43528-123">See Also</span></span>  
 [<span data-ttu-id="43528-124">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43528-124">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [<span data-ttu-id="43528-125">Rozšiřování aplikací Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43528-125">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)
