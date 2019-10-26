---
title: Vytvoření InkCanvas v aplikaci WPF v aplikaci Visual Studio
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: ebbf25037921e7802b2bfcb6ffa562d16a849ffa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920254"
---
# <a name="get-started-with-ink-in-wpf"></a><span data-ttu-id="47086-102">Začínáme s rukopisem v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="47086-102">Get Started with Ink in WPF</span></span>

<span data-ttu-id="47086-103">Windows Presentation Foundation (WPF) má funkci rukopisu, která usnadňuje začleňování digitálního inkoustu do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="47086-103">Windows Presentation Foundation (WPF) has an ink feature that makes it easy to incorporate digital ink into your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="47086-104">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47086-104">Prerequisites</span></span>

<span data-ttu-id="47086-105">Chcete-li použít následující příklady, nejprve nainstalujte [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="47086-105">To use the following examples, first install [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="47086-106">Pomáhá také zjistit, jak psát základní aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="47086-106">It also helps to know how to write basic WPF apps.</span></span> <span data-ttu-id="47086-107">Nápovědu Začínáme s WPF naleznete v tématu [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="47086-107">For help getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="quick-start"></a><span data-ttu-id="47086-108">rychlé zprovoznění</span><span class="sxs-lookup"><span data-stu-id="47086-108">Quick Start</span></span>

<span data-ttu-id="47086-109">Tato část vám pomůže napsat jednoduchou aplikaci WPF, která shromažďuje rukopis.</span><span class="sxs-lookup"><span data-stu-id="47086-109">This section helps you write a simple WPF application that collects ink.</span></span>

### <a name="got-ink"></a><span data-ttu-id="47086-110">Máte inkoust?</span><span class="sxs-lookup"><span data-stu-id="47086-110">Got Ink?</span></span>

<span data-ttu-id="47086-111">Vytvoření aplikace WPF podporující rukopis:</span><span class="sxs-lookup"><span data-stu-id="47086-111">To create a WPF app that supports ink:</span></span>

1. <span data-ttu-id="47086-112">Otevřete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="47086-112">Open Visual Studio.</span></span>

2. <span data-ttu-id="47086-113">Vytvořte novou **aplikaci WPF**.</span><span class="sxs-lookup"><span data-stu-id="47086-113">Create a new **WPF App**.</span></span>

   <span data-ttu-id="47086-114">V dialogovém okně **Nový projekt** rozbalte kategorii **nainstalované** > **Visual C#**  nebo **Visual Basic** > **Windows Desktop** .</span><span class="sxs-lookup"><span data-stu-id="47086-114">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="47086-115">Pak vyberte šablonu aplikace **WPF App (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="47086-115">Then, select the **WPF App (.NET Framework)** app template.</span></span> <span data-ttu-id="47086-116">Zadejte název a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="47086-116">Enter a name, and then select **OK**.</span></span>

   <span data-ttu-id="47086-117">Visual Studio vytvoří projekt a v návrháři se otevře *MainWindow. XAML* .</span><span class="sxs-lookup"><span data-stu-id="47086-117">Visual Studio creates the project, and *MainWindow.xaml* opens in the designer.</span></span>

3. <span data-ttu-id="47086-118">Zadejte `<InkCanvas/>` mezi značkami `<Grid>`.</span><span class="sxs-lookup"><span data-stu-id="47086-118">Type `<InkCanvas/>` between the `<Grid>` tags.</span></span>

   ![Návrhář XAML se značkou InkCanvas](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. <span data-ttu-id="47086-120">Stisknutím klávesy **F5** spusťte aplikaci v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="47086-120">Press **F5** to launch your application in the debugger.</span></span>

5. <span data-ttu-id="47086-121">Pomocí pera nebo myši napište do okna **Hello World** .</span><span class="sxs-lookup"><span data-stu-id="47086-121">Using a stylus or mouse, write **hello world** in the window.</span></span>

<span data-ttu-id="47086-122">Napsali jste ekvivalent inkoustu aplikace "Hello World" s pouze 12 klávesami.</span><span class="sxs-lookup"><span data-stu-id="47086-122">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>

### <a name="spice-up-your-app"></a><span data-ttu-id="47086-123">Spice své aplikace</span><span class="sxs-lookup"><span data-stu-id="47086-123">Spice Up Your App</span></span>

<span data-ttu-id="47086-124">Pojďme využít některé funkce WPF.</span><span class="sxs-lookup"><span data-stu-id="47086-124">Let’s take advantage of some features of the WPF.</span></span> <span data-ttu-id="47086-125">Nahraďte vše mezi otevíracím a zavíracím \<oknem > značky následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="47086-125">Replace everything between the opening and closing \<Window> tags with the following markup:</span></span>

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

<span data-ttu-id="47086-126">Tento kód XAML vytvoří pozadí barevného štětce na ploše pro rukopis.</span><span class="sxs-lookup"><span data-stu-id="47086-126">This XAML creates a gradient brush background on your inking surface.</span></span>

![Barvy přechodu na rukopisné ploše v aplikaci WPF](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a><span data-ttu-id="47086-128">Přidat kód za XAML</span><span class="sxs-lookup"><span data-stu-id="47086-128">Add Some Code Behind the XAML</span></span>

<span data-ttu-id="47086-129">Zatímco XAML usnadňuje návrh uživatelského rozhraní, všechny reálné aplikace musí přidat kód pro zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="47086-129">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="47086-130">Tady je jednoduchý příklad, který se přiblíží inkoustu v reakci na pravé tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="47086-130">Here is a simple example that zooms in on the ink in response to a right-click from a mouse.</span></span>

1. <span data-ttu-id="47086-131">Nastavte obslužnou rutinu `MouseRightButtonUp` ve vašem kódu XAML:</span><span class="sxs-lookup"><span data-stu-id="47086-131">Set the `MouseRightButtonUp` handler in your XAML:</span></span>

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. <span data-ttu-id="47086-132">V **Průzkumník řešení**rozbalte MainWindow. XAML a otevřete soubor kódu na pozadí (MainWindow.XAML.cs nebo MainWindow. XAML. vb).</span><span class="sxs-lookup"><span data-stu-id="47086-132">In **Solution Explorer**, expand MainWindow.xaml and open the code-behind file (MainWindow.xaml.cs or MainWindow.xaml.vb).</span></span> <span data-ttu-id="47086-133">Přidejte následující kód obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="47086-133">Add the following event handler code:</span></span>

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. <span data-ttu-id="47086-134">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="47086-134">Run the application.</span></span> <span data-ttu-id="47086-135">Přidejte nějaký rukopis, klikněte na něj pravým tlačítkem myši nebo proveďte ekvivalent stisknutí klávesy stylus a podržením stylusu.</span><span class="sxs-lookup"><span data-stu-id="47086-135">Add some ink, and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>

   <span data-ttu-id="47086-136">Zobrazení se přiblíží pokaždé, když kliknete pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="47086-136">The display zooms in each time you click with the right mouse button.</span></span>

### <a name="use-procedural-code-instead-of-xaml"></a><span data-ttu-id="47086-137">Použití procedurálního kódu místo XAML</span><span class="sxs-lookup"><span data-stu-id="47086-137">Use Procedural Code Instead of XAML</span></span>

<span data-ttu-id="47086-138">Ke všem funkcím WPF můžete přistupovat z procedurálního kódu.</span><span class="sxs-lookup"><span data-stu-id="47086-138">You can access all WPF features from procedural code.</span></span> <span data-ttu-id="47086-139">Pomocí těchto kroků můžete vytvořit aplikaci Hello World Ink World pro WPF, která vůbec nepoužívá žádný XAML.</span><span class="sxs-lookup"><span data-stu-id="47086-139">Follow these steps to create a "Hello Ink World" application for WPF that doesn’t use any XAML at all.</span></span>

1. <span data-ttu-id="47086-140">Vytvořte nový projekt konzolové aplikace v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="47086-140">Create a new console application project in Visual Studio.</span></span>

   <span data-ttu-id="47086-141">V dialogovém okně **Nový projekt** rozbalte kategorii **nainstalované** > **Visual C#**  nebo **Visual Basic** > **Windows Desktop** .</span><span class="sxs-lookup"><span data-stu-id="47086-141">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="47086-142">Pak vyberte šablonu aplikace **Konzolová aplikace (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="47086-142">Then, select the **Console App (.NET Framework)** app template.</span></span> <span data-ttu-id="47086-143">Zadejte název a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="47086-143">Enter a name, and then select **OK**.</span></span>

1. <span data-ttu-id="47086-144">Vložte následující kód do souboru Program.cs nebo program. vb:</span><span class="sxs-lookup"><span data-stu-id="47086-144">Paste the following code into the Program.cs or Program.vb file:</span></span>

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. <span data-ttu-id="47086-145">Přidejte odkazy na PresentationCore, PresentationFramework a WindowsBase sestavení tak, že kliknete pravým tlačítkem na **odkazy** v **Průzkumník řešení** a zvolíte **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="47086-145">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies by right-clicking on **References** in **Solution Explorer** and choosing **Add Reference**.</span></span>

   ![Správce odkazů zobrazující PresentationCore a PresentationFramework](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. <span data-ttu-id="47086-147">Sestavte aplikaci stisknutím klávesy **F5**.</span><span class="sxs-lookup"><span data-stu-id="47086-147">Build the application by pressing **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="47086-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47086-148">See also</span></span>

- [<span data-ttu-id="47086-149">Rukopis</span><span class="sxs-lookup"><span data-stu-id="47086-149">Digital Ink</span></span>](digital-ink.md)
- [<span data-ttu-id="47086-150">Shromáždění rukopisu</span><span class="sxs-lookup"><span data-stu-id="47086-150">Collecting Ink</span></span>](collecting-ink.md)
- [<span data-ttu-id="47086-151">Rozpoznávání textu psaného rukou</span><span class="sxs-lookup"><span data-stu-id="47086-151">Handwriting Recognition</span></span>](handwriting-recognition.md)
- [<span data-ttu-id="47086-152">Uložení rukopisu</span><span class="sxs-lookup"><span data-stu-id="47086-152">Storing Ink</span></span>](storing-ink.md)
