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
ms.openlocfilehash: 0f15cd870efbdcd00dafa071175be078311a9a37
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289392"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="f2ab3-102">Postupy: Použití komponent, které podporují asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="f2ab3-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="f2ab3-103">Řada komponent nabízí možnost asynchronního provádění jejich práce.</span><span class="sxs-lookup"><span data-stu-id="f2ab3-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="f2ab3-104"><xref:System.Media.SoundPlayer>Komponenty a <xref:System.Windows.Forms.PictureBox> například umožňují načíst zvuky a obrázky "na pozadí", zatímco vaše hlavní vlákno pokračuje v běhu bez přerušení.</span><span class="sxs-lookup"><span data-stu-id="f2ab3-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="f2ab3-105">Použití asynchronních metod pro třídu, která podporuje [Přehled asynchronních vzorů založených na událostech](event-based-asynchronous-pattern-overview.md) , může být jednoduché jako připojení obslužné rutiny události k události _methodName_**Completed** , stejně jako u jakékoli jiné události.</span><span class="sxs-lookup"><span data-stu-id="f2ab3-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's _MethodName_**Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="f2ab3-106">Při volání**asynchronní** metody _methodName_bude aplikace nadále běžet bez přerušení, dokud nedojde k vyvolání události _methodName_**Completed** .</span><span class="sxs-lookup"><span data-stu-id="f2ab3-106">When you call the _MethodName_**Async** method, your application will continue running without interruption until the _MethodName_**Completed** event is raised.</span></span> <span data-ttu-id="f2ab3-107">V obslužné rutině události můžete ověřit <xref:System.ComponentModel.AsyncCompletedEventArgs> parametr a zjistit, zda byla asynchronní operace úspěšně dokončena nebo zda byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="f2ab3-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="f2ab3-108">Další informace o použití obslužných rutin událostí najdete v tématu [Přehled obslužných rutin událostí](../../framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f2ab3-108">For more information about using event handlers, see [Event Handlers Overview](../../framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="f2ab3-109">Následující postup ukazuje, jak použít asynchronní funkce načítání obrázků <xref:System.Windows.Forms.PictureBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f2ab3-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="f2ab3-110">Povolení ovládacího prvku PictureBox k asynchronnímu načtení obrázku</span><span class="sxs-lookup"><span data-stu-id="f2ab3-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1. <span data-ttu-id="f2ab3-111"><xref:System.Windows.Forms.PictureBox>Ve formuláři vytvořte instanci komponenty.</span><span class="sxs-lookup"><span data-stu-id="f2ab3-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2. <span data-ttu-id="f2ab3-112">Přiřaďte události obslužnou rutinu události <xref:System.Windows.Forms.PictureBox.LoadCompleted> .</span><span class="sxs-lookup"><span data-stu-id="f2ab3-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="f2ab3-113">Podívejte se na chyby, ke kterým mohlo během asynchronního stahování dojít.</span><span class="sxs-lookup"><span data-stu-id="f2ab3-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="f2ab3-114">Toto je také místo, kde kontrolujete zrušení.</span><span class="sxs-lookup"><span data-stu-id="f2ab3-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3. <span data-ttu-id="f2ab3-115">Do formuláře přidejte dvě tlačítka, která se nazývají `loadButton` a `cancelLoadButton` .</span><span class="sxs-lookup"><span data-stu-id="f2ab3-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="f2ab3-116">Přidejte <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí, které chcete spustit, a zrušte stahování.</span><span class="sxs-lookup"><span data-stu-id="f2ab3-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="f2ab3-117">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f2ab3-117">Run your application.</span></span>  
  
     <span data-ttu-id="f2ab3-118">Při stahování obrázku můžete formulář přesunout volně, minimalizovat a maximalizovat.</span><span class="sxs-lookup"><span data-stu-id="f2ab3-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ab3-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2ab3-119">See also</span></span>

- [<span data-ttu-id="f2ab3-120">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="f2ab3-120">How to: Run an Operation in the Background</span></span>](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="f2ab3-121">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="f2ab3-121">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
