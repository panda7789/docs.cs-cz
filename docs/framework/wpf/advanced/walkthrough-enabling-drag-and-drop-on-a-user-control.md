---
title: "Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 360b453b2a25b6822485f18cc81cb43e313949eb
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="ca0d2-102">Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku</span><span class="sxs-lookup"><span data-stu-id="ca0d2-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>
<span data-ttu-id="ca0d2-103">Tento návod ukazuje, jak vytvořit vlastní uživatelský ovládací prvek, které mohou být zahrnuty v přenos dat se přetažení myší v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ca0d2-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="ca0d2-104">V tomto návodu vytvoříte vlastní WPF <xref:System.Windows.Controls.UserControl> představující obrazce kruh.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="ca0d2-105">Funkce se implementovat v ovládacím prvku povolit přenos dat pomocí přetahování myší.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="ca0d2-106">Například přetažením z jednoho kruh ovládacího prvku do jiného data barvu výplně se zkopíruje ze zdroje kruh k cíli.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="ca0d2-107">Přetažením z ovládacího prvku kruh k <xref:System.Windows.Controls.TextBox>, řetězcovou reprezentaci barvu výplně se zkopíruje do <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="ca0d2-108">Také vytvoříte malé aplikaci, která obsahuje dva ovládací prvky panelu a <xref:System.Windows.Controls.TextBox> funkci přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="ca0d2-109">Budete psát kód, který umožňuje panelů zpracovat vynechaných kruh data, která vám umožní přesuňte nebo zkopírujte kroužky z podřízené kolekce jednoho z nich na druhý.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>  
  
 <span data-ttu-id="ca0d2-110">Tento návod znázorňuje následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="ca0d2-110">This walkthrough illustrates the following tasks:</span></span>  
  
-   <span data-ttu-id="ca0d2-111">Vytvoření vlastního uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-111">Create a custom user control.</span></span>  
  
-   <span data-ttu-id="ca0d2-112">Povolte uživatelského ovládacího prvku jako zdroje operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-112">Enable the user control to be a drag source.</span></span>  
  
-   <span data-ttu-id="ca0d2-113">Povolte uživatelského ovládacího prvku jako cíle přetažení.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-113">Enable the user control to be a drop target.</span></span>  
  
-   <span data-ttu-id="ca0d2-114">Povolte panel přijímat data z uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-114">Enable a panel to receive data dropped from the user control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ca0d2-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca0d2-115">Prerequisites</span></span>  
 <span data-ttu-id="ca0d2-116">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="ca0d2-116">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="ca0d2-117">Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="ca0d2-117">Visual Studio 2010</span></span>  
  
## <a name="creating-the-application-project"></a><span data-ttu-id="ca0d2-118">Vytvoření projektu aplikace</span><span class="sxs-lookup"><span data-stu-id="ca0d2-118">Creating the Application Project</span></span>  
 <span data-ttu-id="ca0d2-119">V této části vytvoříte infrastrukturu aplikace, která zahrnuje na hlavní stránce s dvěma panelů a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-119">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
### <a name="to-create-the-project"></a><span data-ttu-id="ca0d2-120">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="ca0d2-120">To create the project</span></span>  
  
1.  <span data-ttu-id="ca0d2-121">Vytvořte nový projekt aplikace WPF v jazyce Visual Basic a Visual C# s názvem `DragDropExample`.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-121">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="ca0d2-122">Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="ca0d2-122">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="ca0d2-123">Otevřete MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-123">Open MainWindow.xaml.</span></span>  
  
3.  <span data-ttu-id="ca0d2-124">Přidejte následující kód mezi počáteční a koncovou <xref:System.Windows.Controls.Grid> značky.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-124">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>  
  
     <span data-ttu-id="ca0d2-125">Tento kód vytvoří uživatelské rozhraní pro testovací aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-125">This markup creates the user interface for the test application.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a><span data-ttu-id="ca0d2-126">Přidávání nového uživatele do projektu</span><span class="sxs-lookup"><span data-stu-id="ca0d2-126">Adding a New User Control to the Project</span></span>  
 <span data-ttu-id="ca0d2-127">V této části přidáte nový uživatelský ovládací prvek do projektu.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-127">In this section, you will add a new user control to the project.</span></span>  
  
