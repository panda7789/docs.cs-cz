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
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Postupy: Vytvoření doplňku, který vrací uživatelské rozhraní
Tento příklad ukazuje, jak vytvořit doplněk, který vrací Windows Presentation Foundation (WPF) do samostatné aplikace hostitele WPF.  
  
 Doplněk vrátí uživatelské rozhraní, které je uživatelským ovládacím prvkem WPF. Obsah uživatelského ovládacího prvku je jediné tlačítko, které po kliknutí zobrazí okno se zprávou. Samostatná aplikace WPF je hostitelem doplňku a zobrazuje uživatelský ovládací prvek (vrácený doplňkem) jako obsah okna hlavní aplikace.  
  
 **Požadovaný**  
  
 Tento příklad zvýrazní rozšíření WPF pro .NET Framework Model doplňku, který umožňuje tento scénář, a předpokládá následující:  
  
- Znalost .NET Frameworkho modelu doplňku, včetně kanálu, doplňku a vývoje hostitele. Pokud tyto koncepty neznáte, přečtěte si téma [Doplňky a rozšiřitelnost](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Kurz, který ukazuje implementaci kanálu, doplňku a hostitelské aplikace, najdete v tématu [Návod: vytváření rozšiřitelné aplikace](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- Znalosti rozšíření WPF pro .NET Framework Model doplňku, který najdete tady: [Přehled doplňků WPF](wpf-add-ins-overview.md)  
  
## <a name="example"></a>Příklad  
 Pro vytvoření doplňku, který vrací uživatelské rozhraní WPF, je nutné zadat konkrétní kód pro každý segment kanálu, doplněk a hostitelskou aplikaci.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementace segmentu kanálu smluv  
 Metoda musí být definována kontraktem pro vrácení uživatelského rozhraní a vrácená hodnota musí být typu <xref:System.AddIn.Contract.INativeHandleContract>. To je ukázáno metodou `GetAddInUI` kontraktu `IWPFAddInContract` v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementace segmentu kanálu zobrazení doplňku  
 Vzhledem k tomu, že doplněk implementuje uživatelská rozhraní, který poskytuje jako podtřídy <xref:System.Windows.FrameworkElement>, metoda v zobrazení doplňku, která koreluje s `IWPFAddInView.GetAddInUI` musí vracet hodnotu typu <xref:System.Windows.FrameworkElement>. Následující kód ukazuje zobrazení smlouvy o doplňku, které je implementováno jako rozhraní.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementace segmentu kanálu adaptéru na straně doplňku  
 Metoda kontraktu vrátí <xref:System.AddIn.Contract.INativeHandleContract>, ale doplněk vrátí <xref:System.Windows.FrameworkElement> (jak je uvedeno v zobrazení doplňku). V důsledku toho musí být <xref:System.Windows.FrameworkElement> převedena na <xref:System.AddIn.Contract.INativeHandleContract> před překročením hranice izolace. Tato práce se provádí pomocí adaptéru doplňku na straně voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementace segmentu kanálu zobrazení hostitele  
 Protože hostitelská aplikace zobrazí <xref:System.Windows.FrameworkElement>, metoda v zobrazení hostitele, která koreluje s `IWPFAddInHostView.GetAddInUI`, musí vracet hodnotu typu <xref:System.Windows.FrameworkElement>. Následující kód ukazuje zobrazení hostitele kontraktu, implementované jako rozhraní.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementace segmentu kanálu adaptéru na straně hostitele  
 Metoda kontraktu vrací <xref:System.AddIn.Contract.INativeHandleContract>, ale hostitelská aplikace očekává <xref:System.Windows.FrameworkElement> (jak je uvedeno v zobrazení hostitele). V důsledku toho musí být <xref:System.AddIn.Contract.INativeHandleContract> převedena na <xref:System.Windows.FrameworkElement> po překročení hranice izolace. Tuto práci provádí hostitelský adaptér na straně hostitele voláním <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementace doplňku  
 Když je vytvořen adaptér doplňku a zobrazení doplňku, musí doplněk (`WPFAddIn1.AddIn`) implementovat metodu `IWPFAddInView.GetAddInUI` pro vrácení objektu <xref:System.Windows.FrameworkElement> (v tomto příkladu <xref:System.Windows.Controls.UserControl>). Implementace <xref:System.Windows.Controls.UserControl>, `AddInUI`, je zobrazena v následujícím kódu.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Implementace `IWPFAddInView.GetAddInUI` pomocí doplňku jednoduše potřebuje vrátit novou instanci `AddInUI`, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Implementace hostitelské aplikace  
 S vytvořeným hostitelským adaptérem a zobrazením hostitele může hostitelská aplikace použít model doplňku .NET Framework k otevření kanálu, získání zobrazení hostitele doplňku a volání metody `IWPFAddInHostView.GetAddInUI`. Tyto kroky jsou uvedeny v následujícím kódu.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Viz také:

- [Doplňky a rozšíření](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Přehled doplňků WPF](wpf-add-ins-overview.md)
