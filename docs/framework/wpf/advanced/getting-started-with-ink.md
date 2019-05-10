---
title: Vytvoření objektu InkCanvas v aplikaci WPF v sadě Visual Studio
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: d633111c5abc572b0fc27c1a5b32050681504073
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753007"
---
# <a name="get-started-with-ink-in-wpf"></a><span data-ttu-id="1f860-102">Začínáme s inkoustem v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="1f860-102">Get Started with Ink in WPF</span></span>

<span data-ttu-id="1f860-103">Windows Presentation Foundation (WPF) obsahuje funkci rukopisu, se kterou snadno začlenit digitálních inkoust do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f860-103">Windows Presentation Foundation (WPF) has an ink feature that makes it easy to incorporate digital ink into your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1f860-104">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f860-104">Prerequisites</span></span>

<span data-ttu-id="1f860-105">Pokud chcete použít v následujících příkladech, nejprve nainstalujte [sady Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="1f860-105">To use the following examples, first install [Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="1f860-106">Pomáhá také vědět, jak zapsat základní aplikace pro WPF.</span><span class="sxs-lookup"><span data-stu-id="1f860-106">It also helps to know how to write basic WPF apps.</span></span> <span data-ttu-id="1f860-107">Začínáme s WPF pomoc najdete v tématu [názorný postup: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="1f860-107">For help getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="quick-start"></a><span data-ttu-id="1f860-108">Rychlý Start</span><span class="sxs-lookup"><span data-stu-id="1f860-108">Quick Start</span></span>

<span data-ttu-id="1f860-109">Tato část vám pomůže psát jednoduché aplikace WPF, která shromažďuje rukopisu.</span><span class="sxs-lookup"><span data-stu-id="1f860-109">This section helps you write a simple WPF application that collects ink.</span></span>

### <a name="got-ink"></a><span data-ttu-id="1f860-110">Máte inkoustu?</span><span class="sxs-lookup"><span data-stu-id="1f860-110">Got Ink?</span></span>

<span data-ttu-id="1f860-111">Vytvoření aplikace WPF, která podporuje rukopisu:</span><span class="sxs-lookup"><span data-stu-id="1f860-111">To create a WPF app that supports ink:</span></span>

1. <span data-ttu-id="1f860-112">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f860-112">Open Visual Studio.</span></span>

2. <span data-ttu-id="1f860-113">Vytvořte nový **aplikace WPF**.</span><span class="sxs-lookup"><span data-stu-id="1f860-113">Create a new **WPF App**.</span></span>

   <span data-ttu-id="1f860-114">V **nový projekt** dialogového okna, rozbalte **nainstalováno** > **Visual C#** nebo **jazyka Visual Basic**  >   **Windows Desktop** kategorie.</span><span class="sxs-lookup"><span data-stu-id="1f860-114">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="1f860-115">Vyberte **aplikace WPF (.NET Framework)** šablony aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f860-115">Then, select the **WPF App (.NET Framework)** app template.</span></span> <span data-ttu-id="1f860-116">Zadejte název a potom vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="1f860-116">Enter a name, and then select **OK**.</span></span>

   <span data-ttu-id="1f860-117">Visual Studio vytvoří projekt, a *souboru MainWindow.xaml* otevře v návrháři.</span><span class="sxs-lookup"><span data-stu-id="1f860-117">Visual Studio creates the project, and *MainWindow.xaml* opens in the designer.</span></span>

3. <span data-ttu-id="1f860-118">Typ `<InkCanvas/>` mezi `<Grid>` značky.</span><span class="sxs-lookup"><span data-stu-id="1f860-118">Type `<InkCanvas/>` between the `<Grid>` tags.</span></span>

   ![Návrhář XAML s inkcanvas – značka](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. <span data-ttu-id="1f860-120">Stisknutím klávesy **F5** ke spuštění aplikace v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="1f860-120">Press **F5** to launch your application in the debugger.</span></span>

5. <span data-ttu-id="1f860-121">Pomocí pera nebo myš, zápis **hello world** v okně.</span><span class="sxs-lookup"><span data-stu-id="1f860-121">Using a stylus or mouse, write **hello world** in the window.</span></span>

<span data-ttu-id="1f860-122">Jste napsali ekvivalent inkoustu aplikace "hello world" pomocí pouze 12 stisknutí kláves!</span><span class="sxs-lookup"><span data-stu-id="1f860-122">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>

### <a name="spice-up-your-app"></a><span data-ttu-id="1f860-123">Okořeňte kapacity aplikace</span><span class="sxs-lookup"><span data-stu-id="1f860-123">Spice Up Your App</span></span>

<span data-ttu-id="1f860-124">Můžeme využít některé funkce WPF.</span><span class="sxs-lookup"><span data-stu-id="1f860-124">Let’s take advantage of some features of the WPF.</span></span> <span data-ttu-id="1f860-125">Nahradit vše, co mezi otevírací a zavírací \<okna > značky následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="1f860-125">Replace everything between the opening and closing \<Window> tags with the following markup:</span></span>

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

<span data-ttu-id="1f860-126">Tento XAML vytvoří štětce přechodu pozadí na pera surface.</span><span class="sxs-lookup"><span data-stu-id="1f860-126">This XAML creates a gradient brush background on your inking surface.</span></span>

![Barvy přechodu na rukopis plochu v aplikaci WPF](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a><span data-ttu-id="1f860-128">Přidat některé kódu na pozadí XAML</span><span class="sxs-lookup"><span data-stu-id="1f860-128">Add Some Code Behind the XAML</span></span>

<span data-ttu-id="1f860-129">Zatímco XAML velmi usnadňuje návrh uživatelského rozhraní, žádné reálné aplikaci je potřeba přidat kód pro zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="1f860-129">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="1f860-130">Tady je jednoduchý příklad, který se přiblíží rukopisu v reakci klikněte pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="1f860-130">Here is a simple example that zooms in on the ink in response to a right-click from a mouse.</span></span>

1. <span data-ttu-id="1f860-131">Nastavte `MouseRightButtonUp` obslužné rutiny ve vaší XAML:</span><span class="sxs-lookup"><span data-stu-id="1f860-131">Set the `MouseRightButtonUp` handler in your XAML:</span></span>

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. <span data-ttu-id="1f860-132">V **Průzkumníka řešení**, rozbalte soubor MainWindow.xaml a otevřete soubor kódu na pozadí (MainWindow.xaml.cs nebo soubor MainWindow.xaml.vb).</span><span class="sxs-lookup"><span data-stu-id="1f860-132">In **Solution Explorer**, expand MainWindow.xaml and open the code-behind file (MainWindow.xaml.cs or MainWindow.xaml.vb).</span></span> <span data-ttu-id="1f860-133">Přidejte následující kód obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="1f860-133">Add the following event handler code:</span></span>

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. <span data-ttu-id="1f860-134">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1f860-134">Run the application.</span></span> <span data-ttu-id="1f860-135">Přidat nějaký inkoust a potom klikněte pravým tlačítkem myši nebo provést ekvivalent stiskněte a podržte pomocí pera.</span><span class="sxs-lookup"><span data-stu-id="1f860-135">Add some ink, and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>

   <span data-ttu-id="1f860-136">Zobrazení přiblíží pokaždé, když klepnete pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="1f860-136">The display zooms in each time you click with the right mouse button.</span></span>

### <a name="use-procedural-code-instead-of-xaml"></a><span data-ttu-id="1f860-137">Použít kód procedury namísto XAML</span><span class="sxs-lookup"><span data-stu-id="1f860-137">Use Procedural Code Instead of XAML</span></span>

<span data-ttu-id="1f860-138">Všechny funkce WPF můžete přistupovat z kódu procedury.</span><span class="sxs-lookup"><span data-stu-id="1f860-138">You can access all WPF features from procedural code.</span></span> <span data-ttu-id="1f860-139">Postupujte podle těchto kroků můžete vytvořit "inkoustu aplikace Hello World" pro WPF, která nebude vůbec používat jakékoli XAML.</span><span class="sxs-lookup"><span data-stu-id="1f860-139">Follow these steps to create a "Hello Ink World" application for WPF that doesn’t use any XAML at all.</span></span>

1. <span data-ttu-id="1f860-140">Vytvořte nový projekt konzolové aplikace v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f860-140">Create a new console application project in Visual Studio.</span></span>

   <span data-ttu-id="1f860-141">V **nový projekt** dialogového okna, rozbalte **nainstalováno** > **Visual C#** nebo **jazyka Visual Basic**  >   **Windows Desktop** kategorie.</span><span class="sxs-lookup"><span data-stu-id="1f860-141">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="1f860-142">Vyberte **Konzolová aplikace (.NET Framework)** šablony aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f860-142">Then, select the **Console App (.NET Framework)** app template.</span></span> <span data-ttu-id="1f860-143">Zadejte název a potom vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="1f860-143">Enter a name, and then select **OK**.</span></span>

1. <span data-ttu-id="1f860-144">Vložte následující kód do souboru Program.cs nebo soubor Program.vb:</span><span class="sxs-lookup"><span data-stu-id="1f860-144">Paste the following code into the Program.cs or Program.vb file:</span></span>

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. <span data-ttu-id="1f860-145">Přidat odkazy na sestavení PresentationCore PresentationFramework a WindowsBase kliknutím pravým tlačítkem na **odkazy** v **Průzkumníka řešení** a zvolíte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="1f860-145">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies by right-clicking on **References** in **Solution Explorer** and choosing **Add Reference**.</span></span>

   ![Zobrazuje PresentationCore a PresentationFramework správce odkazů](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. <span data-ttu-id="1f860-147">Sestavte aplikaci stisknutím klávesy **F5**.</span><span class="sxs-lookup"><span data-stu-id="1f860-147">Build the application by pressing **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f860-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f860-148">See also</span></span>

- [<span data-ttu-id="1f860-149">Rukopis</span><span class="sxs-lookup"><span data-stu-id="1f860-149">Digital Ink</span></span>](digital-ink.md)
- [<span data-ttu-id="1f860-150">Shromáždění rukopisu</span><span class="sxs-lookup"><span data-stu-id="1f860-150">Collecting Ink</span></span>](collecting-ink.md)
- [<span data-ttu-id="1f860-151">Rozpoznávání textu psaného rukou</span><span class="sxs-lookup"><span data-stu-id="1f860-151">Handwriting Recognition</span></span>](handwriting-recognition.md)
- [<span data-ttu-id="1f860-152">Uložení rukopisu</span><span class="sxs-lookup"><span data-stu-id="1f860-152">Storing Ink</span></span>](storing-ink.md)
