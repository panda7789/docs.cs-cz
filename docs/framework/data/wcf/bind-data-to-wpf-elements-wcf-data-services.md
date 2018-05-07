---
title: 'Postupy: připojení dat k prvky systému Windows Presentation Foundation (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: da89eebb366cebca9933a30b4753e1fbbe2707c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Postupy: připojení dat k prvky systému Windows Presentation Foundation (WCF Data Services)
S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], lze vázat elementy Windows Presentation Foundation (WPF), jako <xref:System.Windows.Controls.ListBox>'' nebo <xref:System.Windows.Controls.ComboBox> na instanci <xref:System.Data.Services.Client.DataServiceCollection%601>, který zpracovává události vyvolané službou zachovat ovládací prvky <xref:System.Data.Services.Client.DataServiceContext> synchronizována se změnami žádost o data v ovládacích prvcích. Další informace najdete v tématu [vazby dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad je z kódu stránky pro stránku rozšiřitelné aplikace Markup Language (XAML), která definuje `SalesOrders` okno v grafickém subsystému WPF. Při načítání okna <xref:System.Data.Services.Client.DataServiceCollection%601> se vytvoří na základě u výsledku dotazu, který vrátí zákazníků, filtrovaná podle země. Všechny stránky výsledek tohoto stránkové jsou načteny, společně s související objednávky a je vázána na <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.StackPanel> tedy kořenové rozložení ovládacího prvku pro okno WPF. Další informace najdete v tématu [načítání odložení obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Příklad  
 Definuje následující XAML `SalesOrders` okna v grafickém subsystému WPF pro předchozí příklad.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad je z kódu stránky pro stránku rozšiřitelné aplikace Markup Language (XAML), která definuje `SalesOrders` okno v grafickém subsystému WPF. Při načítání okna <xref:System.Data.Services.Client.DataServiceCollection%601> se vytvoří na základě u výsledku dotazu, který vrátí zákazníkům souvisejících objektů, které jsou filtrovány podle země. Tento výsledek je vázána <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.StackPanel> tedy kořenové rozložení ovládacího prvku pro okno WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Příklad  
 Definuje následující XAML `SalesOrders` okna v grafickém subsystému WPF pro předchozí příklad.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
