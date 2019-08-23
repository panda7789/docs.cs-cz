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
ms.openlocfilehash: 522a1012fc7bdd54860b0538064ee073f7a761f7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918430"
---
# <a name="constituent-controls"></a><span data-ttu-id="53d88-102">Základní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="53d88-102">Constituent Controls</span></span>
<span data-ttu-id="53d88-103">Ovládací prvky, které tvoří uživatelský ovládací prvek nebo *ovládací prvky prvku* , když jsou vyvolány, jsou relativně neflexibilní, pokud jsou k dispozici pro vlastní vykreslování grafiky.</span><span class="sxs-lookup"><span data-stu-id="53d88-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="53d88-104">Všechny model Windows Forms ovládací prvky zpracovávají své vlastní vykreslení prostřednictvím své <xref:System.Windows.Forms.Control.OnPaint%2A> vlastní metody.</span><span class="sxs-lookup"><span data-stu-id="53d88-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="53d88-105">Vzhledem k tomu, že je tato metoda chráněná, není vývojářům přístupná, takže se nedá zabránit ve spuštění, když je ovládací prvek vykreslený.</span><span class="sxs-lookup"><span data-stu-id="53d88-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="53d88-106">To však neznamená, že nemůžete přidat kód, který by ovlivnil vzhled prvků prvku.</span><span class="sxs-lookup"><span data-stu-id="53d88-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="53d88-107">Další vykreslování lze provést přidáním obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="53d88-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="53d88-108">Předpokládejme například, že jste provedli <xref:System.Windows.Forms.UserControl> vytváření pomocí tlačítka s `MyButton`názvem.</span><span class="sxs-lookup"><span data-stu-id="53d88-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="53d88-109">Pokud chcete mít další vykreslování nad rámec toho <xref:System.Web.UI.WebControls.Button>, co bylo poskytnuto, měli byste přidat kód do uživatelského ovládacího prvku, který bude vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="53d88-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
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
> <span data-ttu-id="53d88-110">Některé ovládací prvky model Windows Forms, například <xref:System.Windows.Forms.TextBox>, jsou vykresleny přímo v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="53d88-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="53d88-111">V těchto instancích <xref:System.Windows.Forms.Control.OnPaint%2A> není metoda nikdy volána, takže výše uvedený příklad nebude nikdy volán.</span><span class="sxs-lookup"><span data-stu-id="53d88-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="53d88-112">Tím se vytvoří metoda, která se spustí pokaždé, když se `MyButton.Paint` událost spustí, a přidá další grafické znázornění ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="53d88-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="53d88-113">Všimněte si, že to nebrání spuštění `MyButton.OnPaint`, a proto veškeré vykreslování obvykle prováděné tlačítkem bude i nadále provedeno kromě vlastního malování.</span><span class="sxs-lookup"><span data-stu-id="53d88-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="53d88-114">Podrobnosti o technologii rozhraní GDI+ a vlastním vykreslování naleznete v tématu [vytváření grafických imagí s rozhraním GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="53d88-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="53d88-115">Pokud chcete mít jedinečný reprezentace vašeho ovládacího prvku, je nejlepší postup vytvořit Zděděný ovládací prvek a napsat pro něj vlastní kód pro vykreslování.</span><span class="sxs-lookup"><span data-stu-id="53d88-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="53d88-116">Podrobnosti najdete v tématu [ovládací prvky vykreslené uživatelem](user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="53d88-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d88-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53d88-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="53d88-118">Ovládací prvky vykreslované uživatelem</span><span class="sxs-lookup"><span data-stu-id="53d88-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="53d88-119">Postupy: Vytvoření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="53d88-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="53d88-120">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="53d88-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
