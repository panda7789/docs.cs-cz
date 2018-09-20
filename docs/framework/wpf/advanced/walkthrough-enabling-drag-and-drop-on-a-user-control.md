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
ms.openlocfilehash: e151eb7f428fecb330970210fd7addb1603a211f
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326618"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="89e03-102">Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku</span><span class="sxs-lookup"><span data-stu-id="89e03-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>
<span data-ttu-id="89e03-103">Tento návod ukazuje, jak vytvořit vlastní uživatelský ovládací prvek, který se můžete podílet přenos dat a přetahování v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="89e03-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="89e03-104">V tomto návodu vytvoříte vlastní WPF <xref:System.Windows.Controls.UserControl> , která představuje kulaté.</span><span class="sxs-lookup"><span data-stu-id="89e03-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="89e03-105">Funkce provede na ovládacím prvku povolit přenos dat pomocí přetahování myší.</span><span class="sxs-lookup"><span data-stu-id="89e03-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="89e03-106">Například přetažením z jednoho ovládacího prvku kruh do jiného data Barva výplně je zkopírován ze zdroje kruh k cíli.</span><span class="sxs-lookup"><span data-stu-id="89e03-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="89e03-107">Přetažením z ovládacího prvku kruh k <xref:System.Windows.Controls.TextBox>, řetězcová reprezentace barvu výplně se zkopíruje do <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="89e03-108">Také vytvoříte malou aplikaci, která obsahuje dva ovládací prvky panelu a <xref:System.Windows.Controls.TextBox> k testování funkcí a přetažení.</span><span class="sxs-lookup"><span data-stu-id="89e03-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="89e03-109">Budete psát kód, který umožňuje panelů ke zpracování vynechaných kruh dat, která vám umožní se přesunout nebo kopírovat kruhy kolekci Children v panel jeden na druhý.</span><span class="sxs-lookup"><span data-stu-id="89e03-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>  
  
 <span data-ttu-id="89e03-110">Tento návod znázorňuje následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e03-110">This walkthrough illustrates the following tasks:</span></span>  
  
-   <span data-ttu-id="89e03-111">Vytvořte vlastní uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="89e03-111">Create a custom user control.</span></span>  
  
-   <span data-ttu-id="89e03-112">Povolení nástroje Řízení uživatelských jako zdroj přetažení.</span><span class="sxs-lookup"><span data-stu-id="89e03-112">Enable the user control to be a drag source.</span></span>  
  
-   <span data-ttu-id="89e03-113">Povolte uživatelský ovládací prvek jako cíl přetažení.</span><span class="sxs-lookup"><span data-stu-id="89e03-113">Enable the user control to be a drop target.</span></span>  
  
-   <span data-ttu-id="89e03-114">Povolte panel přijímat data z uživatelského ovládacího prvku vyřadit.</span><span class="sxs-lookup"><span data-stu-id="89e03-114">Enable a panel to receive data dropped from the user control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="89e03-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89e03-115">Prerequisites</span></span>  
 <span data-ttu-id="89e03-116">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="89e03-116">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="89e03-117">Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="89e03-117">Visual Studio 2010</span></span>  
  
## <a name="creating-the-application-project"></a><span data-ttu-id="89e03-118">Vytvoření projektu aplikace</span><span class="sxs-lookup"><span data-stu-id="89e03-118">Creating the Application Project</span></span>  
 <span data-ttu-id="89e03-119">V této části vytvoříte aplikační infrastruktury, který obsahuje hlavní stránka s dva panely a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-119">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
### <a name="to-create-the-project"></a><span data-ttu-id="89e03-120">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="89e03-120">To create the project</span></span>  
  
1.  <span data-ttu-id="89e03-121">Vytvoření nového projektu aplikace WPF v jazyce Visual Basic nebo Visual C# s názvem `DragDropExample`.</span><span class="sxs-lookup"><span data-stu-id="89e03-121">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="89e03-122">Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="89e03-122">For more information, see [How to: Create a New WPF Application Project](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="89e03-123">Otevřete soubor MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="89e03-123">Open MainWindow.xaml.</span></span>  
  
