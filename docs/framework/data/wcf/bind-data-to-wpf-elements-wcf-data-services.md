---
title: 'Postupy: Vázání dat na prvky Windows Presentation Foundation (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: 44f3361aa56d9f15e62852000accd0b4d4d8eb43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791129"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Postupy: Vázání dat na prvky Windows Presentation Foundation (WCF Data Services)
Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]nástroje můžete navazovat prvky Windows Presentation Foundation (WPF) <xref:System.Data.Services.Client.DataServiceCollection%601>, jako je <xref:System.Windows.Controls.ListBox> například <xref:System.Windows.Controls.ComboBox> nebo, do instance, <xref:System.Data.Services.Client.DataServiceContext> která zpracovává události vyvolané ovládacími prvky pro zachování synchronizace se změnami. provedeno na data v ovládacích prvcích. Další informace najdete v tématu [vázání dat na ovládací prvky](binding-data-to-controls-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad je ze stránky s kódem na pozadí stránky jazyk Extensible Application Markup Language (XAML) (XAML), která definuje `SalesOrders` okno v subsystému WPF. Po načtení okna se vytvoří <xref:System.Data.Services.Client.DataServiceCollection%601> na základě výsledku dotazu, který vrací zákazníky, filtrovaný podle země nebo oblasti. Všechny stránky tohoto výsledného výsledku jsou načteny společně se souvisejícími objednávkami a jsou vázány na <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.StackPanel> , která je kořenovým ovládacím prvkem rozložení pro okno WPF. Další informace najdete v tématu [načítání odloženého obsahu](loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Příklad  
 Následující kód XAML definuje `SalesOrders` okno v WPF pro předchozí příklad.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad je ze stránky s kódem na pozadí stránky jazyk Extensible Application Markup Language (XAML) (XAML), která definuje `SalesOrders` okno v subsystému WPF. Po načtení okna se vytvoří <xref:System.Data.Services.Client.DataServiceCollection%601> na základě výsledku dotazu, který vrací zákazníky se souvisejícími objekty filtrovanými podle země/oblasti. Tento výsledek je vázán na <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.StackPanel> , která je kořenovým ovládacím prvkem rozložení pro okno WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Příklad  
 Následující kód XAML definuje `SalesOrders` okno v WPF pro předchozí příklad.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
