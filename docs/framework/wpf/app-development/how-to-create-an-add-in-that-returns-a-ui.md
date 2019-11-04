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
ms.openlocfilehash: d799c91b9abdf7882a0fcd3f0b656eac553b188c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460155"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="64098-102">Postupy: Vytvoření doplňku, který vrací uživatelské rozhraní</span><span class="sxs-lookup"><span data-stu-id="64098-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="64098-103">Tento příklad ukazuje, jak vytvořit doplněk, který vrací Windows Presentation Foundation (WPF) do samostatné aplikace hostitele WPF.</span><span class="sxs-lookup"><span data-stu-id="64098-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="64098-104">Doplněk vrátí uživatelské rozhraní, které je uživatelským ovládacím prvkem WPF.</span><span class="sxs-lookup"><span data-stu-id="64098-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="64098-105">Obsah uživatelského ovládacího prvku je jediné tlačítko, které po kliknutí zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="64098-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="64098-106">Samostatná aplikace WPF je hostitelem doplňku a zobrazuje uživatelský ovládací prvek (vrácený doplňkem) jako obsah okna hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="64098-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="64098-107">**Požadovaný**</span><span class="sxs-lookup"><span data-stu-id="64098-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="64098-108">Tento příklad zvýrazní rozšíření WPF pro .NET Framework Model doplňku, který umožňuje tento scénář, a předpokládá následující:</span><span class="sxs-lookup"><span data-stu-id="64098-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="64098-109">Znalost .NET Frameworkho modelu doplňku, včetně kanálu, doplňku a vývoje hostitele.</span><span class="sxs-lookup"><span data-stu-id="64098-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="64098-110">Pokud tyto koncepty neznáte, přečtěte si téma [Doplňky a rozšiřitelnost](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="64098-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="64098-111">Kurz, který ukazuje implementaci kanálu, doplňku a hostitelské aplikace, najdete v tématu [Návod: vytváření rozšiřitelné aplikace](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="64098-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span></span>  
  
- <span data-ttu-id="64098-112">Znalosti rozšíření WPF pro .NET Framework Model doplňku, který najdete tady: [Přehled doplňků WPF](wpf-add-ins-overview.md)</span><span class="sxs-lookup"><span data-stu-id="64098-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64098-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="64098-113">Example</span></span>  
 <span data-ttu-id="64098-114">Pro vytvoření doplňku, který vrací uživatelské rozhraní WPF, je nutné zadat konkrétní kód pro každý segment kanálu, doplněk a hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="64098-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="64098-115">Implementace segmentu kanálu smluv</span><span class="sxs-lookup"><span data-stu-id="64098-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="64098-116">Metoda musí být definována kontraktem pro vrácení uživatelského rozhraní a vrácená hodnota musí být typu <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="64098-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="64098-117">To je ukázáno metodou `GetAddInUI` kontraktu `IWPFAddInContract` v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="64098-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="64098-118">Implementace segmentu kanálu zobrazení doplňku</span><span class="sxs-lookup"><span data-stu-id="64098-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="64098-119">Vzhledem k tomu, že doplněk implementuje uživatelská rozhraní, který poskytuje jako podtřídy <xref:System.Windows.FrameworkElement>, metoda v zobrazení doplňku, která koreluje s `IWPFAddInView.GetAddInUI` musí vracet hodnotu typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="64098-119">Because the add-in implements the UIs it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="64098-120">Následující kód ukazuje zobrazení smlouvy o doplňku, které je implementováno jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64098-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="64098-121">Implementace segmentu kanálu adaptéru na straně doplňku</span><span class="sxs-lookup"><span data-stu-id="64098-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="64098-122">Metoda kontraktu vrátí <xref:System.AddIn.Contract.INativeHandleContract>, ale doplněk vrátí <xref:System.Windows.FrameworkElement> (jak je uvedeno v zobrazení doplňku).</span><span class="sxs-lookup"><span data-stu-id="64098-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="64098-123">V důsledku toho musí být <xref:System.Windows.FrameworkElement> převedena na <xref:System.AddIn.Contract.INativeHandleContract> před překročením hranice izolace.</span><span class="sxs-lookup"><span data-stu-id="64098-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="64098-124">Tato práce se provádí pomocí adaptéru doplňku na straně voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="64098-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="64098-125">Implementace segmentu kanálu zobrazení hostitele</span><span class="sxs-lookup"><span data-stu-id="64098-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="64098-126">Protože hostitelská aplikace zobrazí <xref:System.Windows.FrameworkElement>, metoda v zobrazení hostitele, která koreluje s `IWPFAddInHostView.GetAddInUI`, musí vracet hodnotu typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="64098-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="64098-127">Následující kód ukazuje zobrazení hostitele kontraktu, implementované jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64098-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="64098-128">Implementace segmentu kanálu adaptéru na straně hostitele</span><span class="sxs-lookup"><span data-stu-id="64098-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="64098-129">Metoda kontraktu vrací <xref:System.AddIn.Contract.INativeHandleContract>, ale hostitelská aplikace očekává <xref:System.Windows.FrameworkElement> (jak je uvedeno v zobrazení hostitele).</span><span class="sxs-lookup"><span data-stu-id="64098-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="64098-130">V důsledku toho musí být <xref:System.AddIn.Contract.INativeHandleContract> převedena na <xref:System.Windows.FrameworkElement> po překročení hranice izolace.</span><span class="sxs-lookup"><span data-stu-id="64098-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="64098-131">Tuto práci provádí hostitelský adaptér na straně hostitele voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="64098-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="64098-132">Implementace doplňku</span><span class="sxs-lookup"><span data-stu-id="64098-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="64098-133">Když je vytvořen adaptér doplňku a zobrazení doplňku, musí doplněk (`WPFAddIn1.AddIn`) implementovat metodu `IWPFAddInView.GetAddInUI` pro vrácení objektu <xref:System.Windows.FrameworkElement> (v tomto příkladu <xref:System.Windows.Controls.UserControl>).</span><span class="sxs-lookup"><span data-stu-id="64098-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="64098-134">Implementace <xref:System.Windows.Controls.UserControl>, `AddInUI`, je zobrazena v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="64098-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="64098-135">Implementace `IWPFAddInView.GetAddInUI` pomocí doplňku jednoduše potřebuje vrátit novou instanci `AddInUI`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="64098-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="64098-136">Implementace hostitelské aplikace</span><span class="sxs-lookup"><span data-stu-id="64098-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="64098-137">S vytvořeným hostitelským adaptérem a zobrazením hostitele může hostitelská aplikace použít model doplňku .NET Framework k otevření kanálu, získání zobrazení hostitele doplňku a volání metody `IWPFAddInHostView.GetAddInUI`.</span><span class="sxs-lookup"><span data-stu-id="64098-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="64098-138">Tyto kroky jsou uvedeny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="64098-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="64098-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64098-139">See also</span></span>

- <span data-ttu-id="64098-140">[Doplňky a rozšíření](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="64098-140">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="64098-141">Přehled doplňků WPF</span><span class="sxs-lookup"><span data-stu-id="64098-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
