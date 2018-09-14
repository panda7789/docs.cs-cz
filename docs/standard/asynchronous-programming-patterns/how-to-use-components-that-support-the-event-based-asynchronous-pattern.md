---
title: 'Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: e11bf8af6f56cbdcdcc920cafe145edcf744efed
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45592007"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="1d96c-102">Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="1d96c-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="1d96c-103">Řada komponent poskytují možnost asynchronní provádění své práce.</span><span class="sxs-lookup"><span data-stu-id="1d96c-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="1d96c-104"><xref:System.Media.SoundPlayer> a <xref:System.Windows.Forms.PictureBox> komponenty, například umožňuje načíst podle názvu dalo čekat a Image "v pozadí" i když hlavní podproces stále spuštěná bez přerušení.</span><span class="sxs-lookup"><span data-stu-id="1d96c-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="1d96c-105">Použití asynchronních metod na třídu, která podporuje [založený na událostech přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) může být stejně snadné jako obslužná rutina události se připojuje k součásti _MethodName_  **Dokončení** události, stejně jako ostatní události.</span><span class="sxs-lookup"><span data-stu-id="1d96c-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's _MethodName_**Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="1d96c-106">Při volání _MethodName_**asynchronní** metodu, aplikace bude nadále používat bez přerušení, dokud _MethodName_**dokončeno** událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="1d96c-106">When you call the _MethodName_**Async** method, your application will continue running without interruption until the _MethodName_**Completed** event is raised.</span></span> <span data-ttu-id="1d96c-107">V obslužné rutině události, můžete zkontrolovat <xref:System.ComponentModel.AsyncCompletedEventArgs> parametr určují, jestli asynchronní operace úspěšně dokončena nebo pokud byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="1d96c-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="1d96c-108">Další informace o používání obslužných rutin událostí, naleznete v tématu [Přehled obslužných rutin událostí](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1d96c-108">For more information about using event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="1d96c-109">Následující postup ukazuje, jak použít asynchronní načítání obrázku funkce <xref:System.Windows.Forms.PictureBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1d96c-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="1d96c-110">Aby ovládací prvek PictureBox asynchronně načíst image</span><span class="sxs-lookup"><span data-stu-id="1d96c-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1.  <span data-ttu-id="1d96c-111">Vytvoření instance <xref:System.Windows.Forms.PictureBox> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="1d96c-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2.  <span data-ttu-id="1d96c-112">Přiřadit obslužnou rutinu události pro <xref:System.Windows.Forms.PictureBox.LoadCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="1d96c-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="1d96c-113">Vyhledejte všechny chyby, které mohly nastat během asynchronní stahování.</span><span class="sxs-lookup"><span data-stu-id="1d96c-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="1d96c-114">Toto je také ve kterém můžete zkontrolovat zrušení.</span><span class="sxs-lookup"><span data-stu-id="1d96c-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  <span data-ttu-id="1d96c-115">Přidat dvě tlačítka, volá `loadButton` a `cancelLoadButton`, do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="1d96c-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="1d96c-116">Přidat <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí spuštění a zrušit stahování.</span><span class="sxs-lookup"><span data-stu-id="1d96c-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="1d96c-117">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1d96c-117">Run your application.</span></span>  
  
     <span data-ttu-id="1d96c-118">Jak pokračuje stažení bitové kopie, volně přesouvat formuláře a minimalizovat ji nemaximalizujte.</span><span class="sxs-lookup"><span data-stu-id="1d96c-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d96c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d96c-119">See also</span></span>

- [<span data-ttu-id="1d96c-120">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="1d96c-120">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
- [<span data-ttu-id="1d96c-121">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="1d96c-121">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
