---
title: 'Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 7ca4987da8422c00e3fc34ff4605ddd13e4091b6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087642"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="89e82-102">Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku</span><span class="sxs-lookup"><span data-stu-id="89e82-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="89e82-103">Tento návod ukazuje, jak vytvořit vlastní uživatelský ovládací prvek, který se můžete podílet přenos dat a přetahování v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="89e82-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="89e82-104">V tomto návodu vytvoříte vlastní WPF <xref:System.Windows.Controls.UserControl> , která představuje kulaté.</span><span class="sxs-lookup"><span data-stu-id="89e82-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="89e82-105">Funkce provede na ovládacím prvku povolit přenos dat pomocí přetahování myší.</span><span class="sxs-lookup"><span data-stu-id="89e82-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="89e82-106">Například přetažením z jednoho ovládacího prvku kruh do jiného data Barva výplně je zkopírován ze zdroje kruh k cíli.</span><span class="sxs-lookup"><span data-stu-id="89e82-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="89e82-107">Přetažením z ovládacího prvku kruh k <xref:System.Windows.Controls.TextBox>, řetězcová reprezentace barvu výplně se zkopíruje do <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="89e82-108">Také vytvoříte malou aplikaci, která obsahuje dva ovládací prvky panelu a <xref:System.Windows.Controls.TextBox> k testování funkcí a přetažení.</span><span class="sxs-lookup"><span data-stu-id="89e82-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="89e82-109">Budete psát kód, který umožňuje panelů ke zpracování vynechaných kruh dat, která vám umožní se přesunout nebo kopírovat kruhy kolekci Children v panel jeden na druhý.</span><span class="sxs-lookup"><span data-stu-id="89e82-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="89e82-110">Tento návod znázorňuje následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e82-110">This walkthrough illustrates the following tasks:</span></span>

-   <span data-ttu-id="89e82-111">Vytvořte vlastní uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="89e82-111">Create a custom user control.</span></span>

-   <span data-ttu-id="89e82-112">Povolení nástroje Řízení uživatelských jako zdroj přetažení.</span><span class="sxs-lookup"><span data-stu-id="89e82-112">Enable the user control to be a drag source.</span></span>

-   <span data-ttu-id="89e82-113">Povolte uživatelský ovládací prvek jako cíl přetažení.</span><span class="sxs-lookup"><span data-stu-id="89e82-113">Enable the user control to be a drop target.</span></span>

-   <span data-ttu-id="89e82-114">Povolte panel přijímat data z uživatelského ovládacího prvku vyřadit.</span><span class="sxs-lookup"><span data-stu-id="89e82-114">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="89e82-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89e82-115">Prerequisites</span></span>

<span data-ttu-id="89e82-116">Visual Studio k dokončení tohoto návodu potřebujete.</span><span class="sxs-lookup"><span data-stu-id="89e82-116">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="89e82-117">Vytvoření projektu aplikace</span><span class="sxs-lookup"><span data-stu-id="89e82-117">Create the Application Project</span></span>
 <span data-ttu-id="89e82-118">V této části vytvoříte aplikační infrastruktury, který obsahuje hlavní stránka s dva panely a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-118">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1.  <span data-ttu-id="89e82-119">Vytvoření nového projektu aplikace WPF v jazyce Visual Basic nebo Visual C# s názvem `DragDropExample`.</span><span class="sxs-lookup"><span data-stu-id="89e82-119">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="89e82-120">Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="89e82-120">For more information, see [How to: Create a New WPF Application Project](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>

2.  <span data-ttu-id="89e82-121">Otevřete soubor MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="89e82-121">Open MainWindow.xaml.</span></span>

