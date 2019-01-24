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
ms.openlocfilehash: 0c7a91a53a16012340b5612e19255dfd2f2bad85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654084"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="a15f9-102">Postupy: Vytvoření doplňku, který vrací uživatelské rozhraní</span><span class="sxs-lookup"><span data-stu-id="a15f9-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="a15f9-103">Tento příklad ukazuje, jak vytvořit doplněk, který vrací Windows Presentation Foundation (WPF) do hostitele samostatnou aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="a15f9-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="a15f9-104">Doplněk vrací uživatelské rozhraní, která je uživatelský ovládací prvek WPF.</span><span class="sxs-lookup"><span data-stu-id="a15f9-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="a15f9-105">Obsah uživatelský ovládací prvek je jediné tlačítko, které, při kliknutí zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="a15f9-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="a15f9-106">Samostatná aplikace WPF hostuje doplněk a zobrazuje uživatelský ovládací prvek (vráceným metodou doplněk) jako obsah hlavního okna aplikace.</span><span class="sxs-lookup"><span data-stu-id="a15f9-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="a15f9-107">**Požadavky**</span><span class="sxs-lookup"><span data-stu-id="a15f9-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="a15f9-108">V tomto příkladu zvýrazní WPF rozšíření modelu doplňku rozhraní .NET Framework, které umožňují tento scénář a předpokládá následující:</span><span class="sxs-lookup"><span data-stu-id="a15f9-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
-   <span data-ttu-id="a15f9-109">Znalost modelu rozhraní .NET Framework – doplněk, včetně kanálu doplňku a vývoj pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="a15f9-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="a15f9-110">Pokud nejste obeznámeni s tyto koncepty, najdete v článku [doplňků a rozšíření](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="a15f9-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="a15f9-111">Kurz, který ukazuje implementaci kanálu, doplněk a hostitelskou aplikací, najdete v tématu [názorný postup: Vytváření rozšiřitelné aplikace](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span><span class="sxs-lookup"><span data-stu-id="a15f9-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
-   <span data-ttu-id="a15f9-112">Informace o rozšíření WPF rozhraní .NET Framework model doplňku, který najdete tady: [Přehled doplňků WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a15f9-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a15f9-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="a15f9-113">Example</span></span>  
 <span data-ttu-id="a15f9-114">K vytvoření doplňku, který vrací uživatelské rozhraní WPF vyžaduje konkrétní kód pro každý segment kanálu doplňku a hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a15f9-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="a15f9-115">Implementace kontraktu Segment kanálu</span><span class="sxs-lookup"><span data-stu-id="a15f9-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="a15f9-116">Metoda musí být definován ve smlouvě vrací uživatelské rozhraní a vrácená hodnota musí být typu <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="a15f9-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="a15f9-117">To je patrné podle `GetAddInUI` metodu `IWPFAddInContract` smlouvy v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a15f9-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="a15f9-118">Implementace segmentu kanálu doplňku zobrazení</span><span class="sxs-lookup"><span data-stu-id="a15f9-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="a15f9-119">Protože doplněk implementuje [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] poskytuje jako podtřídy třídy <xref:System.Windows.FrameworkElement>, metoda pro zobrazení, které souvisí s `IWPFAddInView.GetAddInUI` musí vracet hodnotu typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="a15f9-119">Because the add-in implements the [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="a15f9-120">Následující kód ukazuje zobrazení přidat smlouvy, které jsou implementovány jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a15f9-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="a15f9-121">Implementace segmentu přidat v-adaptér na straně kanálu</span><span class="sxs-lookup"><span data-stu-id="a15f9-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="a15f9-122">Vrátí metoda smlouvy <xref:System.AddIn.Contract.INativeHandleContract>, ale doplněk vrátí <xref:System.Windows.FrameworkElement> (jak je uvedeno v zobrazení).</span><span class="sxs-lookup"><span data-stu-id="a15f9-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="a15f9-123">V důsledku toho <xref:System.Windows.FrameworkElement> musejí být převedeny do <xref:System.AddIn.Contract.INativeHandleContract> před překročení hranice izolace.</span><span class="sxs-lookup"><span data-stu-id="a15f9-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="a15f9-124">Tuto práci provádí adaptér přidat v na straně voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a15f9-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="a15f9-125">Implementace segmentu hostitele zobrazení kanálu</span><span class="sxs-lookup"><span data-stu-id="a15f9-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="a15f9-126">Protože hostitelská aplikace se zobrazí <xref:System.Windows.FrameworkElement>, metoda v hostitelském zobrazení, které souvisí s `IWPFAddInHostView.GetAddInUI` musí vracet hodnotu typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="a15f9-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="a15f9-127">Následující kód zobrazuje hostitele kontraktu implementováno jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a15f9-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="a15f9-128">Implementace segmentu kanálu adaptér na straně hostitele</span><span class="sxs-lookup"><span data-stu-id="a15f9-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="a15f9-129">Vrátí metodu smlouvy <xref:System.AddIn.Contract.INativeHandleContract>, ale hostitelská aplikace očekává, že <xref:System.Windows.FrameworkElement> (jak je uvedeno v hostitelském zobrazení).</span><span class="sxs-lookup"><span data-stu-id="a15f9-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="a15f9-130">V důsledku toho <xref:System.AddIn.Contract.INativeHandleContract> musí být převeden do <xref:System.Windows.FrameworkElement> po překročení hranice izolace.</span><span class="sxs-lookup"><span data-stu-id="a15f9-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="a15f9-131">Tato práce se provádí pomocí adaptéru hostitelské voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a15f9-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="a15f9-132">Implementace doplňku pro</span><span class="sxs-lookup"><span data-stu-id="a15f9-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="a15f9-133">Adaptér přidat v na straně a doplňku zobrazení vytvořené, doplněk (`WPFAddIn1.AddIn`) musí implementovat `IWPFAddInView.GetAddInUI` metodu pro návrat <xref:System.Windows.FrameworkElement> objekt ( <xref:System.Windows.Controls.UserControl> v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="a15f9-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="a15f9-134">Provádění <xref:System.Windows.Controls.UserControl>, `AddInUI`, je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a15f9-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="a15f9-135">Provádění `IWPFAddInView.GetAddInUI` pomocí doplňku jednoduše musí vracet novou instanci třídy `AddInUI`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a15f9-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="a15f9-136">Implementace hostitele aplikace</span><span class="sxs-lookup"><span data-stu-id="a15f9-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="a15f9-137">Adaptér na straně hostitele a hostitele zobrazení vytvořené hostitelská aplikace pomocí modelu doplňku rozhraní .NET Framework na Otevřít kanál, získat zobrazení hostitele doplňku a volání `IWPFAddInHostView.GetAddInUI` metody.</span><span class="sxs-lookup"><span data-stu-id="a15f9-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="a15f9-138">Tyto kroky jsou uvedeny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a15f9-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="a15f9-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a15f9-139">See also</span></span>
- <span data-ttu-id="a15f9-140">[Doplňky a rozšíření](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="a15f9-140">[Add-ins and Extensibility](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="a15f9-141">Přehled doplňků WPF</span><span class="sxs-lookup"><span data-stu-id="a15f9-141">WPF Add-Ins Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
