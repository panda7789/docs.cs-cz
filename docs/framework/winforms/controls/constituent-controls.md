---
title: Základní ovládací prvky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 76a5a4f9b02a71616d247a1bb0f03cc0aec1d70d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224869"
---
# <a name="constituent-controls"></a><span data-ttu-id="f3ece-102">Základní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="f3ece-102">Constituent Controls</span></span>
<span data-ttu-id="f3ece-103">Ovládací prvky, které tvoří uživatelský ovládací prvek nebo *základní ovládací prvky* jsou označovány jako, jsou relativně nepřizpůsobitelným při rozhodování o vykreslování grafiky vlastní.</span><span class="sxs-lookup"><span data-stu-id="f3ece-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="f3ece-104">Všechny ovládací prvky Windows Forms zpracovávat své vlastní vykreslování prostřednictvím vlastní <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f3ece-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="f3ece-105">Vzhledem k tomu, že tato metoda je chráněný, není přístupná pro vývojáře a proto ji nelze zabránit spuštění při vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f3ece-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="f3ece-106">To neznamená, ale, že nemůžete přidat kód pro vliv na vzhled základních ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="f3ece-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="f3ece-107">Další vykreslování dosáhnete tak, že přidáte obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="f3ece-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="f3ece-108">Předpokládejme například, že byly pro vytváření <xref:System.Windows.Forms.UserControl> s tlačítkem `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="f3ece-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="f3ece-109">Pokud jste si přáli mít další vykreslování nad rámec je zadán <xref:System.Web.UI.WebControls.Button>, by přidejte kód do vašeho uživatelského ovládacího prvku podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="f3ece-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
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
>  <span data-ttu-id="f3ece-110">Ovládací prvky některé formulářů Windows, jako například <xref:System.Windows.Forms.TextBox>, jsou přímo kresleno Windows.</span><span class="sxs-lookup"><span data-stu-id="f3ece-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="f3ece-111">V těchto případech <xref:System.Windows.Forms.Control.OnPaint%2A> se nikdy nevolá metodu, a proto výše uvedeném příkladu již nikdy nebudou voláni.</span><span class="sxs-lookup"><span data-stu-id="f3ece-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="f3ece-112">Tím se vytvoří metodu, která se spustí pokaždé, když `MyButton.Paint` spustí událost, a tím přidáte další grafické vyjádření do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f3ece-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="f3ece-113">Všimněte si, že tím byste nezabránili provádění `MyButton.OnPaint`, a proto všechny Malování obvykle provádí tlačítko bude stále provádět kromě vlastního vykreslování.</span><span class="sxs-lookup"><span data-stu-id="f3ece-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="f3ece-114">Podrobnosti o rozhraní GDI + technologie a vlastního vykreslování, najdete v článku [grafické vytváření obrázků pomocí GDI +](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="f3ece-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="f3ece-115">Pokud budete chtít mít jedinečné reprezentace vašeho ovládacího prvku, je vaší nejlíp zděděný ovládací prvek a napsat kód pro vlastní vykreslování pro něj.</span><span class="sxs-lookup"><span data-stu-id="f3ece-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="f3ece-116">Podrobnosti najdete v tématu [ovládací prvky User-Drawn](user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f3ece-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ece-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3ece-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="f3ece-118">Ovládací prvky vykreslované uživatelem</span><span class="sxs-lookup"><span data-stu-id="f3ece-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="f3ece-119">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="f3ece-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="f3ece-120">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f3ece-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