3.  <span data-ttu-id="89e82-122">Přidejte následující kód mezi otevírací a zavírací <xref:System.Windows.Controls.Grid> značky.</span><span class="sxs-lookup"><span data-stu-id="89e82-122">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="89e82-123">Tento kód vytvoří uživatelské rozhraní pro testovací aplikace.</span><span class="sxs-lookup"><span data-stu-id="89e82-123">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="89e82-124">Přidat nový uživatelský ovládací prvek do projektu</span><span class="sxs-lookup"><span data-stu-id="89e82-124">Add a New User Control to the Project</span></span>
 <span data-ttu-id="89e82-125">V této části přidáte nový uživatelský ovládací prvek do projektu.</span><span class="sxs-lookup"><span data-stu-id="89e82-125">In this section, you will add a new user control to the project.</span></span>

1.  <span data-ttu-id="89e82-126">V nabídce Projekt vyberte **přidat uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="89e82-126">On the Project menu, select **Add User Control**.</span></span>

2.  <span data-ttu-id="89e82-127">V **přidat novou položku** dialogové okno pole, změňte název na `Circle.xaml`a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="89e82-127">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="89e82-128">Circle.XAML a jeho použití modelu code-behind se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="89e82-128">Circle.xaml and its code-behind is added to the project.</span></span>

3.  <span data-ttu-id="89e82-129">Otevřete Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="89e82-129">Open Circle.xaml.</span></span>

     <span data-ttu-id="89e82-130">Tento soubor bude obsahovat prvky uživatelského rozhraní uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="89e82-130">This file will contain the user interface elements of the user control.</span></span>

4.  <span data-ttu-id="89e82-131">Přidejte následující kód do kořenového adresáře <xref:System.Windows.Controls.Grid> k vytvoření jednoduché uživatelský ovládací prvek, který má kruh jako jeho uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="89e82-131">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5.  <span data-ttu-id="89e82-132">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e82-132">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6.  <span data-ttu-id="89e82-133">V jazyce C# přidejte následující kód za výchozí konstruktor pro vytvoření kopie konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="89e82-133">In C#, add the following code after the default constructor to create a copy constructor.</span></span> <span data-ttu-id="89e82-134">V jazyce Visual Basic přidejte následující kód k vytvoření výchozí konstruktor a kopírovací konstruktor.</span><span class="sxs-lookup"><span data-stu-id="89e82-134">In Visual Basic, add the following code to create both a default constructor and a copy constructor.</span></span>

     <span data-ttu-id="89e82-135">Aby bylo možné povolit uživatelského ovládacího prvku, které se mají zkopírovat, přidejte metodu konstruktoru kopie v souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="89e82-135">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="89e82-136">Ve zjednodušené kruh uživatelského ovládacího prvku, bude pouze zkopírujte výplně a velikost uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="89e82-136">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="89e82-137">Přidat uživatelský ovládací prvek do hlavního okna</span><span class="sxs-lookup"><span data-stu-id="89e82-137">Add the user control to the main window</span></span>

1.  <span data-ttu-id="89e82-138">Otevřete soubor MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="89e82-138">Open MainWindow.xaml.</span></span>

2.  <span data-ttu-id="89e82-139">Přidejte následující XAML do otevíracího <xref:System.Windows.Window> značku k vytvoření oboru názvů XML odkaz na aktuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="89e82-139">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```
    xmlns:local="clr-namespace:DragDropExample"
    ```

3.  <span data-ttu-id="89e82-140">V prvním <xref:System.Windows.Controls.StackPanel>, přidejte následující XAML vytvořit dvě instance kruh uživatelského ovládacího prvku na panelu první.</span><span class="sxs-lookup"><span data-stu-id="89e82-140">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="89e82-141">Úplné XAML pro panel vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="89e82-141">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="89e82-142">Implementace zdroje událostí přetáhněte do uživatelského ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="89e82-142">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="89e82-143">V této části se přepíšou <xref:System.Windows.UIElement.OnMouseMove%2A> metoda a zahájení operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="89e82-143">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="89e82-144">Pokud je spuštěn přetáhněte (stisknutí tlačítka myši a přesunut ukazatel myši), bude balíček data, která mají být převedeny do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="89e82-144">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="89e82-145">V takovém případě bude ovládací prvek kruh balíček tři položky data; řetězcová reprezentace jeho barva výplně, dvojité vyjádření výšku a zkopírujte sebe sama.</span><span class="sxs-lookup"><span data-stu-id="89e82-145">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="89e82-146">K zahájení operace přetažení myší</span><span class="sxs-lookup"><span data-stu-id="89e82-146">To initiate a drag-and-drop operation</span></span>

