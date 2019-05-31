---
title: 'Postupy: Vytvoření vazby dat prvkům Windows Presentation Foundation (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: cecfa42035d4c09eade708417c338ef04ab09ad9
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423823"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Postupy: Vytvoření vazby dat prvkům Windows Presentation Foundation (WCF Data Services)
S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], můžete svázat elementy Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.ListBox> nebo <xref:System.Windows.Controls.ComboBox> do instance <xref:System.Data.Services.Client.DataServiceCollection%601>, která zpracovává události vyvolané službou ovládací prvky, aby <xref:System.Data.Services.Client.DataServiceContext> synchronizována se změnami provedené v datech v ovládacích prvcích. Další informace najdete v tématu [vazba dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá Northwind ukázková data service a automaticky vygenerovaných tříd klientské datové služby. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad je z použití modelu code-behind stránky pro stránku Extensible Application Markup Language (XAML), která definuje `SalesOrders` okna v subsystému WPF. Při načtení okna <xref:System.Data.Services.Client.DataServiceCollection%601> je založeno na výsledku dotazu, který vrátí zákazníky, filtrovat podle země nebo oblasti. Všechny stránky stránkovaného výsledek jsou načteny, spolu s související objednávky a jsou svázaná s <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.StackPanel> , který je kořenové rozložení ovládacího prvku WPF okna. Další informace najdete v tématu [načítání odložené obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Příklad  
 Definuje následující XAML `SalesOrders` okně v subsystému WPF v předchozím příkladu.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad je z použití modelu code-behind stránky pro stránku Extensible Application Markup Language (XAML), která definuje `SalesOrders` okna v subsystému WPF. Při načtení okna <xref:System.Data.Services.Client.DataServiceCollection%601> je založeno na výsledku dotazu, který vrátí zákazníky s související objekty filtrované podle země nebo oblasti. Tento výsledek je vázán na <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.StackPanel> , který je kořenové rozložení ovládacího prvku WPF okna.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Příklad  
 Definuje následující XAML `SalesOrders` okně v subsystému WPF v předchozím příkladu.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