### <a name="to-add-a-new-user-control"></a><span data-ttu-id="ca0d2-128">Chcete-li přidat nový uživatelský ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="ca0d2-128">To add a new user control</span></span>  
  
1.  <span data-ttu-id="ca0d2-129">V nabídce Projekt, vyberte **přidat uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-129">On the Project menu, select **Add User Control**.</span></span>  
  
2.  <span data-ttu-id="ca0d2-130">V dialogovém okně Přidat novou položku změňte název `Circle.xaml`a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-130">In the Add New Item dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>  
  
     <span data-ttu-id="ca0d2-131">Circle.XAML a jeho kódu se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-131">Circle.xaml and its code-behind is added to the project.</span></span>  
  
3.  <span data-ttu-id="ca0d2-132">Otevřete Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-132">Open Circle.xaml.</span></span>  
  
     <span data-ttu-id="ca0d2-133">Tento soubor bude obsahovat prvky uživatelského rozhraní uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-133">This file will contain the user interface elements of the user control.</span></span>  
  
4.  <span data-ttu-id="ca0d2-134">Přidejte následující kód do kořenového adresáře <xref:System.Windows.Controls.Grid> vytvoření jednoduché uživatelského ovládacího prvku, který má modrý kruh jako jeho uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-134">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  <span data-ttu-id="ca0d2-135">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-135">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
6.  <span data-ttu-id="ca0d2-136">V jazyce C# přidejte následující kód po výchozí konstruktor k vytvoření kopírovacího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-136">In C#, add the following code after the default constructor to create a copy constructor.</span></span> <span data-ttu-id="ca0d2-137">V jazyce Visual Basic přidejte následující kód k vytvoření výchozí konstruktor a kopírovacího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-137">In Visual Basic, add the following code to create both a default constructor and a copy constructor.</span></span>  
  
     <span data-ttu-id="ca0d2-138">Chcete-li povolit uživatelský ovládací prvek, který se má zkopírovat, přidejte metodu konstruktoru kopírování v souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-138">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="ca0d2-139">V zjednodušené kruh uživatelského ovládacího prvku, pouze zkopírujete výplně a velikost uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-139">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a><span data-ttu-id="ca0d2-140">Chcete-li přidat uživatelský ovládací prvek do hlavního okna</span><span class="sxs-lookup"><span data-stu-id="ca0d2-140">To add the user control to the main window</span></span>  
  
1.  <span data-ttu-id="ca0d2-141">Otevřete MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-141">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="ca0d2-142">Přidejte následující XAML pro otevření <xref:System.Windows.Window> značka vytvořit odkaz na obor názvů XML pro aktuální aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-142">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  <span data-ttu-id="ca0d2-143">V prvním <xref:System.Windows.Controls.StackPanel>, přidejte následující XAML vytvořit dvě instance kruh uživatelského ovládacího prvku v prvním panelu.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-143">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     <span data-ttu-id="ca0d2-144">Úplné XAML pro panel vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-144">The full XAML for the panel looks like the following.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a><span data-ttu-id="ca0d2-145">Implementace události zdroje přetažení z uživatelského ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ca0d2-145">Implementing Drag Source Events in the User Control</span></span>  
 <span data-ttu-id="ca0d2-146">V této části se přepíše <xref:System.Windows.UIElement.OnMouseMove%2A> metoda a spustit operaci přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-146">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>  
  
 <span data-ttu-id="ca0d2-147">Pokud je spuštěná přetáhněte (stisknutí tlačítka myši a myší), bude balíček data, která mají být převedeny do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-147">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="ca0d2-148">V takovém případě bude ovládací prvek kruh balíček tři položky data; řetězcová reprezentace jeho barvu výplně, double reprezentace výšku a kopii sám sebe.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-148">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="ca0d2-149">Inicializace operace přetažení myší</span><span class="sxs-lookup"><span data-stu-id="ca0d2-149">To initiate a drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="ca0d2-150">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-150">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="ca0d2-151">Přidejte následující <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání zajistit třída zpracování <xref:System.Windows.UIElement.MouseMove> událostí.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-151">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     <span data-ttu-id="ca0d2-152">To <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="ca0d2-152">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="ca0d2-153">Kontroluje, zda je levé tlačítko stisknutí při přesunutí myši.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-153">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>  
  
    -   <span data-ttu-id="ca0d2-154">Balíčky kruh dat do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-154">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="ca0d2-155">V takovém případě ovládacího prvku kruh balíčky tři položky data; řetězcová reprezentace jeho barvu výplně, double reprezentace výšku a kopii sám sebe.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-155">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
    -   <span data-ttu-id="ca0d2-156">Volá statických <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metoda inicializace operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-156">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="ca0d2-157">Předejte tyto tři parametry, které chcete <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda:</span><span class="sxs-lookup"><span data-stu-id="ca0d2-157">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>  
  
        -   <span data-ttu-id="ca0d2-158">`dragSource`– Odkaz na tento ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-158">`dragSource` – A reference to this control.</span></span>  
  
        -   <span data-ttu-id="ca0d2-159">`data`– Na <xref:System.Windows.DataObject> vytvořené v předchozí kód.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-159">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>  
  
        -   <span data-ttu-id="ca0d2-160">`allowedEffects`– Povolených operací přetažení myší, které jsou <xref:System.Windows.DragDropEffects.Copy> nebo <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-160">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="ca0d2-161">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-161">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="ca0d2-162">Klikněte na jednu z ovládacích prvků kruh a přetáhněte jej přes na panely na kruh a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-162">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="ca0d2-163">Při přetažení přes <xref:System.Windows.Controls.TextBox>, změní na znamenat přesunu.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-163">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>  
  
