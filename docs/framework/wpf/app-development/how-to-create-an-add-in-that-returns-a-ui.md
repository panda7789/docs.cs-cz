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
ms.openlocfilehash: faed11bb02037ea42b31402d431e1bcdd8b70339
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115746"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Postupy: Vytvoření doplňku, který vrací uživatelské rozhraní
Tento příklad ukazuje, jak vytvořit doplněk, který vrací Windows Presentation Foundation (WPF) do hostitele samostatnou aplikaci WPF.  
  
 Doplněk vrací uživatelské rozhraní, která je uživatelský ovládací prvek WPF. Obsah uživatelský ovládací prvek je jediné tlačítko, které, při kliknutí zobrazí okno se zprávou. Samostatná aplikace WPF hostuje doplněk a zobrazuje uživatelský ovládací prvek (vráceným metodou doplněk) jako obsah hlavního okna aplikace.  
  
 **Požadavky**  
  
 V tomto příkladu zvýrazní WPF rozšíření modelu doplňku rozhraní .NET Framework, které umožňují tento scénář a předpokládá následující:  
  
-   Znalost modelu rozhraní .NET Framework – doplněk, včetně kanálu doplňku a vývoj pro hostitele. Pokud nejste obeznámeni s tyto koncepty, najdete v článku [doplňků a rozšíření](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Kurz, který ukazuje implementaci kanálu, doplněk a hostitelskou aplikací, najdete v tématu [názorný postup: Vytváření rozšiřitelné aplikace](../../add-ins/walkthrough-create-extensible-app.md).  
  
-   Informace o rozšíření WPF rozhraní .NET Framework model doplňku, který najdete tady: [Přehled doplňků WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Příklad  
 K vytvoření doplňku, který vrací uživatelské rozhraní WPF vyžaduje konkrétní kód pro každý segment kanálu doplňku a hostitelskou aplikaci.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementace kontraktu Segment kanálu  
 Metoda musí být definován ve smlouvě vrací uživatelské rozhraní a vrácená hodnota musí být typu <xref:System.AddIn.Contract.INativeHandleContract>. To je patrné podle `GetAddInUI` metodu `IWPFAddInContract` smlouvy v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementace segmentu kanálu doplňku zobrazení  
 Protože doplněk implementuje [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] poskytuje jako podtřídy třídy <xref:System.Windows.FrameworkElement>, metoda pro zobrazení, které souvisí s `IWPFAddInView.GetAddInUI` musí vracet hodnotu typu <xref:System.Windows.FrameworkElement>. Následující kód ukazuje zobrazení přidat smlouvy, které jsou implementovány jako rozhraní.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementace segmentu přidat v-adaptér na straně kanálu  
 Vrátí metoda smlouvy <xref:System.AddIn.Contract.INativeHandleContract>, ale doplněk vrátí <xref:System.Windows.FrameworkElement> (jak je uvedeno v zobrazení). V důsledku toho <xref:System.Windows.FrameworkElement> musejí být převedeny do <xref:System.AddIn.Contract.INativeHandleContract> před překročení hranice izolace. Tuto práci provádí adaptér přidat v na straně voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementace segmentu hostitele zobrazení kanálu  
 Protože hostitelská aplikace se zobrazí <xref:System.Windows.FrameworkElement>, metoda v hostitelském zobrazení, které souvisí s `IWPFAddInHostView.GetAddInUI` musí vracet hodnotu typu <xref:System.Windows.FrameworkElement>. Následující kód zobrazuje hostitele kontraktu implementováno jako rozhraní.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementace segmentu kanálu adaptér na straně hostitele  
 Vrátí metodu smlouvy <xref:System.AddIn.Contract.INativeHandleContract>, ale hostitelská aplikace očekává, že <xref:System.Windows.FrameworkElement> (jak je uvedeno v hostitelském zobrazení). V důsledku toho <xref:System.AddIn.Contract.INativeHandleContract> musí být převeden do <xref:System.Windows.FrameworkElement> po překročení hranice izolace. Tato práce se provádí pomocí adaptéru hostitelské voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementace doplňku pro  
 Adaptér přidat v na straně a doplňku zobrazení vytvořené, doplněk (`WPFAddIn1.AddIn`) musí implementovat `IWPFAddInView.GetAddInUI` metodu pro návrat <xref:System.Windows.FrameworkElement> objekt ( <xref:System.Windows.Controls.UserControl> v tomto příkladu). Provádění <xref:System.Windows.Controls.UserControl>, `AddInUI`, je znázorněno v následujícím kódu.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Provádění `IWPFAddInView.GetAddInUI` pomocí doplňku jednoduše musí vracet novou instanci třídy `AddInUI`, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Implementace hostitele aplikace  
 Adaptér na straně hostitele a hostitele zobrazení vytvořené hostitelská aplikace pomocí modelu doplňku rozhraní .NET Framework na Otevřít kanál, získat zobrazení hostitele doplňku a volání `IWPFAddInHostView.GetAddInUI` metody. Tyto kroky jsou uvedeny v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Viz také:

- [Doplňky a rozšíření](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Přehled doplňků WPF](wpf-add-ins-overview.md)
