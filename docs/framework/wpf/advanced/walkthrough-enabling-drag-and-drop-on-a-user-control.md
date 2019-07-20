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
ms.openlocfilehash: 80fd55be9230729cb8336be91c1d8fb4f7f3f080
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364260"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="52ec6-102">Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku</span><span class="sxs-lookup"><span data-stu-id="52ec6-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="52ec6-103">Tento návod ukazuje, jak vytvořit vlastní uživatelský ovládací prvek, který se může zúčastnit přenosu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]dat přetahováním myší.</span><span class="sxs-lookup"><span data-stu-id="52ec6-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="52ec6-104">V tomto návodu vytvoříte vlastní WPF <xref:System.Windows.Controls.UserControl> , který představuje kruhový tvar.</span><span class="sxs-lookup"><span data-stu-id="52ec6-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="52ec6-105">V ovládacím prvku implementujete funkce pro povolení přenosu dat pomocí přetahování myší.</span><span class="sxs-lookup"><span data-stu-id="52ec6-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="52ec6-106">Například pokud přetáhnete jeden ovládací prvek kruh do druhého, data barvy výplně se zkopírují ze zdrojového kruhu do cíle.</span><span class="sxs-lookup"><span data-stu-id="52ec6-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="52ec6-107">Pokud přetáhnete z ovládacího prvku Circle do <xref:System.Windows.Controls.TextBox>, Řetězcová reprezentace barvy výplně je zkopírována <xref:System.Windows.Controls.TextBox>do.</span><span class="sxs-lookup"><span data-stu-id="52ec6-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="52ec6-108">Také vytvoříte malou aplikaci, která obsahuje dva ovládací prvky panelu a a <xref:System.Windows.Controls.TextBox> k otestování funkcí přetahování myší.</span><span class="sxs-lookup"><span data-stu-id="52ec6-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="52ec6-109">Napíšete kód, který panelům umožní zpracovat vyhozená data kruhů, což vám umožní přesouvat nebo kopírovat kružnice z kolekce podřízených prvků jednoho panelu na druhý.</span><span class="sxs-lookup"><span data-stu-id="52ec6-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="52ec6-110">Tento návod znázorňuje následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="52ec6-110">This walkthrough illustrates the following tasks:</span></span>

- <span data-ttu-id="52ec6-111">Vytvořte vlastní uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="52ec6-111">Create a custom user control.</span></span>

- <span data-ttu-id="52ec6-112">Povolit uživatelský ovládací prvek jako zdroj přetažení.</span><span class="sxs-lookup"><span data-stu-id="52ec6-112">Enable the user control to be a drag source.</span></span>

- <span data-ttu-id="52ec6-113">Povolit uživatelský ovládací prvek jako cíl přetažení.</span><span class="sxs-lookup"><span data-stu-id="52ec6-113">Enable the user control to be a drop target.</span></span>

- <span data-ttu-id="52ec6-114">Umožňuje panelu, aby přijímal data vyřazená z uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="52ec6-114">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="52ec6-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52ec6-115">Prerequisites</span></span>

<span data-ttu-id="52ec6-116">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="52ec6-116">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="52ec6-117">Vytvoření projektu aplikace</span><span class="sxs-lookup"><span data-stu-id="52ec6-117">Create the Application Project</span></span>
 <span data-ttu-id="52ec6-118">V této části vytvoříte aplikační infrastrukturu, která bude obsahovat hlavní stránku se dvěma panely a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-118">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1. <span data-ttu-id="52ec6-119">Vytvořte nový projekt aplikace WPF v Visual Basic nebo vizuálu C# s názvem `DragDropExample`.</span><span class="sxs-lookup"><span data-stu-id="52ec6-119">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="52ec6-120">Další informace najdete v tématu [Návod: Moje první desktopová aplikace](../getting-started/walkthrough-my-first-wpf-desktop-application.md)WPF.</span><span class="sxs-lookup"><span data-stu-id="52ec6-120">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="52ec6-121">Otevřete MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="52ec6-121">Open MainWindow.xaml.</span></span>

3. <span data-ttu-id="52ec6-122">Přidejte následující značku mezi otevírací a uzavírací <xref:System.Windows.Controls.Grid> značku.</span><span class="sxs-lookup"><span data-stu-id="52ec6-122">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="52ec6-123">Tento kód vytvoří uživatelské rozhraní pro testovací aplikaci.</span><span class="sxs-lookup"><span data-stu-id="52ec6-123">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="52ec6-124">Přidat do projektu nový uživatelský ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="52ec6-124">Add a New User Control to the Project</span></span>
 <span data-ttu-id="52ec6-125">V této části přidáte do projektu nový uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="52ec6-125">In this section, you will add a new user control to the project.</span></span>