5.  <span data-ttu-id="ca0d2-164">Při přetahování kruh přes <xref:System.Windows.Controls.TextBox>, stiskněte klávesu CTRL.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-164">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the CTRL key.</span></span> <span data-ttu-id="ca0d2-165">Všimněte si, jak kurzoru změní udávajících kopii.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-165">Notice how the cursor changes to indicate a copy.</span></span>  
  
6.  <span data-ttu-id="ca0d2-166">Přetáhnout myší na kruh <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-166">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="ca0d2-167">Řetězcová reprezentace barvu výplně na kruh se připojí k <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-167">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
     <span data-ttu-id="ca0d2-168">![Řetězec reprezentace barvu výplně kruhu](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="ca0d2-168">![String representation of Circle's fill color](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>  
  
 <span data-ttu-id="ca0d2-169">Ve výchozím nastavení bude během operace přetažení myší označíte, jaký vliv má vyřazení dat bude mít změnit kurzor.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-169">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="ca0d2-170">Můžete přizpůsobit zpětnou vazbu pro uživatele ve zpracování <xref:System.Windows.UIElement.GiveFeedback> událostí a nastavení různých kurzoru.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-170">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>  
  
### <a name="to-give-feedback-to-the-user"></a><span data-ttu-id="ca0d2-171">Poskytněte zpětnou vazbu pro uživatele</span><span class="sxs-lookup"><span data-stu-id="ca0d2-171">To give feedback to the user</span></span>  
  
1.  <span data-ttu-id="ca0d2-172">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-172">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="ca0d2-173">Přidejte následující <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání zajistit třída zpracování <xref:System.Windows.UIElement.GiveFeedback> událostí.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-173">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     <span data-ttu-id="ca0d2-174">To <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="ca0d2-174">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="ca0d2-175">Kontroluje <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> hodnoty, které jsou nastaveny v cíle přetažení <xref:System.Windows.UIElement.DragOver> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-175">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
    -   <span data-ttu-id="ca0d2-176">Nastaví vlastní kurzor na základě <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-176">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="ca0d2-177">Kurzor je určený pro váš názor visual uživateli o jaký vliv má vyřazení dat bude mít.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-177">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>  
  
3.  <span data-ttu-id="ca0d2-178">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-178">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="ca0d2-179">Přetáhněte jeden kruhu určuje přes na panely na kruh a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-179">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="ca0d2-180">Všimněte si, že kurzory jsou nyní vlastní kurzory, které jste zadali v <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsat.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-180">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>  
  
     <span data-ttu-id="ca0d2-181">![Přetáhnout myší s vlastní kurzory](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="ca0d2-181">![Drag and drop with custom cursors](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>  
  
5.  <span data-ttu-id="ca0d2-182">Vyberte text `green` z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-182">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
6.  <span data-ttu-id="ca0d2-183">Přetáhněte `green` text do ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-183">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="ca0d2-184">Všimněte si, že se zobrazují kurzory výchozí znamenat důsledky operaci přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-184">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="ca0d2-185">Kurzor zpětná vazba je vždycky nastavený podle zdroje operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-185">The feedback cursor is always set by the drag source.</span></span>  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a><span data-ttu-id="ca0d2-186">Implementace cíl události v uživatelského ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ca0d2-186">Implementing Drop Target Events in the User Control</span></span>  
 <span data-ttu-id="ca0d2-187">V této části zadáte, zda je uživatelského ovládacího prvku cíle přetažení, přepsání metody, které umožní uživateli řídit jako cíle přetažení a zpracovat data, která je na něm vyřazen.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-187">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="ca0d2-188">Chcete-li povolit uživatelského ovládacího prvku jako cíle přetažení</span><span class="sxs-lookup"><span data-stu-id="ca0d2-188">To enable the user control to be a drop target</span></span>  
  
1.  <span data-ttu-id="ca0d2-189">Otevřete Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-189">Open Circle.xaml.</span></span>  
  
2.  <span data-ttu-id="ca0d2-190">Při otevírání <xref:System.Windows.Controls.UserControl> značky, přidejte <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost a nastavte ji na `true`.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-190">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <span data-ttu-id="ca0d2-191"><xref:System.Windows.UIElement.OnDrop%2A> Metoda je volána, když <xref:System.Windows.UIElement.AllowDrop%2A> je nastavena na `true` a data ze zdroje operace přetažení přetažení na kruh uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-191">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="ca0d2-192">Tato metoda bude zpracovávat data, která byla vynechána a použít data na kruh.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-192">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>  
  
### <a name="to-process-the-dropped-data"></a><span data-ttu-id="ca0d2-193">Zpracování vynechaných dat</span><span class="sxs-lookup"><span data-stu-id="ca0d2-193">To process the dropped data</span></span>  
  
1.  <span data-ttu-id="ca0d2-194">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-194">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="ca0d2-195">Přidejte následující <xref:System.Windows.UIElement.OnDrop%2A> přepsání zajistit třída zpracování <xref:System.Windows.UIElement.Drop> událostí.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-195">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     <span data-ttu-id="ca0d2-196">To <xref:System.Windows.UIElement.OnDrop%2A> přepsání provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="ca0d2-196">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="ca0d2-197">Používá <xref:System.Windows.DataObject.GetDataPresent%2A> metodu za účelem zjištění, zda taženou dat obsahuje objekt řetězce.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-197">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>  
  
    -   <span data-ttu-id="ca0d2-198">Používá <xref:System.Windows.DataObject.GetData%2A> metoda extrahovat data řetězec, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-198">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>  
  
    -   <span data-ttu-id="ca0d2-199">Používá <xref:System.Windows.Media.BrushConverter> pokusí převést řetězec, který má <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-199">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="ca0d2-200">Pokud převod úspěšný, použije štětce k <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> , který poskytuje uživatelské rozhraní ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-200">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>  
  
    -   <span data-ttu-id="ca0d2-201">Značky <xref:System.Windows.UIElement.Drop> událostí jako zpracování.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-201">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="ca0d2-202">Událost umístění byste měli označit jako zpracování, další prvky, které obdrží tato událost věděli, že uživatelského ovládacího prvku kruh zajistit jeho.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-202">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>  
  
3.  <span data-ttu-id="ca0d2-203">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-203">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="ca0d2-204">Vyberte text `green` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-204">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="ca0d2-205">Přetáhněte text do ovládacího prvku kruh a umístěte jej.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-205">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="ca0d2-206">Kruhu změní z blue zeleně.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-206">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="ca0d2-207">![Převést řetězec na štětce](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="ca0d2-207">![Convert a string to a brush](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>  
  
6.  <span data-ttu-id="ca0d2-208">Zadejte text `green` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-208">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="ca0d2-209">Vyberte text `gre` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-209">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="ca0d2-210">Přetáhněte ji do ovládacího prvku kruh a umístěte jej.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-210">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="ca0d2-211">Všimněte si, že kurzoru změní na znamenat, že rozevírací je povoleno, ale barvu kruhu nezmění, protože `gre` není platnou barvu.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-211">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>  
  
9. <span data-ttu-id="ca0d2-212">Z ovládacího prvku zelená kruh přetažení na modré ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-212">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="ca0d2-213">Kruhu změní z blue zeleně.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-213">The Circle changes from blue to green.</span></span> <span data-ttu-id="ca0d2-214">Všimněte si, že se zobrazí které kurzor závisí na tom, zda <xref:System.Windows.Controls.TextBox> nebo kruhu zdroje operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-214">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>  
  
 <span data-ttu-id="ca0d2-215">Nastavení <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost `true` a zpracování vynechaných dat je všechno, co je potřeba povolit element jako cíle přetažení.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-215">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="ca0d2-216">Však zajistit lepší uživatelské prostředí, můžete také zpracovávat <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, a <xref:System.Windows.UIElement.DragOver> události.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-216">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="ca0d2-217">V těchto událostí můžete provést kontroly a poskytnout další zpětnou vazbu pro uživatele předtím, než je vyřazeno data.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-217">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>  
  
 <span data-ttu-id="ca0d2-218">Při přetažení dat nad kruh uživatelského ovládacího prvku, oznámí ovládacího prvku zdroje operace přetažení jestli může zpracovat data, která je právě přetáhli.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-218">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="ca0d2-219">Pokud ovládací prvek nebude vědět, jak zpracování dat, by měl odmítnout rozevíracího.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-219">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="ca0d2-220">K tomuto účelu bude zpracovávat <xref:System.Windows.UIElement.DragOver> událostí a sadu <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-220">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="ca0d2-221">Chcete-li ověřit, že data vyřadit je povoleno</span><span class="sxs-lookup"><span data-stu-id="ca0d2-221">To verify that the data drop is allowed</span></span>  
  
1.  <span data-ttu-id="ca0d2-222">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-222">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="ca0d2-223">Přidejte následující <xref:System.Windows.UIElement.OnDragOver%2A> přepsání zajistit třída zpracování <xref:System.Windows.UIElement.DragOver> událostí.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-223">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     <span data-ttu-id="ca0d2-224">To <xref:System.Windows.UIElement.OnDragOver%2A> přepsání provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="ca0d2-224">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="ca0d2-225">Nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.None>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-225">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>  
  
    -   <span data-ttu-id="ca0d2-226">Provede stejnou kontroly, které se provádějí v <xref:System.Windows.UIElement.OnDrop%2A> metoda k určení, zda uživatelský ovládací prvek kruh může zpracovat taženou data.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-226">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>  
  
    -   <span data-ttu-id="ca0d2-227">Pokud uživatelského ovládacího prvku může zpracovat data, nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Copy> nebo <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-227">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="ca0d2-228">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-228">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="ca0d2-229">Vyberte text `gre` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-229">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="ca0d2-230">Přetáhněte text do ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-230">Drag the text to a Circle control.</span></span> <span data-ttu-id="ca0d2-231">Všimněte si, že kurzor nyní změny znamenat, že rozevírací není povolená, protože `gre` není platnou barvu.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-231">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>  
  
 <span data-ttu-id="ca0d2-232">Činnost koncového uživatele můžete dále vylepšit použitím náhled operace vyřazení.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-232">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="ca0d2-233">Pro uživatelský ovládací prvek kruh se přepíše <xref:System.Windows.UIElement.OnDragEnter%2A> a <xref:System.Windows.UIElement.OnDragLeave%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-233">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="ca0d2-234">Když je přetáhnout data přes ovládací prvek na aktuální pozadí <xref:System.Windows.Shapes.Shape.Fill%2A> je uložené v proměnné zástupný symbol.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-234">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="ca0d2-235">Řetězec je pak převést na štětce a použít <xref:System.Windows.Shapes.Ellipse> na kruh, který poskytuje uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-235">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="ca0d2-236">Pokud data ocitne mimo kruhu bez vyřazována původní <xref:System.Windows.Shapes.Shape.Fill%2A> kruhu je znovu použita hodnota.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-236">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="ca0d2-237">Zobrazte náhled důsledky operaci přetažení myší</span><span class="sxs-lookup"><span data-stu-id="ca0d2-237">To preview the effects of the drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="ca0d2-238">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-238">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="ca0d2-239">Ve třídě kruh deklarovat privátního <xref:System.Windows.Media.Brush> proměnné s názvem `_previousFill` a inicializujte ho, aby `null`.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-239">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  <span data-ttu-id="ca0d2-240">Přidejte následující <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání zajistit třída zpracování <xref:System.Windows.UIElement.DragEnter> událostí.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-240">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     <span data-ttu-id="ca0d2-241">To <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="ca0d2-241">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="ca0d2-242">Uloží <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost <xref:System.Windows.Shapes.Ellipse> v `_previousFill` proměnné.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-242">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>  
  
    -   <span data-ttu-id="ca0d2-243">Provede stejnou kontroly, které se provádějí v <xref:System.Windows.UIElement.OnDrop%2A> metoda k určení, zda lze převést data na <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-243">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="ca0d2-244">Pokud data jsou převedeny na platnou <xref:System.Windows.Media.Brush>, použije ji k <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-244">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
4.  <span data-ttu-id="ca0d2-245">Přidejte následující <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání zajistit třída zpracování <xref:System.Windows.UIElement.DragLeave> událostí.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-245">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     <span data-ttu-id="ca0d2-246">To <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="ca0d2-246">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="ca0d2-247">Platí <xref:System.Windows.Media.Brush> uloženy ve `_previousFill` proměnnou <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> , který poskytuje uživatelské rozhraní kruh uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-247">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>  
  
5.  <span data-ttu-id="ca0d2-248">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-248">Press F5 to build and run the application.</span></span>  
  
6.  <span data-ttu-id="ca0d2-249">Vyberte text `green` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-249">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="ca0d2-250">Přetáhněte text přes ovládacího prvku kruh bez vyřadíte.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-250">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="ca0d2-251">Kruhu změní z blue zeleně.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-251">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="ca0d2-252">![Náhled důsledky přetáhněte & č. 45; a & č. 45; operace odstranění](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="ca0d2-252">![Preview the effects of a drag&#45;and&#45;drop operation](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>  
  
8.  <span data-ttu-id="ca0d2-253">Přetáhněte text z ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-253">Drag the text away from the Circle control.</span></span> <span data-ttu-id="ca0d2-254">Kruhu změní z zelená zpět na modrou.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-254">The Circle changes from green back to blue.</span></span>  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a><span data-ttu-id="ca0d2-255">Povolení panelu přijímat vyřadit dat</span><span class="sxs-lookup"><span data-stu-id="ca0d2-255">Enabling a Panel to Receive Dropped Data</span></span>  
 <span data-ttu-id="ca0d2-256">V této části povolíte panely, které jsou hostiteli uživatelské ovládací prvky kruh tak, aby fungoval jako cílů přemístění dat taženou kruh.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-256">In this section, you will enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="ca0d2-257">Budete implementovat kód, který umožňuje přesunout kruh z jednoho panelu, nebo vytvořit kopii ovládacího prvku kruh a podržte stisknutou klávesu CTRL a přetahování kruh.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-257">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the CTRL key while dragging and dropping a Circle.</span></span>  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a><span data-ttu-id="ca0d2-258">Chcete-li povolit panelu jako cíle přetažení</span><span class="sxs-lookup"><span data-stu-id="ca0d2-258">To enable the panel to be a drop target</span></span>  
  
1.  <span data-ttu-id="ca0d2-259">Otevřete MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-259">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="ca0d2-260">Jak je znázorněno v následujícím XAML, v každém <xref:System.Windows.Controls.StackPanel> přidejte obslužné rutiny pro ovládací prvky, <xref:System.Windows.UIElement.DragOver> a <xref:System.Windows.UIElement.Drop> události.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-260">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="ca0d2-261">Název <xref:System.Windows.UIElement.DragOver> obslužné rutiny události, `panel_DragOver`a název <xref:System.Windows.UIElement.Drop> obslužné rutiny události, `panel_Drop`.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-261">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  <span data-ttu-id="ca0d2-262">Otevřete MainWindows.xaml.cs nebo MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-262">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>  
  
4.  <span data-ttu-id="ca0d2-263">Přidejte následující kód pro <xref:System.Windows.UIElement.DragOver> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-263">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     <span data-ttu-id="ca0d2-264">To <xref:System.Windows.UIElement.DragOver> obslužné rutiny události provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="ca0d2-264">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="ca0d2-265">Ověří, že taženou datové pole obsahuje "Objekt" data, která byla součástí <xref:System.Windows.DataObject> řízení uživatelských kruh a předána volání <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-265">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>  
  
    -   <span data-ttu-id="ca0d2-266">Pokud se nachází data "Objekt", zkontroluje, zda po stisknutí klávesy CTRL.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-266">If the "Object" data is present, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="ca0d2-267">Pokud po stisknutí klávesy CTRL, nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Copy>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-267">If the CTRL key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="ca0d2-268">Jinak hodnota nastavená <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-268">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
5.  <span data-ttu-id="ca0d2-269">Přidejte následující kód pro <xref:System.Windows.UIElement.Drop> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-269">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     <span data-ttu-id="ca0d2-270">To <xref:System.Windows.UIElement.Drop> obslužné rutiny události provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="ca0d2-270">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="ca0d2-271">Kontroluje, zda <xref:System.Windows.UIElement.Drop> událost již byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-271">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="ca0d2-272">Pro instanci, která kruhu ztracené kruh na jiném obslužné rutiny <xref:System.Windows.UIElement.Drop> událostí, nechcete, aby panelu obsahující kruhu také ji zpracovat.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-272">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>  
  
    -   <span data-ttu-id="ca0d2-273">Pokud <xref:System.Windows.UIElement.Drop> událost není zpracována, kontroly zda stisknutí klávesy CTRL.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-273">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="ca0d2-274">Pokud při stisknutí klávesy CTRL <xref:System.Windows.UIElement.Drop> se stane, díky kopii kruhu řízení a přidejte ho do <xref:System.Windows.Controls.Panel.Children%2A> kolekce <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-274">If the CTRL key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
    -   <span data-ttu-id="ca0d2-275">Pokud není stisknuta klávesa CTRL, se přesune na kruh z <xref:System.Windows.Controls.Panel.Children%2A> kolekce jeho nadřazeného panelu <xref:System.Windows.Controls.Panel.Children%2A> kolekce panelu, která byla vynechána na.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-275">If the CTRL key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>  
  
    -   <span data-ttu-id="ca0d2-276">Nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost upozornit <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda jestli se provedlo operace přesunutí nebo zkopírování.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-276">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>  
  
6.  <span data-ttu-id="ca0d2-277">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-277">Press F5 to build and run the application.</span></span>  
  
7.  <span data-ttu-id="ca0d2-278">Vyberte text `green` z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-278">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="ca0d2-279">Přetáhněte text přes ovládacího prvku kruh a umístěte jej.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-279">Drag the text over a Circle control and drop it.</span></span>  
  
9. <span data-ttu-id="ca0d2-280">Přetáhněte ovládací prvek kruh v levém panelu na pravém panelu a umístěte jej.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-280">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="ca0d2-281">Kruhu je odebrán z <xref:System.Windows.Controls.Panel.Children%2A> kolekce levém panelu a přidat do kolekce podřízených pravém panelu.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-281">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>  
  
10. <span data-ttu-id="ca0d2-282">Přetáhněte ovládací prvek kruh z panelu, který je v jiném panelu a umístěte jej při stisknete klávesu CTRL.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-282">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the CTRL key.</span></span> <span data-ttu-id="ca0d2-283">Se zkopíruje na kruh a o kopírování se přidá <xref:System.Windows.Controls.Panel.Children%2A> kolekce přijímající panelu.</span><span class="sxs-lookup"><span data-stu-id="ca0d2-283">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>  
  
     <span data-ttu-id="ca0d2-284">![Přetahování kruh stiskněte klávesu CTRL](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="ca0d2-284">![Dragging a Circle while pressing the CTRL key](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca0d2-285">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca0d2-285">See Also</span></span>  
 [<span data-ttu-id="ca0d2-286">Přetáhnout myší – přehled</span><span class="sxs-lookup"><span data-stu-id="ca0d2-286">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
