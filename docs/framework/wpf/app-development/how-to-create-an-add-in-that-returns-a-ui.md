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
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Postupy: Vytvoření doplňku, který vrací uživatelské rozhraní
Tento příklad ukazuje, jak vytvořit doplněk, který vrací Windows Presentation Foundation (WPF) do samostatné aplikace WPF hostitele.  
  
 Doplněk vrátí uživatelské rozhraní, které je uživatelský mj. Obsah uživatelského ovládacího prvku je jediné tlačítko, které po klepnutí zobrazí okno se zprávou. Samostatná aplikace WPF hostuje doplněk a zobrazuje uživatelský ovládací prvek (vrácený doplňkem) jako obsah hlavního okna aplikace.  
  
 **Požadavky**  
  
 Tento příklad zvýrazní rozšíření WPF k modelu doplňku rozhraní .NET Framework, které tento scénář povolují, a předpokládá následující:  
  
- Znalost modelu doplňku rozhraní .NET Framework, včetně kanálu, doplňku a vývoje hostitele. Pokud tyto koncepty neznáte, přečtěte si informace [o doplňcích a rozšiřitelnosti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Kurz, který ukazuje implementaci kanálu, doplněk a hostitelské aplikace, naleznete v [návodu: Vytvoření rozšiřitelné aplikace](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- Znalost wpf rozšíření modelu doplňku rozhraní .NET Framework, které lze nalézt zde: [WPF Doplňky Přehled](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit doplněk, který vrací WPF ui vyžaduje konkrétní kód pro každý segment kanálu, doplněk a hostitelské aplikace.  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>Implementace segmentu kanálu smlouvy  
 Metoda musí být definována smlouvou pro vrácení ui a jeho <xref:System.AddIn.Contract.INativeHandleContract>vrácená hodnota musí být typu . To je prokázáno `GetAddInUI` metodou `IWPFAddInContract` smlouvy v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementace segmentu kanálu zobrazení doplňku  
 Vzhledem k tomu, že doplněk implementuje <xref:System.Windows.FrameworkElement>ui poskytuje jako podtřídy , metoda `IWPFAddInView.GetAddInUI` v zobrazení doplňku, který koreluje s musí vrátit hodnotu typu <xref:System.Windows.FrameworkElement>. Následující kód ukazuje zobrazení doplňku smlouvy, implementované jako rozhraní.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementace segmentu kanálu adaptéru na straně doplňku  
 Metoda smlouvy vrátí <xref:System.AddIn.Contract.INativeHandleContract>, ale doplněk vrátí <xref:System.Windows.FrameworkElement> (jak je určeno zobrazení doplňku). V důsledku <xref:System.Windows.FrameworkElement> toho musí být <xref:System.AddIn.Contract.INativeHandleContract> převedena na před překročení hranice izolace. Tuto práci provádí adaptér na straně doplňku <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>voláním , jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementace segmentu kanálu zobrazení hostitele  
 Vzhledem k tomu, <xref:System.Windows.FrameworkElement>že hostitelská aplikace zobrazí , `IWPFAddInHostView.GetAddInUI` metoda v zobrazení <xref:System.Windows.FrameworkElement>hostitele, která koreluje s musí vrátit hodnotu typu . Následující kód zobrazuje zobrazení hostitele smlouvy, implementované jako rozhraní.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementace segmentu kanálu adaptéru na straně hostitele  
 Metoda smlouvy vrátí <xref:System.AddIn.Contract.INativeHandleContract>, ale hostitelská <xref:System.Windows.FrameworkElement> aplikace očekává (jak je určeno zobrazení hostitele). V důsledku <xref:System.AddIn.Contract.INativeHandleContract> toho musí být <xref:System.Windows.FrameworkElement> převedena na po překročení hranice izolace. Tato práce je prováděna adaptérem <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>na straně hostitele voláním , jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>Implementace doplňku  
 Při vytvoření adaptéru na straně a zobrazení doplňku musí`WPFAddIn1.AddIn`doplněk ( `IWPFAddInView.GetAddInUI` ) implementovat <xref:System.Windows.FrameworkElement> metodu <xref:System.Windows.Controls.UserControl> pro vrácení objektu (a v tomto příkladu). Implementace <xref:System.Windows.Controls.UserControl>, `AddInUI`, je zobrazena v následujícím kódu.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Implementace `IWPFAddInView.GetAddInUI` doplňku jednoduše potřebuje vrátit novou instanci `AddInUI`, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>
## <a name="implementing-the-host-application"></a>Implementace hostitelské aplikace  
 Při vytvoření adaptéru na straně hostitele a zobrazení hostitele může hostitelská aplikace použít model doplňku rozhraní .NET Framework k `IWPFAddInHostView.GetAddInUI` otevření kanálu, získání zobrazení hostitele doplňku a volání metody. Tyto kroky jsou uvedeny v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Viz také

- [Doplňky a rozšíření](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Přehled doplňků WPF](wpf-add-ins-overview.md)
