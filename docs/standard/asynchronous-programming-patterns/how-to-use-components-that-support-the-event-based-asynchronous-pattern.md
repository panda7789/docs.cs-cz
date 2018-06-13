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
ms.openlocfilehash: f0bf9b1da76033ef40cc72657ee722083a6f8b1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567626"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="f2be6-102">Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="f2be6-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="f2be6-103">Celá řada komponent poskytují možnost provedení práci asynchronně.</span><span class="sxs-lookup"><span data-stu-id="f2be6-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="f2be6-104"><xref:System.Media.SoundPlayer> a <xref:System.Windows.Forms.PictureBox> součásti, například umožňuje načíst vyznívá a bitové kopie "v pozadí", zatímco hlavní vlákno stále spuštěna bez přerušení.</span><span class="sxs-lookup"><span data-stu-id="f2be6-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="f2be6-105">Použití asynchronních metod na třídu, která podporuje [na základě událostí přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) může být stejně jednoduché jako obslužné rutiny události se připojuje k součásti *MethodName *** dokončeno** události stejně jako ostatní události.</span><span class="sxs-lookup"><span data-stu-id="f2be6-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's *MethodName***Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="f2be6-106">Při volání *MethodName *** asynchronní** metoda, vaše aplikace bude dál běžet bez přerušení, dokud *MethodName *** dokončeno** událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="f2be6-106">When you call the *MethodName***Async** method, your application will continue running without interruption until the *MethodName***Completed** event is raised.</span></span> <span data-ttu-id="f2be6-107">V obslužné rutině událostí, můžete zkontrolovat <xref:System.ComponentModel.AsyncCompletedEventArgs> parametr k určení, pokud asynchronní operace úspěšně dokončena, nebo pokud byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="f2be6-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="f2be6-108">Další informace o používání obslužných rutin událostí najdete v tématu [Přehled obslužných rutin událostí](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f2be6-108">For more information about using event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="f2be6-109">Následující postup ukazuje, jak použít funkci asynchronní načítání bitové kopie systému <xref:System.Windows.Forms.PictureBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f2be6-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="f2be6-110">Chcete-li povolit asynchronně načíst obrázek ovládacího prvku PictureBox</span><span class="sxs-lookup"><span data-stu-id="f2be6-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1.  <span data-ttu-id="f2be6-111">Vytvoření instance <xref:System.Windows.Forms.PictureBox> součásti do formuláře.</span><span class="sxs-lookup"><span data-stu-id="f2be6-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2.  <span data-ttu-id="f2be6-112">Obslužné rutiny události pro přiřazení <xref:System.Windows.Forms.PictureBox.LoadCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="f2be6-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="f2be6-113">Zkontrolujte chyby, ke kterým mohlo dojít během asynchronní stahování.</span><span class="sxs-lookup"><span data-stu-id="f2be6-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="f2be6-114">Toto je také kde kontrolovat zrušení.</span><span class="sxs-lookup"><span data-stu-id="f2be6-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  <span data-ttu-id="f2be6-115">Přidat dvě tlačítka, nazývá `loadButton` a `cancelLoadButton`, do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="f2be6-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="f2be6-116">Přidat <xref:System.Windows.Forms.Control.Click> obslužné rutiny události spuštění a stahování zrušte.</span><span class="sxs-lookup"><span data-stu-id="f2be6-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="f2be6-117">Spusťte svoji aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f2be6-117">Run your application.</span></span>  
  
     <span data-ttu-id="f2be6-118">Jak pokračuje stažení bitové kopie, volně přesouvat formuláře a minimalizovat ji nemaximalizujte.</span><span class="sxs-lookup"><span data-stu-id="f2be6-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2be6-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2be6-119">See Also</span></span>  
 [<span data-ttu-id="f2be6-120">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="f2be6-120">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="f2be6-121">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="f2be6-121">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="f2be6-122">NENÍ v sestavení: Více vláken v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2be6-122">NOT IN BUILD: Multithreading in Visual Basic</span></span>](https://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)
