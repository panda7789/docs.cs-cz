---
title: "Postupy: Vytvoření doplňku tvořící uživatelské rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9151dd5fa36e3691361bcf6d7c7b281646982f3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Postupy: Vytvoření doplňku tvořící uživatelské rozhraní
Tento příklad ukazuje, jak vytvořit doplněk, který je [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] který je hostován [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] samostatné aplikace.  
  
 Doplněk je [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tedy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uživatelský ovládací prvek. Obsah uživatelského ovládacího prvku je jedné tlačítko, která po kliknutí na zobrazí okno se zprávou. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Samostatné aplikace je hostitelem doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jako obsah hlavního okna aplikace.  
  
 **Požadavky**  
  
 Tento příklad klade důraz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšíření [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu, který povolit tento scénář a předpokládá následující:  
  
-   Znalost [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku modelu, včetně kanálu, doplňku a vývoj hostitele. Pokud jste obeznámeni s následujícími základními pojmy, najdete v části [doplňky a rozšíření](../../../../docs/framework/add-ins/index.md). Kurz, který ukazuje implementaci kanál, -v a hostitelskou aplikaci, najdete v části [návod: vytváření rozšiřitelné aplikace](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).  
  
-   Znalosti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšíření [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] doplňku model, který se nachází tady: [WPF doplňky přehled](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit doplněk, který je [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vyžaduje konkrétní kód pro každý segment kanálu v doplňku a hostitelskou aplikaci.  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementace segmentu kanálu kontraktu  
 Pokud je doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], musí implementovat smlouvu pro doplněk <xref:System.AddIn.Contract.INativeHandleContract>. V příkladu `IWPFAddInContract` implementuje <xref:System.AddIn.Contract.INativeHandleContract>, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInIsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]  
  
<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementace segmentu kanál doplňku zobrazení  
 Protože doplněk je implementovaný jako podtřídou třídy <xref:System.Windows.FrameworkElement> typ tohoto zobrazení, musí taky podtřídami <xref:System.Windows.FrameworkElement>. Následující kód ukazuje zobrazení přidat smlouvy, které jsou implementované jako `WPFAddInView` třídy.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
  
 Zde je zobrazení doplněk odvozený od <xref:System.Windows.Controls.UserControl>. V důsledku toho doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] také měl odvozovat od <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementace segmentu kanálu přidat straně adaptéru  
 Když je kontrakt <xref:System.AddIn.Contract.INativeHandleContract>, doplněk je <xref:System.Windows.FrameworkElement> (jak je uvedeno podle segmentu kanálu zobrazení add-in). Proto <xref:System.Windows.FrameworkElement> musí být převedena na <xref:System.AddIn.Contract.INativeHandleContract> před překračuje hranice izolace. Tento pracovní provádí adaptér přidat straně voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
  
 V modelu doplňku kde doplněk, vrátí [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] (najdete v části [vytvořit doplněk, vrátí uživatelského rozhraní](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md)), je adaptér převést <xref:System.Windows.FrameworkElement> k <xref:System.AddIn.Contract.INativeHandleContract> voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>je také nutné volat v tomto modelu, i když potřebujete implementovat metodu ze kterého chcete napsat kód pro volání. To uděláte přepsáním <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> a implementace kód, který volá <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> Pokud kód, který volá <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> očekává <xref:System.AddIn.Contract.INativeHandleContract>. V takovém případě bude volající adaptér straně hostitele, který je popsaná v následující dílčí části.  
  
> [!NOTE]
>  Je také nutné přepsat <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> v tomto modelu k povolení přecházení mezi hostitelskou aplikaci pomocí tabulátoru [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Další informace najdete v tématu "WPF Add-In omezení" v [WPF doplňky přehled](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 Vzhledem k tomu, že je adaptér přidat straně implementuje rozhraní, která je odvozena od <xref:System.AddIn.Contract.INativeHandleContract>, musíte také implementovat <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, i když je to ignorovat při <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> přepsána.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementace segmentu hostitele zobrazení kanálu  
 V tomto modelu hostitelskou aplikaci obvykle očekává hostitelském zobrazení být <xref:System.Windows.FrameworkElement> podtřídy. Adaptér hostitelské nutné převést <xref:System.AddIn.Contract.INativeHandleContract> k <xref:System.Windows.FrameworkElement> po <xref:System.AddIn.Contract.INativeHandleContract> protne hranice izolace. Metoda není volána hostitele aplikací získat <xref:System.Windows.FrameworkElement>, hostitelském zobrazení musí "vrátit" <xref:System.Windows.FrameworkElement> podle obsahující ho. V důsledku toho hostitelském zobrazení musí být odvozeny od podtřídou třídy <xref:System.Windows.FrameworkElement> , může obsahovat jiné [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], jako například <xref:System.Windows.Controls.UserControl>. Následující kód ukazuje hostitelském zobrazení smlouvy, které jsou implementované jako `WPFAddInHostView` třídy.  
  
  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementace segmentu adaptér hostitelské kanálu  
 Když je kontrakt <xref:System.AddIn.Contract.INativeHandleContract>, očekává hostitelskou aplikaci <xref:System.Windows.Controls.UserControl> (jak je uvedeno v zobrazení hostitele). V důsledku toho <xref:System.AddIn.Contract.INativeHandleContract> musí být převedena na <xref:System.Windows.FrameworkElement> po překročení meze hranici izolace, před nastavením jako obsah zobrazení hostitele (která je odvozena z <xref:System.Windows.Controls.UserControl>).  
  
 Tento pracovní provádí adaptéru hostitelské, jak je znázorněno v následujícím kódu.  
  
  
  
 Jak můžete vidět, získá adaptér hostitelské <xref:System.AddIn.Contract.INativeHandleContract> voláním adaptéru přidat straně <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> – metoda (to je bod kde <xref:System.AddIn.Contract.INativeHandleContract> protne hranic izolace).  
  
 Adaptér hostitelské potom převede <xref:System.AddIn.Contract.INativeHandleContract> k <xref:System.Windows.FrameworkElement> voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Nakonec <xref:System.Windows.FrameworkElement> je nastaven jako obsah zobrazení hostitele.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementace v aplikaci  
 Přidat straně adaptéru a přidat zobrazení na místě doplněk lze implementovat Odvozením ze zobrazení add-in, jak je znázorněno v následujícím kódu.  
  
  
  
  
  
 Z tohoto příkladu vidíte zajímavé výhodou tohoto modelu: doplněk vývojáři stačí k implementaci doplňku (vzhledem k tomu, že je [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i), nikoli třída doplňku i doplňku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="HostApp"></a>   
## <a name="implementing-the-host-application"></a>Implementace aplikace pro hostitele  
 Adaptér hostitelské a hostitele zobrazení vytvořené hostitelskou aplikaci pomocí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model doplňku otevřít kanál a získat zobrazení hostitele add-in. Tyto kroky jsou uvedeny v následující kód.  
  
  
  
 Hostitelskou aplikaci používá typické [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model doplňku kód pro aktivaci doplněk, který implicitně vrátí hostitelském zobrazení hostitelskou aplikaci. Hostitelskou aplikaci následně zobrazí hostitelském zobrazení (což je <xref:System.Windows.Controls.UserControl>) z <xref:System.Windows.Controls.Grid>.  
  
 Kód pro zpracování interakce s doplněk [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] běží v doplňku na domény aplikace. Tyto akce patří:  
  
-   Zpracování <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
-   Zobrazuje <xref:System.Windows.MessageBox>.  
  
 Tato aktivita je naprosto izolované od hostitelskou aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Doplňky a rozšíření](../../../../docs/framework/add-ins/index.md)  
 [Přehled doplňky WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