1. <span data-ttu-id="52ec6-126">V nabídce projekt vyberte **Přidat uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="52ec6-126">On the Project menu, select **Add User Control**.</span></span>

2. <span data-ttu-id="52ec6-127">V dialogovém okně **Přidat novou položku** změňte název na `Circle.xaml`a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="52ec6-127">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="52ec6-128">Do projektu se přidá Circle. XAML a jeho kód na pozadí.</span><span class="sxs-lookup"><span data-stu-id="52ec6-128">Circle.xaml and its code-behind is added to the project.</span></span>

3. <span data-ttu-id="52ec6-129">Otevřete Circle. XAML.</span><span class="sxs-lookup"><span data-stu-id="52ec6-129">Open Circle.xaml.</span></span>

     <span data-ttu-id="52ec6-130">Tento soubor bude obsahovat prvky uživatelského rozhraní uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="52ec6-130">This file will contain the user interface elements of the user control.</span></span>

4. <span data-ttu-id="52ec6-131">Přidejte následující kód do kořenového adresáře <xref:System.Windows.Controls.Grid> pro vytvoření jednoduchého uživatelského ovládacího prvku, který má modrý kroužek jako své uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="52ec6-131">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. <span data-ttu-id="52ec6-132">Otevřete Circle.xaml.cs nebo Circle. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="52ec6-132">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6. <span data-ttu-id="52ec6-133">V C#přidejte následující kód za konstruktor bez parametrů k vytvoření kopírovacího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="52ec6-133">In C#, add the following code after the parameterless constructor to create a copy constructor.</span></span> <span data-ttu-id="52ec6-134">V Visual Basic přidejte následující kód pro vytvoření konstruktoru bez parametrů a kopírovacího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="52ec6-134">In Visual Basic, add the following code to create both a parameterless constructor and a copy constructor.</span></span>

     <span data-ttu-id="52ec6-135">Chcete-li, aby byl uživatelský ovládací prvek zkopírován, přidejte do souboru kódu na pozadí metodu kopírovacího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="52ec6-135">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="52ec6-136">V uživatelském ovládacím prvku zjednodušený kruh budete kopírovat pouze výplň a velikost uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="52ec6-136">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="52ec6-137">Přidání uživatelského ovládacího prvku do hlavního okna</span><span class="sxs-lookup"><span data-stu-id="52ec6-137">Add the user control to the main window</span></span>

1. <span data-ttu-id="52ec6-138">Otevřete MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="52ec6-138">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="52ec6-139">Přidejte následující kód XAML do úvodní <xref:System.Windows.Window> značky a vytvořte tak odkaz na obor názvů XML na aktuální aplikaci.</span><span class="sxs-lookup"><span data-stu-id="52ec6-139">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. <span data-ttu-id="52ec6-140">V prvním <xref:System.Windows.Controls.StackPanel>panelu přidejte následující XAML pro vytvoření dvou instancí uživatelského ovládacího prvku Circle.</span><span class="sxs-lookup"><span data-stu-id="52ec6-140">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="52ec6-141">Úplný kód XAML pro panel vypadá následovně.</span><span class="sxs-lookup"><span data-stu-id="52ec6-141">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="52ec6-142">Implementace přetáhněte zdrojové události do uživatelského ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="52ec6-142">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="52ec6-143">V této části přepíšete <xref:System.Windows.UIElement.OnMouseMove%2A> metodu a inicializujete operaci přetažení.</span><span class="sxs-lookup"><span data-stu-id="52ec6-143">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="52ec6-144">Pokud je spuštěno přetahování (stisknuto tlačítko myši a přesun myši), zabalíte data, která chcete přenést do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-144">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="52ec6-145">V tomto případě bude ovládací prvek kruh zabalit tři datové položky. Řetězcová reprezentace barvy jeho výplně, dvojitá reprezentace jeho výšky a kopie sebe sama.</span><span class="sxs-lookup"><span data-stu-id="52ec6-145">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="52ec6-146">Zahájení operace přetažení myší</span><span class="sxs-lookup"><span data-stu-id="52ec6-146">To initiate a drag-and-drop operation</span></span>

