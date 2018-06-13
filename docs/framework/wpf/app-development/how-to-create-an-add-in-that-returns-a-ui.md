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
ms.openlocfilehash: 24b30d61553796840a44a869eacb33232a0b78d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548230"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Postupy: Vytvoření doplňku, který vrací uživatelské rozhraní
Tento příklad ukazuje, jak vytvořit doplněk, který vrací Windows Presentation Foundation (WPF) na hostitele [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] samostatné aplikace.  
  
 Doplněk vrátí [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tedy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uživatelský ovládací prvek. Obsah uživatelského ovládacího prvku je jedné tlačítko, která po kliknutí na zobrazí okno se zprávou. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Samostatné aplikace hostuje doplněk a zobrazí uživatelského ovládacího prvku (vrácený doplněk) jako obsah hlavního okna aplikace.  
  
 **Požadavky**  
  
 Tento příklad klade důraz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšíření [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu, který povolit tento scénář a předpokládá následující:  
  
-   Znalost [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku modelu, včetně kanálu, doplňku a vývoj hostitele. Pokud jste obeznámeni s následujícími základními pojmy, najdete v části [doplňky a rozšíření](../../../../docs/framework/add-ins/index.md). Kurz, který ukazuje implementaci kanál, -v a hostitelskou aplikaci, najdete v části [návod: vytváření rozšiřitelné aplikace](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).  
  
-   Znalosti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšíření [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku model, který se nachází tady: [WPF doplňky přehled](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit doplněk, který vrací [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vyžaduje konkrétní kód pro každý segment kanálu v doplňku a hostitelskou aplikaci.  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementace segmentu kanálu kontraktu  
 Metoda musí být definován ve smlouvě pro návrat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], a hodnoty musí být typu <xref:System.AddIn.Contract.INativeHandleContract>. Tento postup je znázorněn pomocí `GetAddInUI` metodu `IWPFAddInContract` smlouvy v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementace segmentu kanál doplňku zobrazení  
 Protože doplněk implementuje [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] poskytuje jako měly podtřídy <xref:System.Windows.FrameworkElement>, metoda pro zobrazení pro `IWPFAddInView.GetAddInUI` musí vracet hodnoty typu <xref:System.Windows.FrameworkElement>. Následující kód ukazuje zobrazení přidat smlouvy, které jsou implementované jako rozhraní.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementace segmentu kanálu přidat straně adaptéru  
 Vrátí metoda kontraktu <xref:System.AddIn.Contract.INativeHandleContract>, ale doplněk vrací <xref:System.Windows.FrameworkElement> (jak je uvedeno v zobrazení). V důsledku toho <xref:System.Windows.FrameworkElement> musí být převedena na <xref:System.AddIn.Contract.INativeHandleContract> před překračuje hranice izolace. Tento pracovní provádí adaptér přidat straně voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementace segmentu hostitele zobrazení kanálu  
 Protože hostitelskou aplikaci se zobrazí <xref:System.Windows.FrameworkElement>, metoda pro zobrazení hostitele, které odpovídá `IWPFAddInHostView.GetAddInUI` musí vracet hodnoty typu <xref:System.Windows.FrameworkElement>. Následující kód ukazuje hostitelském zobrazení smlouvy, které jsou implementované jako rozhraní.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementace segmentu adaptér hostitelské kanálu  
 Vrátí metodu kontraktu <xref:System.AddIn.Contract.INativeHandleContract>, ale očekává hostitelskou aplikaci <xref:System.Windows.FrameworkElement> (jak je uvedeno v zobrazení hostitele). V důsledku toho <xref:System.AddIn.Contract.INativeHandleContract> musí být převedena na <xref:System.Windows.FrameworkElement> po překročení meze hranice izolace. Tento pracovní provádí adaptér hostitelské voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementace v aplikaci  
 Přidat straně adaptéru a doplněk zobrazení vytvořené, doplněk (`WPFAddIn1.AddIn`) musí implementovat `IWPFAddInView.GetAddInUI` metoda vrátí <xref:System.Windows.FrameworkElement> objekt ( <xref:System.Windows.Controls.UserControl> v tomto příkladu). Implementace <xref:System.Windows.Controls.UserControl>, `AddInUI`, je znázorněno v následujícím kódu.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Implementace `IWPFAddInView.GetAddInUI` pomocí doplňku jednoduše musí vrátit novou instanci třídy `AddInUI`, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Implementace aplikace pro hostitele  
 Adaptér hostitelské a hostitele zobrazení vytvořené hostitelskou aplikaci pomocí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model doplňku otevřít kanál, získat zobrazení hostitele add-in a volání `IWPFAddInHostView.GetAddInUI` metoda. Tyto kroky jsou uvedeny v následující kód.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Viz také  
 [Doplňky a rozšíření](../../../../docs/framework/add-ins/index.md)  
 [Přehled doplňků WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
