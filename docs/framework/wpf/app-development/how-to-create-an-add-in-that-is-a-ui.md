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
ms.openlocfilehash: b0e847061a30e93d36997ab603c52715e2730765
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182636"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Postupy: Vytvoření doplňku tvořící uživatelské rozhraní
Tento příklad ukazuje, jak vytvořit doplněk, který je Windows Presentation Foundation (WPF), která je hostována samostatnou aplikací WPF.  
  
 Doplněk je uživatelské rozhraní, které je uživatelským ovládacím prvkem WPF. Obsah uživatelského ovládacího prvku je jediné tlačítko, které po kliknutí zobrazí okno se zprávou. Samostatná aplikace WPF je hostitelem uživatelského rozhraní doplňku jako obsah hlavního okna aplikace.  
  
 **Požadavky**  
  
 Tento příklad zvýrazní rozšíření WPF pro .NET Framework Model doplňku, který umožňuje tento scénář, a předpokládá následující:  
  
- Znalost .NET Frameworkho modelu doplňku, včetně kanálu, doplňku a vývoje hostitele. Pokud tyto koncepty neznáte, přečtěte si téma [Doplňky a rozšiřitelnost](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Kurz, který ukazuje implementaci kanálu, doplňku a hostitelské aplikace, najdete v tématu [Návod: Vytváření rozšiřitelné aplikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))  
  