1. <span data-ttu-id="52ec6-147">Otevřete Circle.xaml.cs nebo Circle. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="52ec6-147">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="52ec6-148">Přidejte následující <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání k poskytnutí třídy <xref:System.Windows.UIElement.MouseMove> pro zpracování události.</span><span class="sxs-lookup"><span data-stu-id="52ec6-148">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="52ec6-149">Toto <xref:System.Windows.UIElement.OnMouseMove%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="52ec6-149">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="52ec6-150">Kontroluje, zda se při přesouvání myši stiskne levé tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="52ec6-150">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    - <span data-ttu-id="52ec6-151">Zabalí data do kruhu do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-151">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="52ec6-152">V tomto případě ovládací prvek Circle balí tři datové položky; Řetězcová reprezentace barvy jeho výplně, dvojitá reprezentace jeho výšky a kopie sebe sama.</span><span class="sxs-lookup"><span data-stu-id="52ec6-152">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    - <span data-ttu-id="52ec6-153">Volá statickou <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metodu pro zahájení operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="52ec6-153">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="52ec6-154"><xref:System.Windows.DragDrop.DoDragDrop%2A> Metodě předáte následující tři parametry:</span><span class="sxs-lookup"><span data-stu-id="52ec6-154">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        - <span data-ttu-id="52ec6-155">`dragSource`– Odkaz na tento ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="52ec6-155">`dragSource` – A reference to this control.</span></span>

        - <span data-ttu-id="52ec6-156">`data`<xref:System.Windows.DataObject> – Vytvořeno v předchozím kódu.</span><span class="sxs-lookup"><span data-stu-id="52ec6-156">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        - <span data-ttu-id="52ec6-157">`allowedEffects`– Povolené operace přetažení, které jsou <xref:System.Windows.DragDropEffects.Copy> nebo. <xref:System.Windows.DragDropEffects.Move></span><span class="sxs-lookup"><span data-stu-id="52ec6-157">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="52ec6-158">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="52ec6-158">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="52ec6-159">Klikněte na jeden z ovládacích prvků kruh a přetáhněte ho na panely, druhý kruh a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-159">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="52ec6-160">Při přetahování přes <xref:System.Windows.Controls.TextBox>se kurzor změní, aby označoval přesunutí.</span><span class="sxs-lookup"><span data-stu-id="52ec6-160">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5. <span data-ttu-id="52ec6-161">Při přetahování kružnice <xref:System.Windows.Controls.TextBox>na stiskněte klávesu **CTRL** .</span><span class="sxs-lookup"><span data-stu-id="52ec6-161">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="52ec6-162">Všimněte si, jak se kurzor změní, aby označoval kopii.</span><span class="sxs-lookup"><span data-stu-id="52ec6-162">Notice how the cursor changes to indicate a copy.</span></span>