1.  <span data-ttu-id="89e82-147">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e82-147">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2.  <span data-ttu-id="89e82-148">Přidejte následující <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.MouseMove> událostí.</span><span class="sxs-lookup"><span data-stu-id="89e82-148">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="89e82-149">To <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e82-149">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="89e82-150">Kontroluje, zda se stiskne tlačítko levé tlačítko myši, zatímco ukazatel myši pohybuje.</span><span class="sxs-lookup"><span data-stu-id="89e82-150">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    -   <span data-ttu-id="89e82-151">Balíčky kruh dat do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="89e82-151">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="89e82-152">V tomto případě ovládací prvek kruh balíčky tři položky data; řetězcová reprezentace jeho barva výplně, dvojité vyjádření výšku a zkopírujte sebe sama.</span><span class="sxs-lookup"><span data-stu-id="89e82-152">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    -   <span data-ttu-id="89e82-153">Volání statické <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metoda k zahájení operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="89e82-153">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="89e82-154">Následující tři parametry předáváte <xref:System.Windows.DragDrop.DoDragDrop%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="89e82-154">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        -   <span data-ttu-id="89e82-155">`dragSource` – Odkaz na tento ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="89e82-155">`dragSource` – A reference to this control.</span></span>

        -   <span data-ttu-id="89e82-156">`data` – Tím <xref:System.Windows.DataObject> vytvořili v předchozím kódu.</span><span class="sxs-lookup"><span data-stu-id="89e82-156">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        -   <span data-ttu-id="89e82-157">`allowedEffects` – Povolené operace přetažení myší, které jsou <xref:System.Windows.DragDropEffects.Copy> nebo <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="89e82-157">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3.  <span data-ttu-id="89e82-158">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89e82-158">Press **F5** to build and run the application.</span></span>

4.  <span data-ttu-id="89e82-159">Klikněte na jednu z ovládacích prvků kruh a přetáhněte ho na panely na kruh a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-159">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="89e82-160">Při přetažení přes <xref:System.Windows.Controls.TextBox>, změní se kurzor na udávajících přesun.</span><span class="sxs-lookup"><span data-stu-id="89e82-160">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5.  <span data-ttu-id="89e82-161">Při přetažení kruh přes <xref:System.Windows.Controls.TextBox>, stiskněte **Ctrl** klíč.</span><span class="sxs-lookup"><span data-stu-id="89e82-161">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="89e82-162">Všimněte si, jak kurzoru se změní jeho kopii.</span><span class="sxs-lookup"><span data-stu-id="89e82-162">Notice how the cursor changes to indicate a copy.</span></span>

