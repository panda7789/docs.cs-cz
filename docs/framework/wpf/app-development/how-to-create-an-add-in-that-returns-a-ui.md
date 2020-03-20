---
title: 'Postupy: Vytvoření doplňku, který vrací uživatelské rozhraní'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: f8323fe35555a56d39c1efed649c2aa3fcf17e43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174586"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="4e3c6-102">Postupy: Vytvoření doplňku, který vrací uživatelské rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e3c6-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="4e3c6-103">Tento příklad ukazuje, jak vytvořit doplněk, který vrací Windows Presentation Foundation (WPF) do samostatné aplikace WPF hostitele.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="4e3c6-104">Doplněk vrátí uživatelské rozhraní, které je uživatelský mj.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="4e3c6-105">Obsah uživatelského ovládacího prvku je jediné tlačítko, které po klepnutí zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="4e3c6-106">Samostatná aplikace WPF hostuje doplněk a zobrazuje uživatelský ovládací prvek (vrácený doplňkem) jako obsah hlavního okna aplikace.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="4e3c6-107">**Požadavky**</span><span class="sxs-lookup"><span data-stu-id="4e3c6-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="4e3c6-108">Tento příklad zvýrazní rozšíření WPF k modelu doplňku rozhraní .NET Framework, které tento scénář povolují, a předpokládá následující:</span><span class="sxs-lookup"><span data-stu-id="4e3c6-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="4e3c6-109">Znalost modelu doplňku rozhraní .NET Framework, včetně kanálu, doplňku a vývoje hostitele.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="4e3c6-110">Pokud tyto koncepty neznáte, přečtěte si informace [o doplňcích a rozšiřitelnosti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="4e3c6-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="4e3c6-111">Kurz, který ukazuje implementaci kanálu, doplněk a hostitelské aplikace, naleznete v [návodu: Vytvoření rozšiřitelné aplikace](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="4e3c6-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span></span>  
  
- <span data-ttu-id="4e3c6-112">Znalost wpf rozšíření modelu doplňku rozhraní .NET Framework, které lze nalézt zde: [WPF Doplňky Přehled](wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4e3c6-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e3c6-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e3c6-113">Example</span></span>  
 <span data-ttu-id="4e3c6-114">Chcete-li vytvořit doplněk, který vrací WPF ui vyžaduje konkrétní kód pro každý segment kanálu, doplněk a hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="4e3c6-115">Implementace segmentu kanálu smlouvy</span><span class="sxs-lookup"><span data-stu-id="4e3c6-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="4e3c6-116">Metoda musí být definována smlouvou pro vrácení ui a jeho <xref:System.AddIn.Contract.INativeHandleContract>vrácená hodnota musí být typu .</span><span class="sxs-lookup"><span data-stu-id="4e3c6-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="4e3c6-117">To je prokázáno `GetAddInUI` metodou `IWPFAddInContract` smlouvy v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="4e3c6-118">Implementace segmentu kanálu zobrazení doplňku</span><span class="sxs-lookup"><span data-stu-id="4e3c6-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="4e3c6-119">Vzhledem k tomu, že doplněk implementuje <xref:System.Windows.FrameworkElement>ui poskytuje jako podtřídy , metoda `IWPFAddInView.GetAddInUI` v zobrazení doplňku, který koreluje s musí vrátit hodnotu typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-119">Because the add-in implements the UIs it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="4e3c6-120">Následující kód ukazuje zobrazení doplňku smlouvy, implementované jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="4e3c6-121">Implementace segmentu kanálu adaptéru na straně doplňku</span><span class="sxs-lookup"><span data-stu-id="4e3c6-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="4e3c6-122">Metoda smlouvy vrátí <xref:System.AddIn.Contract.INativeHandleContract>, ale doplněk vrátí <xref:System.Windows.FrameworkElement> (jak je určeno zobrazení doplňku).</span><span class="sxs-lookup"><span data-stu-id="4e3c6-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="4e3c6-123">V důsledku <xref:System.Windows.FrameworkElement> toho musí být <xref:System.AddIn.Contract.INativeHandleContract> převedena na před překročení hranice izolace.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="4e3c6-124">Tuto práci provádí adaptér na straně doplňku <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>voláním , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="4e3c6-125">Implementace segmentu kanálu zobrazení hostitele</span><span class="sxs-lookup"><span data-stu-id="4e3c6-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="4e3c6-126">Vzhledem k tomu, <xref:System.Windows.FrameworkElement>že hostitelská aplikace zobrazí , `IWPFAddInHostView.GetAddInUI` metoda v zobrazení <xref:System.Windows.FrameworkElement>hostitele, která koreluje s musí vrátit hodnotu typu .</span><span class="sxs-lookup"><span data-stu-id="4e3c6-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="4e3c6-127">Následující kód zobrazuje zobrazení hostitele smlouvy, implementované jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="4e3c6-128">Implementace segmentu kanálu adaptéru na straně hostitele</span><span class="sxs-lookup"><span data-stu-id="4e3c6-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="4e3c6-129">Metoda smlouvy vrátí <xref:System.AddIn.Contract.INativeHandleContract>, ale hostitelská <xref:System.Windows.FrameworkElement> aplikace očekává (jak je určeno zobrazení hostitele).</span><span class="sxs-lookup"><span data-stu-id="4e3c6-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="4e3c6-130">V důsledku <xref:System.AddIn.Contract.INativeHandleContract> toho musí být <xref:System.Windows.FrameworkElement> převedena na po překročení hranice izolace.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="4e3c6-131">Tato práce je prováděna adaptérem <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>na straně hostitele voláním , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a><span data-ttu-id="4e3c6-132">Implementace doplňku</span><span class="sxs-lookup"><span data-stu-id="4e3c6-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="4e3c6-133">Při vytvoření adaptéru na straně a zobrazení doplňku musí`WPFAddIn1.AddIn`doplněk ( `IWPFAddInView.GetAddInUI` ) implementovat <xref:System.Windows.FrameworkElement> metodu <xref:System.Windows.Controls.UserControl> pro vrácení objektu (a v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="4e3c6-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="4e3c6-134">Implementace <xref:System.Windows.Controls.UserControl>, `AddInUI`, je zobrazena v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="4e3c6-135">Implementace `IWPFAddInView.GetAddInUI` doplňku jednoduše potřebuje vrátit novou instanci `AddInUI`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>
## <a name="implementing-the-host-application"></a><span data-ttu-id="4e3c6-136">Implementace hostitelské aplikace</span><span class="sxs-lookup"><span data-stu-id="4e3c6-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="4e3c6-137">Při vytvoření adaptéru na straně hostitele a zobrazení hostitele může hostitelská aplikace použít model doplňku rozhraní .NET Framework k `IWPFAddInHostView.GetAddInUI` otevření kanálu, získání zobrazení hostitele doplňku a volání metody.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="4e3c6-138">Tyto kroky jsou uvedeny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4e3c6-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="4e3c6-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e3c6-139">See also</span></span>

- <span data-ttu-id="4e3c6-140">[Doplňky a rozšíření](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="4e3c6-140">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="4e3c6-141">Přehled doplňků WPF</span><span class="sxs-lookup"><span data-stu-id="4e3c6-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
