---
title: 'Postupy: Připojení k webové službě'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
ms.openlocfilehash: 75d9d5b6981f868c7a172edd7f23cf923fedd525
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557287"
---
# <a name="how-to-bind-to-a-web-service"></a>Postupy: Připojení k webové službě
Tento příklad ukazuje, jak vytvořit vazbu na objektů vrácený volání metody webové služby.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá [služba obsah na webu MSDN nebo TechNet publikování systému (MTPS)](http://go.microsoft.com/fwlink/?LinkId=95677) načíst seznam jazyků – podpora zadaný dokument.  
  
 Před voláním webové služby, musíte vytvořit odkaz na něj. Chcete-li vytvořit odkaz na použití služby MTPS [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], postupujte podle následujících kroků:  
  
1.  Otevřete projekt v [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].  
  
2.  Z **projektu** nabídky, klikněte na tlačítko **přidat odkaz na Web**.  
  
3.  V dialogovém okně Nastavení **URL** k [ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).  
  
4.  Stiskněte klávesu **přejděte** a potom **přidat odkaz**.  
  
 Pak zavolejte metodu webové služby a nastavte <xref:System.Windows.FrameworkElement.DataContext%2A> vhodný ovládací prvek nebo okna vráceného objektu. **GetContent** metoda služby MTPS přebírá odkaz na **getContentRequest** objektu. Následující příklad proto nejprve nastavuje objekt žádosti:  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 Po <xref:System.Windows.FrameworkElement.DataContext%2A> byl nastaven, můžete vytvořit vazby vlastností objektu, který <xref:System.Windows.FrameworkElement.DataContext%2A> byla nastavena na. V tomto příkladu <xref:System.Windows.FrameworkElement.DataContext%2A> je nastaven na **getContentResponse** objekt vrácený **GetContent** metoda. V následujícím příkladu <xref:System.Windows.Controls.ItemsControl> váže a zobrazí **národního prostředí** hodnoty **availableVersionsAndLocales** z **getContentResponse**.  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 Informace o struktuře **getContentResponse**, najdete v části [služba obsah dokumentaci](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Přehled zdrojů vazby](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Zpřístupnění dat pro vazbu v jazyku XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
