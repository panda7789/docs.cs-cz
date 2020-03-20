---
title: 'Postupy: Vytvoření doplňku tvořící uživatelské rozhraní'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: 339231031b9e57b9f00a2aeb6fbbde8ad66c1ad9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141026"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Postupy: Vytvoření doplňku tvořící uživatelské rozhraní
Tento příklad ukazuje, jak vytvořit doplněk, který je Windows Presentation Foundation (WPF), který je hostitelem samostatné aplikace WPF.  
  
 Doplněk je uživatelské rozhraní, které je uživatelským ovládacím prvkem WPF. Obsah uživatelského ovládacího prvku je jediné tlačítko, které po klepnutí zobrazí okno se zprávou. Samostatná aplikace WPF hostuje u hlavního okna aplikace.  
  
 **Požadavky**  
  
 Tento příklad zvýrazní rozšíření WPF k modelu doplňku rozhraní .NET Framework, které tento scénář povolují, a předpokládá následující:  
  
- Znalost modelu doplňku rozhraní .NET Framework, včetně kanálu, doplňku a vývoje hostitele. Pokud tyto koncepty neznáte, přečtěte si informace [o doplňcích a rozšiřitelnosti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Kurz, který ukazuje implementaci kanálu, doplněk a hostitelské aplikace, naleznete v [návodu: Vytvoření rozšiřitelné aplikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- Znalost wpf rozšíření modelu doplňku rozhraní .NET Framework. Viz [Přehled doplňků WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit doplněk, který je WPF uznané vyžaduje konkrétní kód pro každý segment kanálu, doplněk a hostitelské aplikace.  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>Implementace segmentu kanálu smlouvy

Pokud je doplněk ui, musí implementovat <xref:System.AddIn.Contract.INativeHandleContract>kontrakt pro doplněk . V příkladu `IWPFAddInContract` implementuje <xref:System.AddIn.Contract.INativeHandleContract>, jak je znázorněno v následujícím kódu.  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementace segmentu kanálu zobrazení doplňku

Vzhledem k tomu, že doplněk je <xref:System.Windows.FrameworkElement> implementován jako podtřída typu, musí být zobrazení doplňku také podtřídou <xref:System.Windows.FrameworkElement>. Následující kód ukazuje zobrazení doplňku smlouvy, implementované `WPFAddInView` jako třída.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
Zde je zobrazení doplňku odvozeno <xref:System.Windows.Controls.UserControl>od . V důsledku toho by mělo být odvozeno také <xref:System.Windows.Controls.UserControl>z .  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementace segmentu kanálu adaptéru na straně doplňku

Zatímco smlouva je <xref:System.AddIn.Contract.INativeHandleContract>, doplněk je <xref:System.Windows.FrameworkElement> (jak je určeno segmentu kanálu zobrazení doplňku). Proto <xref:System.Windows.FrameworkElement> musí být převedeny <xref:System.AddIn.Contract.INativeHandleContract> na před překročení hranice izolace. Tuto práci provádí adaptér na straně doplňku <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>voláním , jak je znázorněno v následujícím kódu.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

V modelu doplňku, kde doplněk vrátí ui (viz [Vytvoření doplňku, který vrací uI](how-to-create-an-add-in-that-returns-a-ui.md)), adaptér <xref:System.Windows.FrameworkElement> doplňku převedenna <xref:System.AddIn.Contract.INativeHandleContract> voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>musí být také volána v tomto modelu, i když je třeba implementovat metodu, ze které chcete napsat kód volat. Provedete to <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> přepsáním a implementací kódu, který volá, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> pokud kód, který volá, <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> očekává . <xref:System.AddIn.Contract.INativeHandleContract> V takovém případě bude volající adaptér na straně hostitele, který je popsán v následující podčásti.  
  
> [!NOTE]
> Musíte také přepsat <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> v tomto modelu povolit tabulátory mezi uzdu hostitelské aplikace a ui doplňku. Další informace naleznete v části "Omezení doplňku WPF" v [přehledu doplňků WPF](wpf-add-ins-overview.md).  
  
Vzhledem k tomu, že adaptér doplňku implementuje rozhraní, které je odvozeno z <xref:System.AddIn.Contract.INativeHandleContract>aplikace , je také nutné implementovat <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, i když je to ignorováno, když <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> je přepsán.  
  
<a name="HostViewPipeline"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementace segmentu kanálu zobrazení hostitele

V tomto modelu hostitelské aplikace obvykle očekává, že <xref:System.Windows.FrameworkElement> zobrazení hostitele je podtřída. Adaptér na straně hostitele <xref:System.AddIn.Contract.INativeHandleContract> musí <xref:System.Windows.FrameworkElement> převést <xref:System.AddIn.Contract.INativeHandleContract> na po protíná hranice izolace. Vzhledem k tomu, že metoda není volána hostitelskou aplikací k získání <xref:System.Windows.FrameworkElement>, musí zobrazení hostitele "vrátit" <xref:System.Windows.FrameworkElement> tím, že ji bude obsahovat. V důsledku toho musí hostitelské zobrazení <xref:System.Windows.FrameworkElement> vycházet z podtřídy, <xref:System.Windows.Controls.UserControl>která může obsahovat jiná ucína, například . Následující kód zobrazuje zobrazení hostitele smlouvy, implementované jako `WPFAddInHostView` třída.  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementace segmentu kanálu adaptéru na straně hostitele

Zatímco smlouva je <xref:System.AddIn.Contract.INativeHandleContract>, hostitelská aplikace <xref:System.Windows.Controls.UserControl> očekává (jak je určeno zobrazení hostitele). V důsledku <xref:System.AddIn.Contract.INativeHandleContract> toho musí být <xref:System.Windows.FrameworkElement> převedena na po překročení hranice izolace, před nastavením jako <xref:System.Windows.Controls.UserControl>obsah zobrazení hostitele (který pochází z ).  
  
Tato práce je prováděna adaptérem na straně hostitele, jak je znázorněno v následujícím kódu.  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

Jak můžete vidět, adaptér na straně <xref:System.AddIn.Contract.INativeHandleContract> hostitele získá voláním metody adaptéru <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> na straně přídavku <xref:System.AddIn.Contract.INativeHandleContract> (toto je bod, kde překračuje hranice izolace).  
  
Adaptér na straně hostitele pak <xref:System.AddIn.Contract.INativeHandleContract> převede na <xref:System.Windows.FrameworkElement> volání <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Nakonec <xref:System.Windows.FrameworkElement> je nastaven jako obsah zobrazení hostitele.  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>Implementace doplňku

S adaptérem na straně doplňku a zobrazení doplňku na místě doplněk lze implementovat odvozením z zobrazení doplňku, jak je znázorněno v následujícím kódu.  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

Z tohoto příkladu můžete vidět jednu zajímavou výhodu tohoto modelu: vývojáři doplňku potřebují pouze implementovat doplněk (protože je také uj. u.), nikoli třídu doplňku a uhlavní ho.  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>Implementace hostitelské aplikace

Při vytvoření adaptéru na straně hostitele a zobrazení hostitele může hostitelská aplikace použít model doplňku rozhraní .NET Framework k otevření kanálu a získání zobrazení hostitele doplňku. Tyto kroky jsou uvedeny v následujícím kódu.  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

Hostitelská aplikace používá typický kód modelu doplňku rozhraní .NET Framework k aktivaci doplňku, který implicitně vrací zobrazení hostitele hostitelské aplikaci. Hostitelská aplikace následně zobrazí zobrazení hostitele <xref:System.Windows.Controls.UserControl>(což <xref:System.Windows.Controls.Grid>je ) z .  
  
 Kód pro zpracování interakcí s předpojatého uživatele spouští v doméně aplikace doplňku. Mezi tyto interakce patří následující:  
  
- <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Zpracování události.  
  
- Zobrazení <xref:System.Windows.MessageBox>.  
  
 Tato aktivita je zcela izolována od hostitelské aplikace.  
  
## <a name="see-also"></a>Viz také

- [Doplňky a rozšíření](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Přehled doplňků WPF](wpf-add-ins-overview.md)