6.  <span data-ttu-id="89e82-163">Přetáhnout myší kruhu na <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-163">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="89e82-164">Řetězcová reprezentace barvu kruhu se připojí <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-164">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="89e82-165">![Řetězcové vyjádření barvu kruhu](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="89e82-165">![String representation of Circle's fill color](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="89e82-166">Ve výchozím nastavení se kurzor změní během operace přetažení myší označíte, jaký vliv má vyřazení dat bude mít.</span><span class="sxs-lookup"><span data-stu-id="89e82-166">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="89e82-167">Můžete přizpůsobit poskytnutou zpětnou vazbu pro uživatele pomocí manipulace <xref:System.Windows.UIElement.GiveFeedback> událostí a nastavení různých kurzoru.</span><span class="sxs-lookup"><span data-stu-id="89e82-167">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="89e82-168">Váš názor na uživatele</span><span class="sxs-lookup"><span data-stu-id="89e82-168">Give feedback to the user</span></span>

1.  <span data-ttu-id="89e82-169">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e82-169">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2.  <span data-ttu-id="89e82-170">Přidejte následující <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.GiveFeedback> událostí.</span><span class="sxs-lookup"><span data-stu-id="89e82-170">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="89e82-171">To <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e82-171">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="89e82-172">Kontroluje <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> hodnoty nastavené v cíl přetažení <xref:System.Windows.UIElement.DragOver> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="89e82-172">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    -   <span data-ttu-id="89e82-173">Nastaví vlastní kurzor na základě <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="89e82-173">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="89e82-174">Kurzor má předat uživateli o jaký vliv má vyřadit data budou mít vizuální zpětnou vazbu.</span><span class="sxs-lookup"><span data-stu-id="89e82-174">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3.  <span data-ttu-id="89e82-175">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89e82-175">Press **F5** to build and run the application.</span></span>

4.  <span data-ttu-id="89e82-176">Přetáhněte jednu kruhu určuje přes panelů na kruh a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-176">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="89e82-177">Všimněte si, že kurzory teď vlastní ukazatele, které jste zadali <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsat.</span><span class="sxs-lookup"><span data-stu-id="89e82-177">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="89e82-178">![Přetáhnout myší s vlastní ukazatele](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="89e82-178">![Drag and drop with custom cursors](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5.  <span data-ttu-id="89e82-179">Vyberte text `green` z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-179">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6.  <span data-ttu-id="89e82-180">Přetáhněte `green` text do ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="89e82-180">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="89e82-181">Všimněte si, že jsou zobrazeny kurzory výchozí udávajících účinky operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="89e82-181">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="89e82-182">Kurzor zpětná vazba je vždycky nastavený zdroj přetažení.</span><span class="sxs-lookup"><span data-stu-id="89e82-182">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="89e82-183">Implementace událostí cíl přetažení do uživatelského ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="89e82-183">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="89e82-184">V této části určíte, že uživatelský ovládací prvek je cíl přetažení, přepsání metody, které umožňují uživateli ovládací prvek jako cíl přetažení a zpracovávat data, která je na něm vyřadit.</span><span class="sxs-lookup"><span data-stu-id="89e82-184">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="89e82-185">Chcete-li povolit uživatelský ovládací prvek jako cíl přetažení</span><span class="sxs-lookup"><span data-stu-id="89e82-185">To enable the user control to be a drop target</span></span>

1.  <span data-ttu-id="89e82-186">Otevřete Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="89e82-186">Open Circle.xaml.</span></span>

2.  <span data-ttu-id="89e82-187">Při otevírání <xref:System.Windows.Controls.UserControl> značky, přidejte <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost a nastavte ho na `true`.</span><span class="sxs-lookup"><span data-stu-id="89e82-187">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="89e82-188"><xref:System.Windows.UIElement.OnDrop%2A> Metoda je volána, když <xref:System.Windows.UIElement.AllowDrop%2A> je nastavena na `true` a data ze zdroje přetáhněte přesunuta uživatelský ovládací prvek kruh.</span><span class="sxs-lookup"><span data-stu-id="89e82-188">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="89e82-189">V této metodě budou zpracovávat data, která byla zahozena a použít data kruhu.</span><span class="sxs-lookup"><span data-stu-id="89e82-189">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="89e82-190">Ke zpracování vynechaných dat</span><span class="sxs-lookup"><span data-stu-id="89e82-190">To process the dropped data</span></span>

1.  <span data-ttu-id="89e82-191">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e82-191">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2.  <span data-ttu-id="89e82-192">Přidejte následující <xref:System.Windows.UIElement.OnDrop%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.Drop> událostí.</span><span class="sxs-lookup"><span data-stu-id="89e82-192">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="89e82-193">To <xref:System.Windows.UIElement.OnDrop%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e82-193">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="89e82-194">Používá <xref:System.Windows.DataObject.GetDataPresent%2A> metodu ke kontrole, pokud Přetahované dat obsahuje objekt řetězce.</span><span class="sxs-lookup"><span data-stu-id="89e82-194">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    -   <span data-ttu-id="89e82-195">Používá <xref:System.Windows.DataObject.GetData%2A> metody se extrahují data řetězce, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="89e82-195">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    -   <span data-ttu-id="89e82-196">Používá <xref:System.Windows.Media.BrushConverter> pokusí převést řetězec, který má <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="89e82-196">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    -   <span data-ttu-id="89e82-197">Pokud převod je úspěšný, štětce, který se vztahuje <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> , který poskytuje uživatelské rozhraní ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="89e82-197">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    -   <span data-ttu-id="89e82-198">Značky <xref:System.Windows.UIElement.Drop> události jako zpracování.</span><span class="sxs-lookup"><span data-stu-id="89e82-198">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="89e82-199">Událost přetažení by měla označit jako ošetřenou, takže další prvky, které se zobrazí tato událost vědět, že uživatelský ovládací prvek kruh zpracovává ji.</span><span class="sxs-lookup"><span data-stu-id="89e82-199">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3.  <span data-ttu-id="89e82-200">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89e82-200">Press **F5** to build and run the application.</span></span>

4.  <span data-ttu-id="89e82-201">Vyberte text `green` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-201">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5.  <span data-ttu-id="89e82-202">Text do ovládacího prvku kruh přetáhnout.</span><span class="sxs-lookup"><span data-stu-id="89e82-202">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="89e82-203">Kruh se změní z modrá na zelenou.</span><span class="sxs-lookup"><span data-stu-id="89e82-203">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="89e82-204">![Převod řetězce na stopu](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="89e82-204">![Convert a string to a brush](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6.  <span data-ttu-id="89e82-205">Zadejte text `green` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-205">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7.  <span data-ttu-id="89e82-206">Vyberte text `gre` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-206">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8.  <span data-ttu-id="89e82-207">Přetáhněte do ovládacího prvku kruhu a umístěte jej.</span><span class="sxs-lookup"><span data-stu-id="89e82-207">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="89e82-208">Všimněte si, že se ukazatel změní na ukazují, že rozevírací je povoleno, ale barvu kruhu se nemění, protože `gre` není platná barva.</span><span class="sxs-lookup"><span data-stu-id="89e82-208">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="89e82-209">Z ovládacího prvku zelený kroužek přetažením na ovládacím prvku modré kruh.</span><span class="sxs-lookup"><span data-stu-id="89e82-209">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="89e82-210">Kruh se změní z modrá na zelenou.</span><span class="sxs-lookup"><span data-stu-id="89e82-210">The Circle changes from blue to green.</span></span> <span data-ttu-id="89e82-211">Všimněte si, že se zobrazí kurzor, který závisí na tom, zda <xref:System.Windows.Controls.TextBox> nebo kruhu je zdroji přetažení.</span><span class="sxs-lookup"><span data-stu-id="89e82-211">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="89e82-212">Nastavení <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost `true` a zpracování dat vynechaných je vše, co je potřeba povolit element, který má být cíl přetažení.</span><span class="sxs-lookup"><span data-stu-id="89e82-212">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="89e82-213">Však zajistit lepší výkon, můžete také pracovat <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, a <xref:System.Windows.UIElement.DragOver> události.</span><span class="sxs-lookup"><span data-stu-id="89e82-213">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="89e82-214">V těchto událostí můžete provést kontroly a zadejte víc uživateli předtím, než se ukončí data.</span><span class="sxs-lookup"><span data-stu-id="89e82-214">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="89e82-215">Když data je přetažený na ovládací prvek uživatele kruh, ovládací prvek by měl oznámení zdroji přetažení, zda může zpracovat data, která je právě přetáhli.</span><span class="sxs-lookup"><span data-stu-id="89e82-215">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="89e82-216">Pokud ovládací prvek není známo, jak ke zpracování dat, by měl odmítnout rozevírací nabídku.</span><span class="sxs-lookup"><span data-stu-id="89e82-216">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="89e82-217">K tomuto účelu bude zpracovávat <xref:System.Windows.UIElement.DragOver> událostí a nastavte <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="89e82-217">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="89e82-218">Chcete-li ověřit, že rozevírací dat není povolené</span><span class="sxs-lookup"><span data-stu-id="89e82-218">To verify that the data drop is allowed</span></span>

1.  <span data-ttu-id="89e82-219">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e82-219">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2.  <span data-ttu-id="89e82-220">Přidejte následující <xref:System.Windows.UIElement.OnDragOver%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.DragOver> událostí.</span><span class="sxs-lookup"><span data-stu-id="89e82-220">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="89e82-221">To <xref:System.Windows.UIElement.OnDragOver%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e82-221">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="89e82-222">Nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.None>.</span><span class="sxs-lookup"><span data-stu-id="89e82-222">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    -   <span data-ttu-id="89e82-223">Provádí stejné kontroly, které se provádí v <xref:System.Windows.UIElement.OnDrop%2A> metodou ke zjištění, zda uživatelský ovládací prvek kruh může zpracovávat Přetahované data.</span><span class="sxs-lookup"><span data-stu-id="89e82-223">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    -   <span data-ttu-id="89e82-224">Pokud uživatelský ovládací prvek můžete zpracovávat data, nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Copy> nebo <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="89e82-224">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3.  <span data-ttu-id="89e82-225">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89e82-225">Press **F5** to build and run the application.</span></span>

4.  <span data-ttu-id="89e82-226">Vyberte text `gre` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-226">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5.  <span data-ttu-id="89e82-227">Přetáhněte text do ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="89e82-227">Drag the text to a Circle control.</span></span> <span data-ttu-id="89e82-228">Všimněte si, že se kurzor změní teď označuje, že rozevírací není povolená, protože `gre` není platná barva.</span><span class="sxs-lookup"><span data-stu-id="89e82-228">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="89e82-229">Můžete dále vylepšit uživatelské prostředí s použitím operace přetažení ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="89e82-229">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="89e82-230">Pro uživatelský ovládací prvek kruh, přepíše <xref:System.Windows.UIElement.OnDragEnter%2A> a <xref:System.Windows.UIElement.OnDragLeave%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="89e82-230">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="89e82-231">Když jsou data přetažený na ovládací prvek, aktuální pozadí <xref:System.Windows.Shapes.Shape.Fill%2A> je uložen v proměnné zástupný symbol.</span><span class="sxs-lookup"><span data-stu-id="89e82-231">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="89e82-232">Pak převedena na štětce a použít na řetězec <xref:System.Windows.Shapes.Ellipse> kruhu, která poskytuje uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="89e82-232">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="89e82-233">Pokud data ocitne mimo kruh bez probíhá vyřazování původní <xref:System.Windows.Shapes.Shape.Fill%2A> hodnota je znovu použita v kruhu.</span><span class="sxs-lookup"><span data-stu-id="89e82-233">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="89e82-234">Náhled účinky operace přetažení myší</span><span class="sxs-lookup"><span data-stu-id="89e82-234">To preview the effects of the drag-and-drop operation</span></span>

1.  <span data-ttu-id="89e82-235">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e82-235">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2.  <span data-ttu-id="89e82-236">Ve třídě kruh deklarovat soukromé <xref:System.Windows.Media.Brush> proměnnou s názvem `_previousFill` a inicializujte ji na `null`.</span><span class="sxs-lookup"><span data-stu-id="89e82-236">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3.  <span data-ttu-id="89e82-237">Přidejte následující <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.DragEnter> událostí.</span><span class="sxs-lookup"><span data-stu-id="89e82-237">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="89e82-238">To <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e82-238">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="89e82-239">Uloží <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost <xref:System.Windows.Shapes.Ellipse> v `_previousFill` proměnné.</span><span class="sxs-lookup"><span data-stu-id="89e82-239">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    -   <span data-ttu-id="89e82-240">Provádí stejné kontroly, které se provádí v <xref:System.Windows.UIElement.OnDrop%2A> metodou ke zjištění, zda data lze převést na <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="89e82-240">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    -   <span data-ttu-id="89e82-241">Pokud data je převést na platnou <xref:System.Windows.Media.Brush>, použije ho k <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="89e82-241">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4.  <span data-ttu-id="89e82-242">Přidejte následující <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.DragLeave> událostí.</span><span class="sxs-lookup"><span data-stu-id="89e82-242">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="89e82-243">To <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e82-243">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    -   <span data-ttu-id="89e82-244">Se vztahuje <xref:System.Windows.Media.Brush> uložené v `_previousFill` proměnnou <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> , který poskytuje uživatelské rozhraní uživatelského ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="89e82-244">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5.  <span data-ttu-id="89e82-245">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89e82-245">Press **F5** to build and run the application.</span></span>

6.  <span data-ttu-id="89e82-246">Vyberte text `green` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-246">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7.  <span data-ttu-id="89e82-247">Přetáhněte text myší na ovládací prvek kruh bez zastaví.</span><span class="sxs-lookup"><span data-stu-id="89e82-247">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="89e82-248">Kruh se změní z modrá na zelenou.</span><span class="sxs-lookup"><span data-stu-id="89e82-248">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="89e82-249">![Ve verzi Preview efekty přetáhněte&#45;a&#45;operace odstranění](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="89e82-249">![Preview the effects of a drag&#45;and&#45;drop operation](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8.  <span data-ttu-id="89e82-250">Přetáhněte text z ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="89e82-250">Drag the text away from the Circle control.</span></span> <span data-ttu-id="89e82-251">Kruh se změní z zelené zpět na modrou.</span><span class="sxs-lookup"><span data-stu-id="89e82-251">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="89e82-252">Povolit Panel přijímat vynechaných Data</span><span class="sxs-lookup"><span data-stu-id="89e82-252">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="89e82-253">V této části povolíte panely, které jsou hostiteli uživatelské ovládací prvky kruh tak, aby fungoval jako cíle přetažení pro Přetahované data kruh.</span><span class="sxs-lookup"><span data-stu-id="89e82-253">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="89e82-254">Budete implementovat kód, který umožňuje přesunout kruh z jednoho panelu na jiný nebo vytvořit kopii ovládacího prvku kruh současným **Ctrl** klíče při přetahování kruh.</span><span class="sxs-lookup"><span data-stu-id="89e82-254">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1.  <span data-ttu-id="89e82-255">Otevřete soubor MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="89e82-255">Open MainWindow.xaml.</span></span>

2.  <span data-ttu-id="89e82-256">Jak je znázorněno v následující XAML v každém <xref:System.Windows.Controls.StackPanel> přidat obslužné rutiny pro ovládací prvky, <xref:System.Windows.UIElement.DragOver> a <xref:System.Windows.UIElement.Drop> události.</span><span class="sxs-lookup"><span data-stu-id="89e82-256">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="89e82-257">Název <xref:System.Windows.UIElement.DragOver> obslužná rutina události `panel_DragOver`a pojmenujte <xref:System.Windows.UIElement.Drop> obslužná rutina události, `panel_Drop`.</span><span class="sxs-lookup"><span data-stu-id="89e82-257">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3.  <span data-ttu-id="89e82-258">Otevřete MainWindows.xaml.cs nebo soubor MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e82-258">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4.  <span data-ttu-id="89e82-259">Přidejte následující kód <xref:System.Windows.UIElement.DragOver> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="89e82-259">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="89e82-260">To <xref:System.Windows.UIElement.DragOver> obslužná rutina události provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e82-260">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    -   <span data-ttu-id="89e82-261">Kontroluje, že Přetahované data obsahují data "Object", který byl zabalen do <xref:System.Windows.DataObject> v uživatelském ovládacím prvku kruhu a předat ve volání do <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span><span class="sxs-lookup"><span data-stu-id="89e82-261">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    -   <span data-ttu-id="89e82-262">Pokud jsou data "Objekt" k dispozici, zkontroluje, jestli **Ctrl** stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="89e82-262">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    -   <span data-ttu-id="89e82-263">Pokud **Ctrl** se stiskne klávesa, nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Copy>.</span><span class="sxs-lookup"><span data-stu-id="89e82-263">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="89e82-264">V opačném případě nastavte <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="89e82-264">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5.  <span data-ttu-id="89e82-265">Přidejte následující kód <xref:System.Windows.UIElement.Drop> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="89e82-265">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="89e82-266">To <xref:System.Windows.UIElement.Drop> obslužná rutina události provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e82-266">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    -   <span data-ttu-id="89e82-267">Kontroluje, zda <xref:System.Windows.UIElement.Drop> události již byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="89e82-267">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="89e82-268">Pro instanci, která kroužek ztracené kruhu na jiném obslužné rutiny <xref:System.Windows.UIElement.Drop> události, nechcete, aby panelu, který obsahuje kruhu také ji zpracovat.</span><span class="sxs-lookup"><span data-stu-id="89e82-268">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    -   <span data-ttu-id="89e82-269">Pokud <xref:System.Windows.UIElement.Drop> událostí není zpracována, zkontroluje, jestli **Ctrl** stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="89e82-269">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    -   <span data-ttu-id="89e82-270">Pokud **Ctrl** při stisknutí klávesy <xref:System.Windows.UIElement.Drop> se stane, vytvoří kopii kruhu ovládací prvek a přidat ji do <xref:System.Windows.Controls.Panel.Children%2A> kolekce <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="89e82-270">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    -   <span data-ttu-id="89e82-271">Pokud **Ctrl** není stisknuta klávesa, přesune kruh z <xref:System.Windows.Controls.Panel.Children%2A> kolekce jeho nadřazeného panelu <xref:System.Windows.Controls.Panel.Children%2A> kolekce, která byla vynechána na panelu.</span><span class="sxs-lookup"><span data-stu-id="89e82-271">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    -   <span data-ttu-id="89e82-272">Sady <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost upozornit <xref:System.Windows.DragDrop.DoDragDrop%2A> metody Určuje, zda byla provedena operace přesunutí nebo kopírování.</span><span class="sxs-lookup"><span data-stu-id="89e82-272">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6.  <span data-ttu-id="89e82-273">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89e82-273">Press **F5** to build and run the application.</span></span>

7.  <span data-ttu-id="89e82-274">Vyberte text `green` z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e82-274">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8.  <span data-ttu-id="89e82-275">Přetáhněte myší na ovládací prvek kruh text a umístěte jej.</span><span class="sxs-lookup"><span data-stu-id="89e82-275">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="89e82-276">Přetáhněte ovládací prvek kruhu na levém panelu na pravém panelu a umístěte ho.</span><span class="sxs-lookup"><span data-stu-id="89e82-276">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="89e82-277">Kruh se odebere z <xref:System.Windows.Controls.Panel.Children%2A> kolekce na levém panelu a přidat do podřízené kolekce pravého panelu.</span><span class="sxs-lookup"><span data-stu-id="89e82-277">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="89e82-278">Přetáhněte ovládací prvek kruh z panelu je v jiné panel a umístěte jej při stisknutí **Ctrl** klíč.</span><span class="sxs-lookup"><span data-stu-id="89e82-278">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="89e82-279">Kruh se zkopíruje a kopie je přidána do <xref:System.Windows.Controls.Panel.Children%2A> kolekce přijímající panelu.</span><span class="sxs-lookup"><span data-stu-id="89e82-279">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="89e82-280">![Přetažení kruh při stisknutí klávesy CTRL](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="89e82-280">![Dragging a Circle while pressing the CTRL key](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="89e82-281">Viz také</span><span class="sxs-lookup"><span data-stu-id="89e82-281">See Also</span></span>

- [<span data-ttu-id="89e82-282">Přehled přetažení</span><span class="sxs-lookup"><span data-stu-id="89e82-282">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)