6. <span data-ttu-id="52ec6-163">Přetáhněte kruh na <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-163">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="52ec6-164">Řetězcová reprezentace barvy výplně kruhu je připojena k <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-164">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="52ec6-165">![Řetězcová reprezentace barvy výplně kruhu](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="52ec6-165">![String representation of Circle's fill color](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="52ec6-166">Ve výchozím nastavení se kurzor během operace přetažení změní, aby označoval, jaký vliv bude mít data na odstranění.</span><span class="sxs-lookup"><span data-stu-id="52ec6-166">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="52ec6-167">Zpětnou vazbu určenou uživateli můžete přizpůsobit zpracováním <xref:System.Windows.UIElement.GiveFeedback> události a nastavením jiného kurzoru.</span><span class="sxs-lookup"><span data-stu-id="52ec6-167">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="52ec6-168">Poskytněte uživateli zpětnou vazbu.</span><span class="sxs-lookup"><span data-stu-id="52ec6-168">Give feedback to the user</span></span>

1. <span data-ttu-id="52ec6-169">Otevřete Circle.xaml.cs nebo Circle. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="52ec6-169">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="52ec6-170">Přidejte následující <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání k poskytnutí třídy <xref:System.Windows.UIElement.GiveFeedback> pro zpracování události.</span><span class="sxs-lookup"><span data-stu-id="52ec6-170">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="52ec6-171">Toto <xref:System.Windows.UIElement.OnGiveFeedback%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="52ec6-171">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="52ec6-172">Kontroluje hodnoty, které jsou nastaveny v obslužné rutině <xref:System.Windows.UIElement.DragOver> události cílového umístění. <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A></span><span class="sxs-lookup"><span data-stu-id="52ec6-172">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    - <span data-ttu-id="52ec6-173">Nastaví vlastní kurzor na základě <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="52ec6-173">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="52ec6-174">Cílem tohoto kurzoru je poskytnout vizuální zpětnou vazbu uživateli o tom, jaký vliv bude mít data přehozena.</span><span class="sxs-lookup"><span data-stu-id="52ec6-174">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3. <span data-ttu-id="52ec6-175">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="52ec6-175">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="52ec6-176">Přetáhněte jeden z kruhových ovládacích prvků přes panely, druhý kruh a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-176">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="52ec6-177">Všimněte si, že kurzory jsou nyní vlastními kurzory, které jste zadali <xref:System.Windows.UIElement.OnGiveFeedback%2A> v přepsání.</span><span class="sxs-lookup"><span data-stu-id="52ec6-177">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="52ec6-178">![Přetahování pomocí vlastních kurzorů](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="52ec6-178">![Drag and drop with custom cursors](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5. <span data-ttu-id="52ec6-179">Vyberte text `green` <xref:System.Windows.Controls.TextBox>z.</span><span class="sxs-lookup"><span data-stu-id="52ec6-179">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6. <span data-ttu-id="52ec6-180">`green` Přetáhněte text do ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="52ec6-180">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="52ec6-181">Všimněte si, že výchozí kurzory jsou zobrazeny pro indikaci vlivu operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="52ec6-181">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="52ec6-182">Ukazatel zpětné vazby je vždy nastaven zdrojem přetažení.</span><span class="sxs-lookup"><span data-stu-id="52ec6-182">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="52ec6-183">Implementovat události cíle zrušení v uživatelském ovládacím prvku</span><span class="sxs-lookup"><span data-stu-id="52ec6-183">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="52ec6-184">V této části určíte, že uživatelský ovládací prvek je cílem přetažení, přepište metody, které umožňují, aby uživatelský ovládací prvek byl cílem přetažení, a zpracovávat data, která jsou na něm vyřazena.</span><span class="sxs-lookup"><span data-stu-id="52ec6-184">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="52ec6-185">Povolení uživatelského ovládacího prvku jako cíle přetažení</span><span class="sxs-lookup"><span data-stu-id="52ec6-185">To enable the user control to be a drop target</span></span>

1. <span data-ttu-id="52ec6-186">Otevřete Circle. XAML.</span><span class="sxs-lookup"><span data-stu-id="52ec6-186">Open Circle.xaml.</span></span>

2. <span data-ttu-id="52ec6-187">V otevírací <xref:System.Windows.Controls.UserControl> značce <xref:System.Windows.UIElement.AllowDrop%2A> přidejte vlastnost a nastavte ji na `true`.</span><span class="sxs-lookup"><span data-stu-id="52ec6-187">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="52ec6-188">Metoda je volána, <xref:System.Windows.UIElement.AllowDrop%2A> když je vlastnost nastavena na `true` hodnotu a data ze zdroje přetažení jsou vyřazena v uživatelském ovládacím prvku Circle. <xref:System.Windows.UIElement.OnDrop%2A></span><span class="sxs-lookup"><span data-stu-id="52ec6-188">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="52ec6-189">V této metodě budete zpracovávat data, která byla vyřazena, a použijí data v kruhu.</span><span class="sxs-lookup"><span data-stu-id="52ec6-189">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="52ec6-190">Zpracování zahozených dat</span><span class="sxs-lookup"><span data-stu-id="52ec6-190">To process the dropped data</span></span>

1. <span data-ttu-id="52ec6-191">Otevřete Circle.xaml.cs nebo Circle. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="52ec6-191">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="52ec6-192">Přidejte následující <xref:System.Windows.UIElement.OnDrop%2A> přepsání k poskytnutí třídy <xref:System.Windows.UIElement.Drop> pro zpracování události.</span><span class="sxs-lookup"><span data-stu-id="52ec6-192">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="52ec6-193">Toto <xref:System.Windows.UIElement.OnDrop%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="52ec6-193">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="52ec6-194"><xref:System.Windows.DataObject.GetDataPresent%2A> Používá metodu ke kontrole, zda přetažená data obsahují objekt String.</span><span class="sxs-lookup"><span data-stu-id="52ec6-194">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    - <span data-ttu-id="52ec6-195"><xref:System.Windows.DataObject.GetData%2A> Používá metodu k extrakci řetězcových dat, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="52ec6-195">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    - <span data-ttu-id="52ec6-196">Používá k pokusu o převod řetězce <xref:System.Windows.Media.Brush>na. <xref:System.Windows.Media.BrushConverter></span><span class="sxs-lookup"><span data-stu-id="52ec6-196">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="52ec6-197">Pokud je převod úspěšný, použije štětec na <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> z, který poskytuje uživatelské rozhraní ovládacího prvku Circle.</span><span class="sxs-lookup"><span data-stu-id="52ec6-197">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    - <span data-ttu-id="52ec6-198"><xref:System.Windows.UIElement.Drop> Označí událost jako zpracovanou.</span><span class="sxs-lookup"><span data-stu-id="52ec6-198">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="52ec6-199">Odkládací událost byste měli označit jako pořízenou, aby ostatní prvky, které obdrží tuto událost, věděly, že ovládací prvek kruhového uživatele ho zpracoval.</span><span class="sxs-lookup"><span data-stu-id="52ec6-199">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3. <span data-ttu-id="52ec6-200">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="52ec6-200">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="52ec6-201">Vyberte text `green` v části <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-201">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="52ec6-202">Přetáhněte text do kruhu a pusťte ho do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="52ec6-202">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="52ec6-203">Kruh se změní z modré na zelenou.</span><span class="sxs-lookup"><span data-stu-id="52ec6-203">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="52ec6-204">![Převod řetězce na štětec](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="52ec6-204">![Convert a string to a brush](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6. <span data-ttu-id="52ec6-205">Zadejte text `green` do pole <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-205">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="52ec6-206">Vyberte text `gre` v části <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-206">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="52ec6-207">Přetáhněte ho do kruhu a pusťte ho do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="52ec6-207">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="52ec6-208">Všimněte si, že se kurzor změní, aby označoval, že je povoleno zrušení, ale barva kružnice se nemění `gre` , protože není platná barva.</span><span class="sxs-lookup"><span data-stu-id="52ec6-208">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="52ec6-209">Přetáhněte z zeleného kruhu ovládacího prvku a umístěte ukazatel myši na ovládací prvek modrého kruhu.</span><span class="sxs-lookup"><span data-stu-id="52ec6-209">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="52ec6-210">Kruh se změní z modré na zelenou.</span><span class="sxs-lookup"><span data-stu-id="52ec6-210">The Circle changes from blue to green.</span></span> <span data-ttu-id="52ec6-211">Všimněte si, že se kurzor zobrazuje, závisí na <xref:System.Windows.Controls.TextBox> tom, zda je nebo kroužek zdrojem přetažení.</span><span class="sxs-lookup"><span data-stu-id="52ec6-211">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="52ec6-212">Nastavení vlastnosti na `true` a zpracování vynechaných dat je vyžadováno pro povolení prvku jako cíle přetažení. <xref:System.Windows.UIElement.AllowDrop%2A></span><span class="sxs-lookup"><span data-stu-id="52ec6-212">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="52ec6-213">Chcete-li však poskytnout lepší uživatelské prostředí, měli byste také zpracovat <xref:System.Windows.UIElement.DragEnter>události, <xref:System.Windows.UIElement.DragLeave>a. <xref:System.Windows.UIElement.DragOver></span><span class="sxs-lookup"><span data-stu-id="52ec6-213">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="52ec6-214">V těchto událostech můžete provádět kontroly a před vyřazením dat poskytnout uživateli dodatečnou zpětnou vazbu.</span><span class="sxs-lookup"><span data-stu-id="52ec6-214">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="52ec6-215">Když jsou data přetažena přes uživatelský ovládací prvek kruh, ovládací prvek by měl informovat zdroj přetažení, zda může zpracovat data, která jsou přetažena.</span><span class="sxs-lookup"><span data-stu-id="52ec6-215">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="52ec6-216">Pokud ovládací prvek neví, jak data zpracovat, měla by být zamítnuta operace drop.</span><span class="sxs-lookup"><span data-stu-id="52ec6-216">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="52ec6-217">K tomu je potřeba zpracovat <xref:System.Windows.UIElement.DragOver> událost a <xref:System.Windows.DragEventArgs.Effects%2A> nastavit vlastnost.</span><span class="sxs-lookup"><span data-stu-id="52ec6-217">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="52ec6-218">Ověření, zda je povoleno ukládání dat</span><span class="sxs-lookup"><span data-stu-id="52ec6-218">To verify that the data drop is allowed</span></span>

1. <span data-ttu-id="52ec6-219">Otevřete Circle.xaml.cs nebo Circle. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="52ec6-219">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="52ec6-220">Přidejte následující <xref:System.Windows.UIElement.OnDragOver%2A> přepsání k poskytnutí třídy <xref:System.Windows.UIElement.DragOver> pro zpracování události.</span><span class="sxs-lookup"><span data-stu-id="52ec6-220">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="52ec6-221">Toto <xref:System.Windows.UIElement.OnDragOver%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="52ec6-221">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="52ec6-222">Nastaví vlastnost na <xref:System.Windows.DragDropEffects.None>hodnotu. <xref:System.Windows.DragEventArgs.Effects%2A></span><span class="sxs-lookup"><span data-stu-id="52ec6-222">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    - <span data-ttu-id="52ec6-223">Provede stejné kontroly, které jsou provedeny v <xref:System.Windows.UIElement.OnDrop%2A> metodě k určení, zda uživatelský ovládací prvek kruh může zpracovat přetažená data.</span><span class="sxs-lookup"><span data-stu-id="52ec6-223">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    - <span data-ttu-id="52ec6-224">Pokud uživatelský ovládací prvek může zpracovat data, nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost na <xref:System.Windows.DragDropEffects.Copy> nebo <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-224">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="52ec6-225">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="52ec6-225">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="52ec6-226">Vyberte text `gre` v části <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-226">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="52ec6-227">Přetáhněte text do ovládacího prvku kruh.</span><span class="sxs-lookup"><span data-stu-id="52ec6-227">Drag the text to a Circle control.</span></span> <span data-ttu-id="52ec6-228">Všimněte si, že kurzor se nyní změní, aby označoval, že zrušení není `gre` povoleno, protože není platná barva.</span><span class="sxs-lookup"><span data-stu-id="52ec6-228">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="52ec6-229">Činnost koncového uživatele můžete dále vylepšit použitím náhledu operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="52ec6-229">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="52ec6-230">Pro uživatelský ovládací prvek kruh přepíšete <xref:System.Windows.UIElement.OnDragEnter%2A> metody a. <xref:System.Windows.UIElement.OnDragLeave%2A></span><span class="sxs-lookup"><span data-stu-id="52ec6-230">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="52ec6-231">Když jsou data přetažena na ovládací prvek, aktuální pozadí <xref:System.Windows.Shapes.Shape.Fill%2A> je uloženo v zástupné proměnné.</span><span class="sxs-lookup"><span data-stu-id="52ec6-231">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="52ec6-232">Řetězec se pak převede na štětec a použije se na <xref:System.Windows.Shapes.Ellipse> rozhraní, které poskytuje kolečko v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="52ec6-232">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="52ec6-233">Pokud jsou data přetažena mimo kruh, aniž by byla vynechána, původní <xref:System.Windows.Shapes.Shape.Fill%2A> hodnota se znovu použije na kroužek.</span><span class="sxs-lookup"><span data-stu-id="52ec6-233">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="52ec6-234">Náhled efektů operace přetažení</span><span class="sxs-lookup"><span data-stu-id="52ec6-234">To preview the effects of the drag-and-drop operation</span></span>

1. <span data-ttu-id="52ec6-235">Otevřete Circle.xaml.cs nebo Circle. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="52ec6-235">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="52ec6-236">V kruhu třídy deklarujte privátní <xref:System.Windows.Media.Brush> proměnnou s názvem `_previousFill` a inicializujte ji na `null`.</span><span class="sxs-lookup"><span data-stu-id="52ec6-236">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. <span data-ttu-id="52ec6-237">Přidejte následující <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání k poskytnutí třídy <xref:System.Windows.UIElement.DragEnter> pro zpracování události.</span><span class="sxs-lookup"><span data-stu-id="52ec6-237">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="52ec6-238">Toto <xref:System.Windows.UIElement.OnDragEnter%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="52ec6-238">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="52ec6-239"><xref:System.Windows.Shapes.Shape.Fill%2A> Uloží vlastnost <xref:System.Windows.Shapes.Ellipse> v proměnné.`_previousFill`</span><span class="sxs-lookup"><span data-stu-id="52ec6-239">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    - <span data-ttu-id="52ec6-240">Provede stejné kontroly, které jsou provedeny v <xref:System.Windows.UIElement.OnDrop%2A> metodě k určení, zda lze data převést <xref:System.Windows.Media.Brush>na.</span><span class="sxs-lookup"><span data-stu-id="52ec6-240">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="52ec6-241">Pokud jsou data převedena na platná <xref:System.Windows.Media.Brush>, aplikuje ji <xref:System.Windows.Shapes.Shape.Fill%2A> na <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-241">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4. <span data-ttu-id="52ec6-242">Přidejte následující <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání k poskytnutí třídy <xref:System.Windows.UIElement.DragLeave> pro zpracování události.</span><span class="sxs-lookup"><span data-stu-id="52ec6-242">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="52ec6-243">Toto <xref:System.Windows.UIElement.OnDragLeave%2A> přepsání provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="52ec6-243">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="52ec6-244">Použije uložené v `_previousFill` proměnnéna<xref:System.Windows.Shapes.Shape.Fill%2A> z ,kterýposkytujeuživatelskérozhraníuživatelskéhoovládacíhoprvkuCircle.<xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Media.Brush></span><span class="sxs-lookup"><span data-stu-id="52ec6-244">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5. <span data-ttu-id="52ec6-245">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="52ec6-245">Press **F5** to build and run the application.</span></span>

6. <span data-ttu-id="52ec6-246">Vyberte text `green` v části <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-246">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="52ec6-247">Přetáhněte text přes ovládací prvek Circle, aniž byste ho museli přetahovat.</span><span class="sxs-lookup"><span data-stu-id="52ec6-247">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="52ec6-248">Kruh se změní z modré na zelenou.</span><span class="sxs-lookup"><span data-stu-id="52ec6-248">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="52ec6-249">![Náhled efektů operace přetažení&#45;&#45;](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="52ec6-249">![Preview the effects of a drag&#45;and&#45;drop operation](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8. <span data-ttu-id="52ec6-250">Přetáhněte text směrem od ovládacího prvku Circle.</span><span class="sxs-lookup"><span data-stu-id="52ec6-250">Drag the text away from the Circle control.</span></span> <span data-ttu-id="52ec6-251">Kruh se změní z zelené na modrou.</span><span class="sxs-lookup"><span data-stu-id="52ec6-251">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="52ec6-252">Povolení panelu pro příjem zahozených dat</span><span class="sxs-lookup"><span data-stu-id="52ec6-252">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="52ec6-253">V této části povolíte panely, které jsou hostiteli uživatelských ovládacích prvků kruh, aby fungovaly jako cíle přetažení pro přetažená data v kruhu.</span><span class="sxs-lookup"><span data-stu-id="52ec6-253">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="52ec6-254">Budete implementovat kód, který umožňuje přesunout kruh z jednoho panelu na jiný, nebo vytvořit kopii ovládacího prvku Circle tak, že podržíte stisknutou klávesu **CTRL** při přetahování a vyřazení kružnice.</span><span class="sxs-lookup"><span data-stu-id="52ec6-254">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1. <span data-ttu-id="52ec6-255">Otevřete MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="52ec6-255">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="52ec6-256">Jak je znázorněno v následujícím kódu XAML, v každém <xref:System.Windows.Controls.StackPanel> z ovládacích prvků přidejte obslužné rutiny <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.DragOver> pro události a.</span><span class="sxs-lookup"><span data-stu-id="52ec6-256">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="52ec6-257">Pojmenujte `panel_DragOver`obslužnou rutinu `panel_Drop` <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.DragOver> události, a pojmenujte obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="52ec6-257">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. <span data-ttu-id="52ec6-258">Otevřete MainWindows.xaml.cs nebo MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="52ec6-258">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4. <span data-ttu-id="52ec6-259">Přidejte následující kód pro <xref:System.Windows.UIElement.DragOver> obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="52ec6-259">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="52ec6-260">Tato <xref:System.Windows.UIElement.DragOver> obslužná rutina události provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="52ec6-260">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="52ec6-261">Kontroluje, zda přetažená data obsahují data "Object", která byla zabalena <xref:System.Windows.DataObject> v uživatelském ovládacím prvku Circle a předaná <xref:System.Windows.DragDrop.DoDragDrop%2A>volání.</span><span class="sxs-lookup"><span data-stu-id="52ec6-261">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    - <span data-ttu-id="52ec6-262">Pokud jsou k dispozici data "objekt", aplikace kontroluje, zda je stisknuta klávesa **CTRL** .</span><span class="sxs-lookup"><span data-stu-id="52ec6-262">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="52ec6-263">Pokud stisknete klávesu **CTRL** , nastaví <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost na <xref:System.Windows.DragDropEffects.Copy>hodnotu.</span><span class="sxs-lookup"><span data-stu-id="52ec6-263">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="52ec6-264">V opačném případě <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost nastavte <xref:System.Windows.DragDropEffects.Move>na.</span><span class="sxs-lookup"><span data-stu-id="52ec6-264">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5. <span data-ttu-id="52ec6-265">Přidejte následující kód pro <xref:System.Windows.UIElement.Drop> obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="52ec6-265">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="52ec6-266">Tato <xref:System.Windows.UIElement.Drop> obslužná rutina události provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="52ec6-266">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="52ec6-267">Kontroluje, zda <xref:System.Windows.UIElement.Drop> událost již byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="52ec6-267">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="52ec6-268">Například pokud je kroužek vyřazen na jiném kruhu, který zpracovává <xref:System.Windows.UIElement.Drop> událost, nechcete, aby byl panel, který obsahuje kroužek, také zpracován.</span><span class="sxs-lookup"><span data-stu-id="52ec6-268">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    - <span data-ttu-id="52ec6-269">Pokud událost není zpracována, aplikace zkontroluje, zda je stisknuta klávesa **CTRL.** <xref:System.Windows.UIElement.Drop></span><span class="sxs-lookup"><span data-stu-id="52ec6-269">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="52ec6-270">Pokud je stisknuta klávesa **CTRL** , <xref:System.Windows.UIElement.Drop> když dojde k tomu, vytvoří kopii ovládacího prvku Circle a <xref:System.Windows.Controls.Panel.Children%2A> přidá jej do kolekce <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="52ec6-270">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    - <span data-ttu-id="52ec6-271">Pokud klávesu **CTRL** nestiskne, přesune kruh z <xref:System.Windows.Controls.Panel.Children%2A> kolekce svého <xref:System.Windows.Controls.Panel.Children%2A> nadřazeného panelu do kolekce panelu, ve kterém byl vyřazen.</span><span class="sxs-lookup"><span data-stu-id="52ec6-271">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    - <span data-ttu-id="52ec6-272">Nastaví vlastnost pro oznamování <xref:System.Windows.DragDrop.DoDragDrop%2A> metody, zda byla provedena operace přesunutí nebo kopírování. <xref:System.Windows.DragEventArgs.Effects%2A></span><span class="sxs-lookup"><span data-stu-id="52ec6-272">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6. <span data-ttu-id="52ec6-273">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="52ec6-273">Press **F5** to build and run the application.</span></span>

7. <span data-ttu-id="52ec6-274">Vyberte text `green` <xref:System.Windows.Controls.TextBox>z.</span><span class="sxs-lookup"><span data-stu-id="52ec6-274">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="52ec6-275">Přetáhněte text přes ovládací prvek kruh a umístěte ho.</span><span class="sxs-lookup"><span data-stu-id="52ec6-275">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="52ec6-276">Přetáhněte ovládací prvek kruh z levého panelu do pravého panelu a přetáhněte ho.</span><span class="sxs-lookup"><span data-stu-id="52ec6-276">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="52ec6-277">Kruh se odebere z <xref:System.Windows.Controls.Panel.Children%2A> kolekce levého panelu a přidá se do kolekce podřízenosti pravého panelu.</span><span class="sxs-lookup"><span data-stu-id="52ec6-277">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="52ec6-278">Přetáhněte ovládací prvek Circle z panelu, na který se nachází, na jiný panel a při stisknutí klávesy **CTRL** ho umístěte.</span><span class="sxs-lookup"><span data-stu-id="52ec6-278">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="52ec6-279">Kruh se zkopíruje a kopie se přidá do <xref:System.Windows.Controls.Panel.Children%2A> kolekce přijímacího panelu.</span><span class="sxs-lookup"><span data-stu-id="52ec6-279">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="52ec6-280">![Přetažení kruhu při stisknutí klávesy CTRL](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="52ec6-280">![Dragging a Circle while pressing the CTRL key](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="52ec6-281">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52ec6-281">See also</span></span>

- [<span data-ttu-id="52ec6-282">Přehled přetažení</span><span class="sxs-lookup"><span data-stu-id="52ec6-282">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