3.  <span data-ttu-id="89e03-124">Přidejte následující kód mezi otevírací a zavírací <xref:System.Windows.Controls.Grid> značky.</span><span class="sxs-lookup"><span data-stu-id="89e03-124">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>  
  
     <span data-ttu-id="89e03-125">Tento kód vytvoří uživatelské rozhraní pro testovací aplikace.</span><span class="sxs-lookup"><span data-stu-id="89e03-125">This markup creates the user interface for the test application.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a><span data-ttu-id="89e03-126">Přidání nového uživatelského ovládacího prvku do projektu</span><span class="sxs-lookup"><span data-stu-id="89e03-126">Adding a New User Control to the Project</span></span>  
 <span data-ttu-id="89e03-127">V této části přidáte nový uživatelský ovládací prvek do projektu.</span><span class="sxs-lookup"><span data-stu-id="89e03-127">In this section, you will add a new user control to the project.</span></span>  
  
### <a name="to-add-a-new-user-control"></a><span data-ttu-id="89e03-128">Chcete-li přidat nového uživatelského ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="89e03-128">To add a new user control</span></span>  
  
1.  <span data-ttu-id="89e03-129">V nabídce Projekt vyberte **přidat uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="89e03-129">On the Project menu, select **Add User Control**.</span></span>  
  
2.  <span data-ttu-id="89e03-130">V dialogovém okně Přidat novou položku změnit název, který má `Circle.xaml`a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="89e03-130">In the Add New Item dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>  
  
     <span data-ttu-id="89e03-131">Circle.XAML a jeho použití modelu code-behind se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="89e03-131">Circle.xaml and its code-behind is added to the project.</span></span>  
  
3.  <span data-ttu-id="89e03-132">Otevřete Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="89e03-132">Open Circle.xaml.</span></span>  
  
     <span data-ttu-id="89e03-133">Tento soubor bude obsahovat prvky uživatelského rozhraní uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="89e03-133">This file will contain the user interface elements of the user control.</span></span>  
  
4.  <span data-ttu-id="89e03-134">Přidejte následující kód do kořenového adresáře <xref:System.Windows.Controls.Grid> k vytvoření jednoduché uživatelský ovládací prvek, který má kruh jako jeho uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="89e03-134">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  <span data-ttu-id="89e03-135">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e03-135">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
6.  <span data-ttu-id="89e03-136">V jazyce C# přidejte následující kód za výchozí konstruktor pro vytvoření kopie konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="89e03-136">In C#, add the following code after the default constructor to create a copy constructor.</span></span> <span data-ttu-id="89e03-137">V jazyce Visual Basic přidejte následující kód k vytvoření výchozí konstruktor a kopírovací konstruktor.</span><span class="sxs-lookup"><span data-stu-id="89e03-137">In Visual Basic, add the following code to create both a default constructor and a copy constructor.</span></span>  
  
     <span data-ttu-id="89e03-138">Aby bylo možné povolit uživatelského ovládacího prvku, které se mají zkopírovat, přidejte metodu konstruktoru kopie v souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="89e03-138">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="89e03-139">Ve zjednodušené kruh uživatelského ovládacího prvku, bude pouze zkopírujte výplně a velikost uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="89e03-139">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a><span data-ttu-id="89e03-140">Chcete-li přidat uživatelský ovládací prvek do hlavního okna</span><span class="sxs-lookup"><span data-stu-id="89e03-140">To add the user control to the main window</span></span>  
  
