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
ms.openlocfilehash: b2ef0cce293913fc7bd9d59baa91bd875823cbe2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353930"
---
# <a name="how-to-bind-to-a-web-service"></a>Postupy: Připojení k webové službě
Tento příklad ukazuje, jak svázat objekty vrácené z volání metody webové služby.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu [služba obsah MSDN/TechNet Publishing System (MTPS)](https://go.microsoft.com/fwlink/?LinkId=95677) načíst seznam jazyků podporovaných zadaný dokument.  
  
 Než bude volat webovou službu, musíte vytvořit odkaz na něj. Chcete-li vytvořit webový odkaz na službu MTPS pomocí [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], postupujte podle následujících kroků:  
  
1.  Otevřete projekt v [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].  
  
2.  Z **projektu** nabídky, klikněte na tlačítko **přidat webový odkaz**.  
  
3.  V dialogovém okně nastavte **URL** k [ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).  
  
4.  Stisknutím klávesy **Přejít** a potom **přidat odkaz na**.  
  
 V dalším kroku volání metody webové služby a nastavení <xref:System.Windows.FrameworkElement.DataContext%2A> vhodný ovládací prvek nebo v okně pro vrácený objekt. **GetContent** metody MTPS služby používá odkaz na objekt **getContentRequest** objektu. Následující příklad proto nejprve nastaví objekt žádosti:  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 Po <xref:System.Windows.FrameworkElement.DataContext%2A> byl nastaven, můžete vytvořit vazby na vlastnosti objektu, který <xref:System.Windows.FrameworkElement.DataContext%2A> byla nastavena. V tomto příkladu <xref:System.Windows.FrameworkElement.DataContext%2A> je nastavena na **getContentResponse** objekt vrácený **GetContent** metoda. V následujícím příkladu <xref:System.Windows.Controls.ItemsControl> vazbu a zobrazí **národní prostředí** hodnoty **availableVersionsAndLocales** z **getContentResponse**.  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 Informace o struktuře **getContentResponse**, naleznete v tématu [dokumentace ke službě Content](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## <a name="see-also"></a>Viz také:
- [Přehled datových vazeb](data-binding-overview.md)
- [Přehled zdrojů vazby](binding-sources-overview.md)
- [Zpřístupnění dat pro vazbu v jazyku XAML](how-to-make-data-available-for-binding-in-xaml.md)
