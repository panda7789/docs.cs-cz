---
title: "Základní ovládací prvky"
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
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d03b69c334148313b0cd495fad1b2dfd13df833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="constituent-controls"></a><span data-ttu-id="1b787-102">Základní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="1b787-102">Constituent Controls</span></span>
<span data-ttu-id="1b787-103">Ovládací prvky, které tvoří uživatelský ovládací prvek, nebo *základních ovládacích prvků* jako jsou označovány jako, jsou relativně pevná, pokud jde o vlastní grafiky vykreslování.</span><span class="sxs-lookup"><span data-stu-id="1b787-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="1b787-104">Všechny ovládací prvky Windows Forms zpracovávat své vlastní vykreslování prostřednictvím svých vlastních <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1b787-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="1b787-105">Protože tato metoda je chráněn, není přístupná pro vývojáře a proto není možné zabránit spuštění při vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1b787-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="1b787-106">To neznamená, ale, že není možné přidat kód do mají vliv na vzhled základních ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="1b787-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="1b787-107">Další vykreslování dosáhnete přidáním obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1b787-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="1b787-108">Předpokládejme například, že byly vytváření obsahu <xref:System.Windows.Forms.UserControl> s tlačítko s názvem `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="1b787-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="1b787-109">Pokud jste si přáli mít další vykreslování rámec toho, co byl poskytnut <xref:System.Web.UI.WebControls.Button>, byste přidali kód pro váš uživatelský ovládací prvek podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="1b787-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=   
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,   
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="1b787-110">Některé Windows Forms – ovládací prvky, jako například <xref:System.Windows.Forms.TextBox>, jsou vykresluje přímo v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1b787-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="1b787-111">V těchto případech <xref:System.Windows.Forms.Control.OnPaint%2A> nikdy metoda je volána, a proto nebude výše uvedeném příkladu nikdy volat.</span><span class="sxs-lookup"><span data-stu-id="1b787-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="1b787-112">Tím se vytvoří metodu, která se spustí pokaždé, když `MyButton.Paint` událost spuštěna, a tím přidání další grafické vyjádření do vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1b787-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="1b787-113">Všimněte si, že to nezabrání spuštění `MyButton.OnPaint`, a proto všechny Malování obvykle provádí tlačítko bude stále provést kromě vaše vlastní Malování.</span><span class="sxs-lookup"><span data-stu-id="1b787-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="1b787-114">Podrobnosti o GDI + technologie a vlastní vykreslení najdete v tématu [vytváření grafického obrázků pomocí GDI +](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="1b787-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="1b787-115">Pokud chcete mít jedinečné reprezentace vlastního ovládacího prvku, je váš nejlepší postup k vytvoření ovládacího prvku zděděné a napsat vlastní vykreslení kód pro něj.</span><span class="sxs-lookup"><span data-stu-id="1b787-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="1b787-116">Podrobnosti najdete v tématu [ovládací prvky User-Drawn](../../../../docs/framework/winforms/controls/user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1b787-116">For details, see [User-Drawn Controls](../../../../docs/framework/winforms/controls/user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b787-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b787-117">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="1b787-118">Ovládací prvky vykreslované uživatelem</span><span class="sxs-lookup"><span data-stu-id="1b787-118">User-Drawn Controls</span></span>](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 [<span data-ttu-id="1b787-119">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="1b787-119">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="1b787-120">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="1b787-120">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