- Znalosti rozšíření WPF pro .NET Framework Model doplňku. Viz [Přehled doplňků WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit doplněk, který je uživatelským rozhraním WPF, vyžaduje konkrétní kód pro každý segment kanálu, doplněk a hostitelskou aplikaci.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementace segmentu kanálu smluv

Když je doplněk uživatelským rozhraním, kontrakt pro doplněk musí implementovat <xref:System.AddIn.Contract.INativeHandleContract>. V příkladu `IWPFAddInContract` implementuje <xref:System.AddIn.Contract.INativeHandleContract>, jak je znázorněno v následujícím kódu.  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementace segmentu kanálu zobrazení doplňku

Vzhledem k tomu, že doplněk je implementován jako podtřídou <xref:System.Windows.FrameworkElement> typu, zobrazení doplňku musí také podtřídou. <xref:System.Windows.FrameworkElement> Následující kód ukazuje zobrazení smlouvy o doplňku, které je implementováno jako `WPFAddInView` třída.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
Zde je zobrazení doplňku odvozeno z <xref:System.Windows.Controls.UserControl>. V důsledku toho by uživatelské rozhraní doplňku mělo být také <xref:System.Windows.Controls.UserControl>odvozeno z.  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementace segmentu kanálu adaptéru na straně doplňku

I když je <xref:System.AddIn.Contract.INativeHandleContract>kontraktem, doplněk <xref:System.Windows.FrameworkElement> je (jak je určeno segmentem kanálu zobrazení doplňku). Proto je <xref:System.AddIn.Contract.INativeHandleContract> nutné převést na a před vykřížením hranice izolace. <xref:System.Windows.FrameworkElement> Tuto práci provádí adaptér doplňku na straně voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak je znázorněno v následujícím kódu.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

V modelu doplňku, kde doplněk vrátí uživatelské rozhraní (viz téma [Vytvoření doplňku, který vrací uživatelské rozhraní](how-to-create-an-add-in-that-returns-a-ui.md)), adaptér doplňku převedený <xref:System.Windows.FrameworkElement> <xref:System.AddIn.Contract.INativeHandleContract> na volání <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>pomocí. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>musí být také volána v tomto modelu, přestože je nutné implementovat metodu, ze které má být kód zapsán pro volání. Provedete to tak <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> , že přepíšete a <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> implementujete kód, který volá <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> , pokud kód, <xref:System.AddIn.Contract.INativeHandleContract>který je volán, očekává. V takovém případě volající bude adaptér na straně hostitele, který je popsaný v následné části.  
  
> [!NOTE]
> Je také nutné přepsat <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> tento model, aby bylo možné povolit procházení tabulátorem mezi uživatelským rozhraním hostitelské aplikace a uživatelským rozhraním doplňku. Další informace naleznete v tématu "omezení doplňku WPF" v tématu [Doplňky WPF – přehled](wpf-add-ins-overview.md).  
  
Vzhledem k tomu, že adaptér doplňku implementuje rozhraní, které je odvozeno <xref:System.AddIn.Contract.INativeHandleContract>od, je nutné implementovat <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>také, i když je ignorováno <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> , pokud je přepsáno.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementace segmentu kanálu zobrazení hostitele

V tomto modelu hostitelská aplikace obvykle očekává, že zobrazení hostitele bude <xref:System.Windows.FrameworkElement> podtřídou. Adaptér na straně hostitele musí převést <xref:System.AddIn.Contract.INativeHandleContract> na a <xref:System.Windows.FrameworkElement> za <xref:System.AddIn.Contract.INativeHandleContract> překročení hranice izolace. Vzhledem k tomu <xref:System.Windows.FrameworkElement>, že metoda není volána hostitelskou aplikací, aby získala, musí zobrazení hostitele "vracet <xref:System.Windows.FrameworkElement> ", a to tak, že ho obsahuje. V důsledku toho musí být zobrazení hostitele odvozeno od třídy <xref:System.Windows.FrameworkElement> , která může obsahovat jiné uživatelská rozhraní, <xref:System.Windows.Controls.UserControl>například. Následující kód ukazuje zobrazení hostitele kontraktu, implementovaného jako `WPFAddInHostView` třída.  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementace segmentu kanálu adaptéru na straně hostitele

I když je <xref:System.AddIn.Contract.INativeHandleContract>kontraktem, hostitelská aplikace <xref:System.Windows.Controls.UserControl> očekává (jak je určeno zobrazením hostitele). V <xref:System.AddIn.Contract.INativeHandleContract> důsledku toho musí být před nastavením jako <xref:System.Windows.FrameworkElement> obsahu zobrazení hostitele (který je odvozen z <xref:System.Windows.Controls.UserControl>) převedena na a po překročení hranice izolace.  
  
Tato práce je prováděna hostitelským adaptérem, jak je znázorněno v následujícím kódu.  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

Jak vidíte, adaptér na straně hostitele získá <xref:System.AddIn.Contract.INativeHandleContract> volání <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> metody adaptéru doplňku (to je bod, ve kterém se <xref:System.AddIn.Contract.INativeHandleContract> protíná hranice izolace).  
  
Adaptér na straně hostitele pak převede <xref:System.AddIn.Contract.INativeHandleContract> na a <xref:System.Windows.FrameworkElement> voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. <xref:System.Windows.FrameworkElement> Nakonec je nastaven jako obsah zobrazení hostitele.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementace doplňku

S použitím adaptéru doplňku a zobrazení doplňku je možné doplněk implementovat odvozením z zobrazení doplňku, jak je znázorněno v následujícím kódu.  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

V tomto příkladu se můžete podívat na zajímavé výhody tohoto modelu: vývojáři doplňků potřebují jenom implementovat doplněk (protože je to také uživatelské rozhraní), nikoli jak ke třídě doplňku, tak k uživatelskému rozhraní doplňku.  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>Implementace hostitelské aplikace

S vytvořeným hostitelským adaptérem a zobrazením hostitele může hostitelská aplikace použít model doplňku .NET Framework k otevření kanálu a získání zobrazení hostitele doplňku. Tyto kroky jsou uvedeny v následujícím kódu.  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

Hostitelská aplikace používá typický .NET Framework kód modelu doplňku k aktivaci doplňku, který implicitně vrátí zobrazení hostitele na hostitelskou aplikaci. Hostitelská aplikace následně zobrazí zobrazení hostitele (což je a <xref:System.Windows.Controls.UserControl>) <xref:System.Windows.Controls.Grid>z.  
  
 Kód pro zpracování interakcí s uživatelským rozhraním doplňku se spouští v doméně aplikace doplňku. Mezi tyto interakce patří následující:  
  
- Zpracovává se <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost.  
  
- Zobrazuje se <xref:System.Windows.MessageBox>.  
  
 Tato aktivita je zcela izolovaná od hostitelské aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Doplňky a rozšíření](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Přehled doplňků WPF](wpf-add-ins-overview.md)
