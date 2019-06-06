---
title: 'Postupy: Vytvoření doplňku, který je uživatelským rozhraním'
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
ms.openlocfilehash: b0213ddfd8197ffabcbeb1cd5fc78e517920b8fe
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690447"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Postupy: Vytvoření doplňku, který je uživatelským rozhraním
Tento příklad ukazuje, jak vytvořit doplněk, který je Windows Presentation Foundation (WPF) pomocí samostatné aplikace WPF hostované.  
  
 Doplněk je uživatelské rozhraní, která je uživatelský ovládací prvek WPF. Obsah uživatelský ovládací prvek je jediné tlačítko, které, při kliknutí zobrazí okno se zprávou. Samostatná aplikace WPF hostitelem uživatelského rozhraní doplňku jako obsah hlavního okna aplikace.  
  
 **Požadavky**  
  
 V tomto příkladu zvýrazní WPF rozšíření modelu doplňku rozhraní .NET Framework, které umožňují tento scénář a předpokládá následující:  
  
- Znalost modelu rozhraní .NET Framework – doplněk, včetně kanálu doplňku a vývoj pro hostitele. Pokud nejste obeznámeni s tyto koncepty, najdete v článku [doplňků a rozšíření](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Kurz, který ukazuje implementaci kanálu, doplněk a hostitelskou aplikací, najdete v tématu [názorný postup: Vytváření rozšiřitelné aplikace](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- Znalost rozšíření WPF k modelu doplňku rozhraní .NET Framework. Zobrazit [přehled doplňků WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Příklad  
 K vytvoření doplňku tvořící uživatelské rozhraní WPF vyžaduje konkrétní kód pro každý segment kanálu doplňku a hostitelskou aplikaci.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementace kontraktu Segment kanálu

Když doplňkem uživatelského rozhraní, musí implementovat kontrakt pro doplněk <xref:System.AddIn.Contract.INativeHandleContract>. V tomto příkladu `IWPFAddInContract` implementuje <xref:System.AddIn.Contract.INativeHandleContract>, jak je znázorněno v následujícím kódu.  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementace segmentu kanálu doplňku zobrazení

Protože doplněk je implementovaný jako podtřída <xref:System.Windows.FrameworkElement> typ zobrazení doplňku, musí taky podtřídy <xref:System.Windows.FrameworkElement>. Následující kód ukazuje zobrazení přidat smlouvy, které jsou implementovány jako `WPFAddInView` třídy.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
Zde je zobrazení doplňku odvozený od <xref:System.Windows.Controls.UserControl>. V důsledku toho uživatelského rozhraní doplňku musí také být odvozený z: <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementace segmentu přidat v-adaptér na straně kanálu

Zatímco kontrakt <xref:System.AddIn.Contract.INativeHandleContract>, doplněk je <xref:System.Windows.FrameworkElement> (jak je uvedeno podle segmentů kanálu doplňku zobrazení). Proto <xref:System.Windows.FrameworkElement> musejí být převedeny do <xref:System.AddIn.Contract.INativeHandleContract> před překročení hranice izolace. Tuto práci provádí adaptér přidat v na straně voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak je znázorněno v následujícím kódu.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

V modelu doplňku kde doplněk vrací uživatelské rozhraní (naleznete v tématu [vytvořit doplňku, vrací uživatelské rozhraní](how-to-create-an-add-in-that-returns-a-ui.md)), převést adaptér doplňků <xref:System.Windows.FrameworkElement> do <xref:System.AddIn.Contract.INativeHandleContract> voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> musí také být volána v tomto modelu, i když je potřeba implementovat metodu, ze kterého chcete napsat kód pro její zavolání. To provedete tak, že přepíšete <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> a provádění kódu, který volá <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> Pokud kód, který volá <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> očekává <xref:System.AddIn.Contract.INativeHandleContract>. V takovém případě bude volající adaptér na straně hostitele, kterému se věnujeme v následující podčásti.  
  
> [!NOTE]
>  Je také potřeba přepsat <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> v tomto modelu k povolení přecházení mezi hostitele v uživatelském rozhraní aplikace pomocí tabulátoru a uživatelského rozhraní doplňku. Další informace najdete v tématu "WPF Add-In omezení" [přehled doplňků WPF](wpf-add-ins-overview.md).  
  
Protože adaptér přidat v na straně implementuje rozhraní, která je odvozena z <xref:System.AddIn.Contract.INativeHandleContract>, budete také muset implementovat <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, i když je ignorováno, pokud <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> je přepsána.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementace segmentu hostitele zobrazení kanálu

V tomto modelu hostitelská aplikace obvykle očekává, že zobrazení hostitele bude <xref:System.Windows.FrameworkElement> podtřídy. Adaptér na straně hostitele, musíte převést <xref:System.AddIn.Contract.INativeHandleContract> k <xref:System.Windows.FrameworkElement> po <xref:System.AddIn.Contract.INativeHandleContract> překročí hranice izolace. Protože metoda není volána hostitele aplikací zobrazíte <xref:System.Windows.FrameworkElement>, zobrazení hostitele musí "vrátit" <xref:System.Windows.FrameworkElement> podle který ji obsahuje. V důsledku toho zobrazení hostitele musí být odvozen od podtřída <xref:System.Windows.FrameworkElement> , která mohou obsahovat další uživatelská rozhraní, jako například <xref:System.Windows.Controls.UserControl>. Následující kód ukazuje zobrazení hostitele smlouvy, které jsou implementovány jako `WPFAddInHostView` třídy.  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementace segmentu kanálu adaptér na straně hostitele

Když je kontrakt <xref:System.AddIn.Contract.INativeHandleContract>, hostitelská aplikace očekává, že <xref:System.Windows.Controls.UserControl> (jak je uvedeno v hostitelském zobrazení). V důsledku toho <xref:System.AddIn.Contract.INativeHandleContract> musí být převeden do <xref:System.Windows.FrameworkElement> po překročení hranice izolace, před nastavením jako obsah zobrazení hostitele (která je odvozena z <xref:System.Windows.Controls.UserControl>).  
  
Tuto práci provádí adaptér na straně hostitele, jak je znázorněno v následujícím kódu.  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

Jak je vidět, získá adaptér na straně hostitele <xref:System.AddIn.Contract.INativeHandleContract> voláním adaptér přidat v na straně <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> – metoda (Toto je bod kam <xref:System.AddIn.Contract.INativeHandleContract> překročí hranice izolace).  
  
Adaptér na straně hostitele převede <xref:System.AddIn.Contract.INativeHandleContract> k <xref:System.Windows.FrameworkElement> voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Nakonec <xref:System.Windows.FrameworkElement> je nastaven jako obsah zobrazení hostitele.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementace doplňku pro

Adaptér přidat v na straně a zobrazení doplňku na místě doplněk může být implementována vyplývající z doplňku zobrazení, jak je znázorněno v následujícím kódu.  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

V tomto příkladu můžete zobrazit zajímavé výhodou tohoto modelu: add-in vývojáři potřebují pouze k implementaci doplněk (protože je také uživatelské rozhraní), spíše než o třídu i uživatelského rozhraní doplňku.  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>Implementace hostitele aplikace

Adaptér na straně hostitele a hostitele zobrazení vytvořené hostitelská aplikace pomocí modelu doplňku rozhraní .NET Framework k otevření kanálu a získat zobrazení hostitele doplňku. Tyto kroky jsou uvedeny v následujícím kódu.  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

Hostitelská aplikace používá typické kódu v modelu doplňku rozhraní .NET Framework aktivovat doplněk, který implicitně vrátí zobrazení hostitele do hostitelské aplikace. Hostitelská aplikace následně zobrazí zobrazení hostitele (což je <xref:System.Windows.Controls.UserControl>) z <xref:System.Windows.Controls.Grid>.  
  
 Spuštění kódu pro zpracování interakce s uživatelským rozhraním doplňku v doplňku na aplikační domény. Tyto akce patří:  
  
- Zpracování <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
- Zobrazuje <xref:System.Windows.MessageBox>.  
  
 Tato aktivita je zcela izolována od hostitelskou aplikaci.  
  
## <a name="see-also"></a>Viz také:

- [Doplňky a rozšíření](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Přehled doplňků WPF](wpf-add-ins-overview.md)