1.  <span data-ttu-id="89e03-141">Otevřete soubor MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="89e03-141">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="89e03-142">Přidejte následující XAML do otevíracího <xref:System.Windows.Window> značku k vytvoření oboru názvů XML odkaz na aktuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="89e03-142">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  <span data-ttu-id="89e03-143">V prvním <xref:System.Windows.Controls.StackPanel>, přidejte následující XAML vytvořit dvě instance kruh uživatelského ovládacího prvku na panelu první.</span><span class="sxs-lookup"><span data-stu-id="89e03-143">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     <span data-ttu-id="89e03-144">Úplné XAML pro panel vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="89e03-144">The full XAML for the panel looks like the following.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a><span data-ttu-id="89e03-145">Implementace zdroj události přetažení do uživatelského ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="89e03-145">Implementing Drag Source Events in the User Control</span></span>  
 <span data-ttu-id="89e03-146">V této části se přepíšou <xref:System.Windows.UIElement.OnMouseMove%2A> metoda a zahájení operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="89e03-146">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>  
  
 <span data-ttu-id="89e03-147">Pokud je spuštěn přetáhněte (stisknutí tlačítka myši a přesunut ukazatel myši), bude balíček data, která mají být převedeny do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="89e03-147">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="89e03-148">V takovém případě bude ovládací prvek kruh balíček tři položky data; řetězcová reprezentace jeho barva výplně, dvojité vyjádření výšku a zkopírujte sebe sama.</span><span class="sxs-lookup"><span data-stu-id="89e03-148">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="89e03-149">K zahájení operace přetažení myší</span><span class="sxs-lookup"><span data-stu-id="89e03-149">To initiate a drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="89e03-150">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e03-150">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="89e03-151">Přidejte následující <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.MouseMove> událostí.</span><span class="sxs-lookup"><span data-stu-id="89e03-151">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     <span data-ttu-id="89e03-152">To <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e03-152">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="89e03-153">Kontroluje, zda se stiskne tlačítko levé tlačítko myši, zatímco ukazatel myši pohybuje.</span><span class="sxs-lookup"><span data-stu-id="89e03-153">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>  
  
    -   <span data-ttu-id="89e03-154">Balíčky kruh dat do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="89e03-154">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="89e03-155">V tomto případě ovládací prvek kruh balíčky tři položky data; řetězcová reprezentace jeho barva výplně, dvojité vyjádření výšku a zkopírujte sebe sama.</span><span class="sxs-lookup"><span data-stu-id="89e03-155">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
    -   <span data-ttu-id="89e03-156">Volání statické <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metoda k zahájení operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="89e03-156">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="89e03-157">Následující tři parametry předáváte <xref:System.Windows.DragDrop.DoDragDrop%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="89e03-157">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>  
  
        -   <span data-ttu-id="89e03-158">`dragSource` – Odkaz na tento ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="89e03-158">`dragSource` – A reference to this control.</span></span>  
  
        -   <span data-ttu-id="89e03-159">`data` – Tím <xref:System.Windows.DataObject> vytvořili v předchozím kódu.</span><span class="sxs-lookup"><span data-stu-id="89e03-159">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>  
  
        -   <span data-ttu-id="89e03-160">`allowedEffects` – Povolené operace přetažení myší, které jsou <xref:System.Windows.DragDropEffects.Copy> nebo <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="89e03-160">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="89e03-161">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89e03-161">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="89e03-162">Klikněte na jednu z ovládacích prvků kruh a přetáhněte ho na panely na kruh a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-162">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="89e03-163">Při přetažení přes <xref:System.Windows.Controls.TextBox>, změní se kurzor na udávajících přesun.</span><span class="sxs-lookup"><span data-stu-id="89e03-163">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>  
  
5.  <span data-ttu-id="89e03-164">Při přetažení kruh přes <xref:System.Windows.Controls.TextBox>, stiskněte klávesu CTRL.</span><span class="sxs-lookup"><span data-stu-id="89e03-164">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the CTRL key.</span></span> <span data-ttu-id="89e03-165">Všimněte si, jak kurzoru se změní jeho kopii.</span><span class="sxs-lookup"><span data-stu-id="89e03-165">Notice how the cursor changes to indicate a copy.</span></span>  
  
