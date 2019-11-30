---
title: 'Postupy: vázání dat na prvky Windows Presentation Foundation (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: b623dc10bfe1b723c62b2861b4142a138904e64a
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569342"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Postupy: vázání dat na prvky Windows Presentation Foundation (WCF Data Services)
Pomocí WCF Data Services lze navázat prvky Windows Presentation Foundation (WPF), jako je například <xref:System.Windows.Controls.ListBox> nebo <xref:System.Windows.Controls.ComboBox>, do instance <xref:System.Data.Services.Client.DataServiceCollection%601>, která zpracovává události vyvolané ovládacími prvky, aby zůstala <xref:System.Data.Services.Client.DataServiceContext> synchronizována se změnami provedenými v datech v ovládacích prvcích. Další informace najdete v tématu [vázání dat na ovládací prvky](binding-data-to-controls-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad je ze stránky s kódem na pozadí stránky jazyk Extensible Application Markup Language (XAML) (XAML), která definuje okno `SalesOrders` v subsystému WPF. Po načtení okna se vytvoří <xref:System.Data.Services.Client.DataServiceCollection%601> na základě výsledku dotazu, který vrací zákazníky, filtrovaný podle země nebo oblasti. Všechny stránky tohoto výsledného výsledku jsou načteny společně se souvisejícími objednávkami a jsou vázány na vlastnost <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.StackPanel>, která je ovládací prvek kořenového rozložení pro okno WPF. Další informace najdete v tématu [načítání odloženého obsahu](loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Příklad  
 Následující kód XAML definuje okno `SalesOrders` v subsystému WPF pro předchozí příklad.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad je ze stránky s kódem na pozadí stránky jazyk Extensible Application Markup Language (XAML) (XAML), která definuje okno `SalesOrders` v subsystému WPF. Po načtení okna se vytvoří <xref:System.Data.Services.Client.DataServiceCollection%601> na základě výsledku dotazu, který vrátí zákazníky se souvisejícími objekty filtrovanými podle země/oblasti. Tento výsledek je vázán na vlastnost <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.StackPanel>, která je kořenovým ovládacím prvkem rozložení okna WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Příklad  
 Následující kód XAML definuje okno `SalesOrders` v subsystému WPF pro předchozí příklad.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
