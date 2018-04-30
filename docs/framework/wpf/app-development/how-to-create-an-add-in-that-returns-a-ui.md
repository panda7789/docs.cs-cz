---
title: 'Postupy: Vytvoření doplňku, který vrací uživatelské rozhraní'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e89cb9d0c8e5a26703ff5f56a3af10d7fe9923f
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="81117-102">Postupy: Vytvoření doplňku, který vrací uživatelské rozhraní</span><span class="sxs-lookup"><span data-stu-id="81117-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="81117-103">Tento příklad ukazuje, jak vytvořit doplněk, který vrací Windows Presentation Foundation (WPF) na hostitele [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] samostatné aplikace.</span><span class="sxs-lookup"><span data-stu-id="81117-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application.</span></span>  
  
 <span data-ttu-id="81117-104">Doplněk vrátí [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tedy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="81117-104">The add-in returns a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that is a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] user control.</span></span> <span data-ttu-id="81117-105">Obsah uživatelského ovládacího prvku je jedné tlačítko, která po kliknutí na zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="81117-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="81117-106">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Samostatné aplikace hostuje doplněk a zobrazí uživatelského ovládacího prvku (vrácený doplněk) jako obsah hlavního okna aplikace.</span><span class="sxs-lookup"><span data-stu-id="81117-106">The [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="81117-107">**Požadavky**</span><span class="sxs-lookup"><span data-stu-id="81117-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="81117-108">Tento příklad klade důraz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšíření [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu, který povolit tento scénář a předpokládá následující:</span><span class="sxs-lookup"><span data-stu-id="81117-108">This example highlights the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model that enable this scenario, and assumes the following:</span></span>  
  
-   <span data-ttu-id="81117-109">Znalost [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku modelu, včetně kanálu, doplňku a vývoj hostitele.</span><span class="sxs-lookup"><span data-stu-id="81117-109">Knowledge of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="81117-110">Pokud jste obeznámeni s následujícími základními pojmy, najdete v části [doplňky a rozšíření](../../../../docs/framework/add-ins/index.md).</span><span class="sxs-lookup"><span data-stu-id="81117-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](../../../../docs/framework/add-ins/index.md).</span></span> <span data-ttu-id="81117-111">Kurz, který ukazuje implementaci kanál, -v a hostitelskou aplikaci, najdete v části [návod: vytváření rozšiřitelné aplikace](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span><span class="sxs-lookup"><span data-stu-id="81117-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
-   <span data-ttu-id="81117-112">Znalosti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšíření [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku model, který se nachází tady: [WPF doplňky přehled](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="81117-112">Knowledge of the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, which can be found here: [WPF Add-Ins Overview](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81117-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="81117-113">Example</span></span>  
 <span data-ttu-id="81117-114">Chcete-li vytvořit doplněk, který vrací [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vyžaduje konkrétní kód pro každý segment kanálu v doplňku a hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="81117-114">To create an add-in that returns a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="81117-115">Implementace segmentu kanálu kontraktu</span><span class="sxs-lookup"><span data-stu-id="81117-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="81117-116">Metoda musí být definován ve smlouvě pro návrat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], a hodnoty musí být typu <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="81117-116">A method must be defined by the contract for returning a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="81117-117">Tento postup je znázorněn pomocí `GetAddInUI` metodu `IWPFAddInContract` smlouvy v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="81117-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="81117-118">Implementace segmentu kanál doplňku zobrazení</span><span class="sxs-lookup"><span data-stu-id="81117-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="81117-119">Protože doplněk implementuje [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] poskytuje jako měly podtřídy <xref:System.Windows.FrameworkElement>, metoda pro zobrazení pro `IWPFAddInView.GetAddInUI` musí vracet hodnoty typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="81117-119">Because the add-in implements the [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="81117-120">Následující kód ukazuje zobrazení přidat smlouvy, které jsou implementované jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81117-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="81117-121">Implementace segmentu kanálu přidat straně adaptéru</span><span class="sxs-lookup"><span data-stu-id="81117-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="81117-122">Vrátí metoda kontraktu <xref:System.AddIn.Contract.INativeHandleContract>, ale doplněk vrací <xref:System.Windows.FrameworkElement> (jak je uvedeno v zobrazení).</span><span class="sxs-lookup"><span data-stu-id="81117-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="81117-123">V důsledku toho <xref:System.Windows.FrameworkElement> musí být převedena na <xref:System.AddIn.Contract.INativeHandleContract> před překračuje hranice izolace.</span><span class="sxs-lookup"><span data-stu-id="81117-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="81117-124">Tento pracovní provádí adaptér přidat straně voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="81117-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="81117-125">Implementace segmentu hostitele zobrazení kanálu</span><span class="sxs-lookup"><span data-stu-id="81117-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="81117-126">Protože hostitelskou aplikaci se zobrazí <xref:System.Windows.FrameworkElement>, metoda pro zobrazení hostitele, které odpovídá `IWPFAddInHostView.GetAddInUI` musí vracet hodnoty typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="81117-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="81117-127">Následující kód ukazuje hostitelském zobrazení smlouvy, které jsou implementované jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81117-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="81117-128">Implementace segmentu adaptér hostitelské kanálu</span><span class="sxs-lookup"><span data-stu-id="81117-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="81117-129">Vrátí metodu kontraktu <xref:System.AddIn.Contract.INativeHandleContract>, ale očekává hostitelskou aplikaci <xref:System.Windows.FrameworkElement> (jak je uvedeno v zobrazení hostitele).</span><span class="sxs-lookup"><span data-stu-id="81117-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="81117-130">V důsledku toho <xref:System.AddIn.Contract.INativeHandleContract> musí být převedena na <xref:System.Windows.FrameworkElement> po překročení meze hranice izolace.</span><span class="sxs-lookup"><span data-stu-id="81117-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="81117-131">Tento pracovní provádí adaptér hostitelské voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="81117-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="81117-132">Implementace v aplikaci</span><span class="sxs-lookup"><span data-stu-id="81117-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="81117-133">Přidat straně adaptéru a doplněk zobrazení vytvořené, doplněk (`WPFAddIn1.AddIn`) musí implementovat `IWPFAddInView.GetAddInUI` metoda vrátí <xref:System.Windows.FrameworkElement> objekt ( <xref:System.Windows.Controls.UserControl> v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="81117-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="81117-134">Implementace <xref:System.Windows.Controls.UserControl>, `AddInUI`, je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="81117-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="81117-135">Implementace `IWPFAddInView.GetAddInUI` pomocí doplňku jednoduše musí vrátit novou instanci třídy `AddInUI`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="81117-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="81117-136">Implementace aplikace pro hostitele</span><span class="sxs-lookup"><span data-stu-id="81117-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="81117-137">Adaptér hostitelské a hostitele zobrazení vytvořené hostitelskou aplikaci pomocí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model doplňku otevřít kanál, získat zobrazení hostitele add-in a volání `IWPFAddInHostView.GetAddInUI` metoda.</span><span class="sxs-lookup"><span data-stu-id="81117-137">With the host-side adapter and host view created, the host application can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="81117-138">Tyto kroky jsou uvedeny v následující kód.</span><span class="sxs-lookup"><span data-stu-id="81117-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="81117-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="81117-139">See Also</span></span>  
 [<span data-ttu-id="81117-140">Doplňky a rozšíření</span><span class="sxs-lookup"><span data-stu-id="81117-140">Add-ins and Extensibility</span></span>](../../../../docs/framework/add-ins/index.md)  
 [<span data-ttu-id="81117-141">Přehled doplňků WPF</span><span class="sxs-lookup"><span data-stu-id="81117-141">WPF Add-Ins Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