6.  <span data-ttu-id="89e03-166">Přetáhnout myší kruhu na <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-166">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="89e03-167">Řetězcová reprezentace barvu kruhu se připojí <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-167">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
     <span data-ttu-id="89e03-168">![Řetězcové vyjádření barvu kruhu](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="89e03-168">![String representation of Circle's fill color](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>  
  
 <span data-ttu-id="89e03-169">Ve výchozím nastavení se kurzor změní během operace přetažení myší označíte, jaký vliv má vyřazení dat bude mít.</span><span class="sxs-lookup"><span data-stu-id="89e03-169">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="89e03-170">Můžete přizpůsobit poskytnutou zpětnou vazbu pro uživatele pomocí manipulace <xref:System.Windows.UIElement.GiveFeedback> událostí a nastavení různých kurzoru.</span><span class="sxs-lookup"><span data-stu-id="89e03-170">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>  
  
### <a name="to-give-feedback-to-the-user"></a><span data-ttu-id="89e03-171">Poskytněte zpětnou vazbu pro uživatele</span><span class="sxs-lookup"><span data-stu-id="89e03-171">To give feedback to the user</span></span>  
  
1.  <span data-ttu-id="89e03-172">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e03-172">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="89e03-173">Přidejte následující <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.GiveFeedback> událostí.</span><span class="sxs-lookup"><span data-stu-id="89e03-173">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     <span data-ttu-id="89e03-174">To <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e03-174">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="89e03-175">Kontroluje <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> hodnoty nastavené v cíl přetažení <xref:System.Windows.UIElement.DragOver> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="89e03-175">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
    -   <span data-ttu-id="89e03-176">Nastaví vlastní kurzor na základě <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="89e03-176">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="89e03-177">Kurzor má předat uživateli o jaký vliv má vyřadit data budou mít vizuální zpětnou vazbu.</span><span class="sxs-lookup"><span data-stu-id="89e03-177">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>  
  
3.  <span data-ttu-id="89e03-178">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89e03-178">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="89e03-179">Přetáhněte jednu kruhu určuje přes panelů na kruh a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-179">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="89e03-180">Všimněte si, že kurzory teď vlastní ukazatele, které jste zadali <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsat.</span><span class="sxs-lookup"><span data-stu-id="89e03-180">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>  
  
     <span data-ttu-id="89e03-181">![Přetáhnout myší s vlastní ukazatele](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="89e03-181">![Drag and drop with custom cursors](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>  
  
5.  <span data-ttu-id="89e03-182">Vyberte text `green` z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-182">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
6.  <span data-ttu-id="89e03-183">Přetáhněte `green` text do ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="89e03-183">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="89e03-184">Všimněte si, že jsou zobrazeny kurzory výchozí udávajících účinky operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="89e03-184">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="89e03-185">Kurzor zpětná vazba je vždycky nastavený zdroj přetažení.</span><span class="sxs-lookup"><span data-stu-id="89e03-185">The feedback cursor is always set by the drag source.</span></span>  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a><span data-ttu-id="89e03-186">Implementace události cíl přetažení do uživatelského ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="89e03-186">Implementing Drop Target Events in the User Control</span></span>  
 <span data-ttu-id="89e03-187">V této části určíte, že uživatelský ovládací prvek je cíl přetažení, přepsání metody, které umožňují uživateli ovládací prvek jako cíl přetažení a zpracovávat data, která je na něm vyřadit.</span><span class="sxs-lookup"><span data-stu-id="89e03-187">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="89e03-188">Chcete-li povolit uživatelský ovládací prvek jako cíl přetažení</span><span class="sxs-lookup"><span data-stu-id="89e03-188">To enable the user control to be a drop target</span></span>  
  
1.  <span data-ttu-id="89e03-189">Otevřete Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="89e03-189">Open Circle.xaml.</span></span>  
  
2.  <span data-ttu-id="89e03-190">Při otevírání <xref:System.Windows.Controls.UserControl> značky, přidejte <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost a nastavte ho na `true`.</span><span class="sxs-lookup"><span data-stu-id="89e03-190">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <span data-ttu-id="89e03-191"><xref:System.Windows.UIElement.OnDrop%2A> Metoda je volána, když <xref:System.Windows.UIElement.AllowDrop%2A> je nastavena na `true` a data ze zdroje přetáhněte přesunuta uživatelský ovládací prvek kruh.</span><span class="sxs-lookup"><span data-stu-id="89e03-191">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="89e03-192">V této metodě budou zpracovávat data, která byla zahozena a použít data kruhu.</span><span class="sxs-lookup"><span data-stu-id="89e03-192">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>  
  
### <a name="to-process-the-dropped-data"></a><span data-ttu-id="89e03-193">Ke zpracování vynechaných dat</span><span class="sxs-lookup"><span data-stu-id="89e03-193">To process the dropped data</span></span>  
  
1.  <span data-ttu-id="89e03-194">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e03-194">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="89e03-195">Přidejte následující <xref:System.Windows.UIElement.OnDrop%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.Drop> událostí.</span><span class="sxs-lookup"><span data-stu-id="89e03-195">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     <span data-ttu-id="89e03-196">To <xref:System.Windows.UIElement.OnDrop%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e03-196">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="89e03-197">Používá <xref:System.Windows.DataObject.GetDataPresent%2A> metodu ke kontrole, pokud Přetahované dat obsahuje objekt řetězce.</span><span class="sxs-lookup"><span data-stu-id="89e03-197">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>  
  
    -   <span data-ttu-id="89e03-198">Používá <xref:System.Windows.DataObject.GetData%2A> metody se extrahují data řetězce, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="89e03-198">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>  
  
    -   <span data-ttu-id="89e03-199">Používá <xref:System.Windows.Media.BrushConverter> pokusí převést řetězec, který má <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="89e03-199">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="89e03-200">Pokud převod je úspěšný, štětce, který se vztahuje <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> , který poskytuje uživatelské rozhraní ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="89e03-200">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>  
  
    -   <span data-ttu-id="89e03-201">Značky <xref:System.Windows.UIElement.Drop> události jako zpracování.</span><span class="sxs-lookup"><span data-stu-id="89e03-201">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="89e03-202">Událost přetažení by měla označit jako ošetřenou, takže další prvky, které se zobrazí tato událost vědět, že uživatelský ovládací prvek kruh zpracovává ji.</span><span class="sxs-lookup"><span data-stu-id="89e03-202">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>  
  
3.  <span data-ttu-id="89e03-203">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89e03-203">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="89e03-204">Vyberte text `green` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-204">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="89e03-205">Text do ovládacího prvku kruh přetáhnout.</span><span class="sxs-lookup"><span data-stu-id="89e03-205">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="89e03-206">Kruh se změní z modrá na zelenou.</span><span class="sxs-lookup"><span data-stu-id="89e03-206">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="89e03-207">![Převod řetězce na stopu](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="89e03-207">![Convert a string to a brush](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>  
  
6.  <span data-ttu-id="89e03-208">Zadejte text `green` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-208">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="89e03-209">Vyberte text `gre` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-209">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="89e03-210">Přetáhněte do ovládacího prvku kruhu a umístěte jej.</span><span class="sxs-lookup"><span data-stu-id="89e03-210">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="89e03-211">Všimněte si, že se ukazatel změní na ukazují, že rozevírací je povoleno, ale barvu kruhu se nemění, protože `gre` není platná barva.</span><span class="sxs-lookup"><span data-stu-id="89e03-211">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>  
  
9. <span data-ttu-id="89e03-212">Z ovládacího prvku zelený kroužek přetažením na ovládacím prvku modré kruh.</span><span class="sxs-lookup"><span data-stu-id="89e03-212">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="89e03-213">Kruh se změní z modrá na zelenou.</span><span class="sxs-lookup"><span data-stu-id="89e03-213">The Circle changes from blue to green.</span></span> <span data-ttu-id="89e03-214">Všimněte si, že se zobrazí kurzor, který závisí na tom, zda <xref:System.Windows.Controls.TextBox> nebo kruhu je zdroji přetažení.</span><span class="sxs-lookup"><span data-stu-id="89e03-214">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>  
  
 <span data-ttu-id="89e03-215">Nastavení <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost `true` a zpracování dat vynechaných je vše, co je potřeba povolit element, který má být cíl přetažení.</span><span class="sxs-lookup"><span data-stu-id="89e03-215">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="89e03-216">Však zajistit lepší výkon, můžete také pracovat <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, a <xref:System.Windows.UIElement.DragOver> události.</span><span class="sxs-lookup"><span data-stu-id="89e03-216">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="89e03-217">V těchto událostí můžete provést kontroly a zadejte víc uživateli předtím, než se ukončí data.</span><span class="sxs-lookup"><span data-stu-id="89e03-217">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>  
  
 <span data-ttu-id="89e03-218">Když data je přetažený na ovládací prvek uživatele kruh, ovládací prvek by měl oznámení zdroji přetažení, zda může zpracovat data, která je právě přetáhli.</span><span class="sxs-lookup"><span data-stu-id="89e03-218">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="89e03-219">Pokud ovládací prvek není známo, jak ke zpracování dat, by měl odmítnout rozevírací nabídku.</span><span class="sxs-lookup"><span data-stu-id="89e03-219">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="89e03-220">K tomuto účelu bude zpracovávat <xref:System.Windows.UIElement.DragOver> událostí a nastavte <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="89e03-220">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="89e03-221">Chcete-li ověřit, že rozevírací dat není povolené</span><span class="sxs-lookup"><span data-stu-id="89e03-221">To verify that the data drop is allowed</span></span>  
  
1.  <span data-ttu-id="89e03-222">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e03-222">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="89e03-223">Přidejte následující <xref:System.Windows.UIElement.OnDragOver%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.DragOver> událostí.</span><span class="sxs-lookup"><span data-stu-id="89e03-223">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     <span data-ttu-id="89e03-224">To <xref:System.Windows.UIElement.OnDragOver%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e03-224">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="89e03-225">Nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.None>.</span><span class="sxs-lookup"><span data-stu-id="89e03-225">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>  
  
    -   <span data-ttu-id="89e03-226">Provádí stejné kontroly, které se provádí v <xref:System.Windows.UIElement.OnDrop%2A> metodou ke zjištění, zda uživatelský ovládací prvek kruh může zpracovávat Přetahované data.</span><span class="sxs-lookup"><span data-stu-id="89e03-226">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>  
  
    -   <span data-ttu-id="89e03-227">Pokud uživatelský ovládací prvek můžete zpracovávat data, nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Copy> nebo <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="89e03-227">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="89e03-228">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89e03-228">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="89e03-229">Vyberte text `gre` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-229">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="89e03-230">Přetáhněte text do ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="89e03-230">Drag the text to a Circle control.</span></span> <span data-ttu-id="89e03-231">Všimněte si, že se kurzor změní teď označuje, že rozevírací není povolená, protože `gre` není platná barva.</span><span class="sxs-lookup"><span data-stu-id="89e03-231">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>  
  
 <span data-ttu-id="89e03-232">Můžete dále vylepšit uživatelské prostředí s použitím operace přetažení ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="89e03-232">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="89e03-233">Pro uživatelský ovládací prvek kruh, přepíše <xref:System.Windows.UIElement.OnDragEnter%2A> a <xref:System.Windows.UIElement.OnDragLeave%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="89e03-233">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="89e03-234">Když jsou data přetažený na ovládací prvek, aktuální pozadí <xref:System.Windows.Shapes.Shape.Fill%2A> je uložen v proměnné zástupný symbol.</span><span class="sxs-lookup"><span data-stu-id="89e03-234">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="89e03-235">Pak převedena na štětce a použít na řetězec <xref:System.Windows.Shapes.Ellipse> kruhu, která poskytuje uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="89e03-235">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="89e03-236">Pokud data ocitne mimo kruh bez probíhá vyřazování původní <xref:System.Windows.Shapes.Shape.Fill%2A> hodnota je znovu použita v kruhu.</span><span class="sxs-lookup"><span data-stu-id="89e03-236">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="89e03-237">Náhled účinky operace přetažení myší</span><span class="sxs-lookup"><span data-stu-id="89e03-237">To preview the effects of the drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="89e03-238">Otevřete Circle.xaml.cs nebo Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e03-238">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="89e03-239">Ve třídě kruh deklarovat soukromé <xref:System.Windows.Media.Brush> proměnnou s názvem `_previousFill` a inicializujte ji na `null`.</span><span class="sxs-lookup"><span data-stu-id="89e03-239">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  <span data-ttu-id="89e03-240">Přidejte následující <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.DragEnter> událostí.</span><span class="sxs-lookup"><span data-stu-id="89e03-240">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     <span data-ttu-id="89e03-241">To <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e03-241">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="89e03-242">Uloží <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost <xref:System.Windows.Shapes.Ellipse> v `_previousFill` proměnné.</span><span class="sxs-lookup"><span data-stu-id="89e03-242">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>  
  
    -   <span data-ttu-id="89e03-243">Provádí stejné kontroly, které se provádí v <xref:System.Windows.UIElement.OnDrop%2A> metodou ke zjištění, zda data lze převést na <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="89e03-243">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="89e03-244">Pokud data je převést na platnou <xref:System.Windows.Media.Brush>, použije ho k <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="89e03-244">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
4.  <span data-ttu-id="89e03-245">Přidejte následující <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání zajistit zpracování třídy pro <xref:System.Windows.UIElement.DragLeave> událostí.</span><span class="sxs-lookup"><span data-stu-id="89e03-245">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     <span data-ttu-id="89e03-246">To <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e03-246">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="89e03-247">Se vztahuje <xref:System.Windows.Media.Brush> uložené v `_previousFill` proměnnou <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> , který poskytuje uživatelské rozhraní uživatelského ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="89e03-247">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>  
  
5.  <span data-ttu-id="89e03-248">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89e03-248">Press F5 to build and run the application.</span></span>  
  
6.  <span data-ttu-id="89e03-249">Vyberte text `green` v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-249">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="89e03-250">Přetáhněte text myší na ovládací prvek kruh bez zastaví.</span><span class="sxs-lookup"><span data-stu-id="89e03-250">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="89e03-251">Kruh se změní z modrá na zelenou.</span><span class="sxs-lookup"><span data-stu-id="89e03-251">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="89e03-252">![Ve verzi Preview efekty přetáhněte&#45;a&#45;operace odstranění](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="89e03-252">![Preview the effects of a drag&#45;and&#45;drop operation](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>  
  
8.  <span data-ttu-id="89e03-253">Přetáhněte text z ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="89e03-253">Drag the text away from the Circle control.</span></span> <span data-ttu-id="89e03-254">Kruh se změní z zelené zpět na modrou.</span><span class="sxs-lookup"><span data-stu-id="89e03-254">The Circle changes from green back to blue.</span></span>  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a><span data-ttu-id="89e03-255">Povolení panely přijímat vyřadit dat</span><span class="sxs-lookup"><span data-stu-id="89e03-255">Enabling a Panel to Receive Dropped Data</span></span>  
 <span data-ttu-id="89e03-256">V této části vám umožní panely, které jsou hostiteli uživatelské ovládací prvky kruh tak, aby fungoval jako cíle přetažení pro Přetahované data kruh.</span><span class="sxs-lookup"><span data-stu-id="89e03-256">In this section, you will enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="89e03-257">Budete implementovat kód, který umožňuje přesunout kruh z jednoho panelu na jiný, nebo vytvořte kopii kruh ovládací prvek tím, že podržíte stisknutou klávesu CTRL při přetahování kruh.</span><span class="sxs-lookup"><span data-stu-id="89e03-257">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the CTRL key while dragging and dropping a Circle.</span></span>  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a><span data-ttu-id="89e03-258">Povolit panelu bude cíle přetažení</span><span class="sxs-lookup"><span data-stu-id="89e03-258">To enable the panel to be a drop target</span></span>  
  
1.  <span data-ttu-id="89e03-259">Otevřete soubor MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="89e03-259">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="89e03-260">Jak je znázorněno v následující XAML v každém <xref:System.Windows.Controls.StackPanel> přidat obslužné rutiny pro ovládací prvky, <xref:System.Windows.UIElement.DragOver> a <xref:System.Windows.UIElement.Drop> události.</span><span class="sxs-lookup"><span data-stu-id="89e03-260">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="89e03-261">Název <xref:System.Windows.UIElement.DragOver> obslužná rutina události `panel_DragOver`a pojmenujte <xref:System.Windows.UIElement.Drop> obslužná rutina události, `panel_Drop`.</span><span class="sxs-lookup"><span data-stu-id="89e03-261">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  <span data-ttu-id="89e03-262">Otevřete MainWindows.xaml.cs nebo soubor MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="89e03-262">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>  
  
4.  <span data-ttu-id="89e03-263">Přidejte následující kód <xref:System.Windows.UIElement.DragOver> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="89e03-263">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     <span data-ttu-id="89e03-264">To <xref:System.Windows.UIElement.DragOver> obslužná rutina události provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e03-264">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="89e03-265">Kontroluje, že Přetahované data obsahují data "Object", který byl zabalen do <xref:System.Windows.DataObject> v uživatelském ovládacím prvku kruhu a předat ve volání do <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span><span class="sxs-lookup"><span data-stu-id="89e03-265">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>  
  
    -   <span data-ttu-id="89e03-266">Pokud jsou k dispozici data "Object", zkontroluje, zda je klávesa CTRL stisknuta.</span><span class="sxs-lookup"><span data-stu-id="89e03-266">If the "Object" data is present, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="89e03-267">Pokud se stiskne klávesu CTRL, nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Copy>.</span><span class="sxs-lookup"><span data-stu-id="89e03-267">If the CTRL key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="89e03-268">V opačném případě nastavte <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="89e03-268">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
5.  <span data-ttu-id="89e03-269">Přidejte následující kód <xref:System.Windows.UIElement.Drop> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="89e03-269">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     <span data-ttu-id="89e03-270">To <xref:System.Windows.UIElement.Drop> obslužná rutina události provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="89e03-270">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="89e03-271">Kontroluje, zda <xref:System.Windows.UIElement.Drop> události již byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="89e03-271">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="89e03-272">Pro instanci, která kroužek ztracené kruhu na jiném obslužné rutiny <xref:System.Windows.UIElement.Drop> události, nechcete, aby panelu, který obsahuje kruhu také ji zpracovat.</span><span class="sxs-lookup"><span data-stu-id="89e03-272">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>  
  
    -   <span data-ttu-id="89e03-273">Pokud <xref:System.Windows.UIElement.Drop> událostí není zpracována, zkontroluje, zda je klávesa CTRL stisknuta.</span><span class="sxs-lookup"><span data-stu-id="89e03-273">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="89e03-274">Pokud se stiskne klávesa CTRL, kdy <xref:System.Windows.UIElement.Drop> se stane, vytvoří kopii kruhu ovládací prvek a přidat ji do <xref:System.Windows.Controls.Panel.Children%2A> kolekce <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="89e03-274">If the CTRL key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
    -   <span data-ttu-id="89e03-275">Pokud se stiskne klávesu CTRL, přesune kruh z <xref:System.Windows.Controls.Panel.Children%2A> kolekce jeho nadřazeného panelu <xref:System.Windows.Controls.Panel.Children%2A> kolekce, která byla vynechána na panelu.</span><span class="sxs-lookup"><span data-stu-id="89e03-275">If the CTRL key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>  
  
    -   <span data-ttu-id="89e03-276">Sady <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost upozornit <xref:System.Windows.DragDrop.DoDragDrop%2A> metody Určuje, zda byla provedena operace přesunutí nebo kopírování.</span><span class="sxs-lookup"><span data-stu-id="89e03-276">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>  
  
6.  <span data-ttu-id="89e03-277">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89e03-277">Press F5 to build and run the application.</span></span>  
  
7.  <span data-ttu-id="89e03-278">Vyberte text `green` z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="89e03-278">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="89e03-279">Přetáhněte myší na ovládací prvek kruh text a umístěte jej.</span><span class="sxs-lookup"><span data-stu-id="89e03-279">Drag the text over a Circle control and drop it.</span></span>  
  
9. <span data-ttu-id="89e03-280">Přetáhněte ovládací prvek kruhu na levém panelu na pravém panelu a umístěte ho.</span><span class="sxs-lookup"><span data-stu-id="89e03-280">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="89e03-281">Kruh se odebere z <xref:System.Windows.Controls.Panel.Children%2A> kolekce na levém panelu a přidat do podřízené kolekce pravého panelu.</span><span class="sxs-lookup"><span data-stu-id="89e03-281">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>  
  
10. <span data-ttu-id="89e03-282">Přetáhněte ovládací prvek kruh z panelu, které se nachází na panel a umístěte jej při stisknutí klávesy CTRL.</span><span class="sxs-lookup"><span data-stu-id="89e03-282">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the CTRL key.</span></span> <span data-ttu-id="89e03-283">Kruh se zkopíruje a kopie je přidána do <xref:System.Windows.Controls.Panel.Children%2A> kolekce přijímající panelu.</span><span class="sxs-lookup"><span data-stu-id="89e03-283">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>  
  
     <span data-ttu-id="89e03-284">![Přetažení kruh při stisknutí klávesy CTRL](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="89e03-284">![Dragging a Circle while pressing the CTRL key](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e03-285">Viz také</span><span class="sxs-lookup"><span data-stu-id="89e03-285">See Also</span></span>  
 [<span data-ttu-id="89e03-286">Přehled přetažení</span><span class="sxs-lookup"><span data-stu-id="89e03-286">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
