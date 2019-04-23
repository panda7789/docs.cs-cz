---
title: 'Postupy: Přizpůsobení chování (WCF Data Services) datových vazeb'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: f55c9790b8300a1a3f26e031a17a0982638b562b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517418"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Postupy: Přizpůsobení chování (WCF Data Services) datových vazeb
S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], můžete zadat vlastní logiku, která je volána <xref:System.Data.Services.Client.DataServiceCollection%601> při přidá nebo odebere z kolekce vazby nebo když je zjištěna změna vlastností objektu. Tato vlastní logika se poskytuje jako metody na něho odkazovat jako <xref:System.Func%602> delegáty, které vracejí hodnotu `false` když výchozí chování stále proveďte, když vlastní metoda dokončí a `true` při následné zpracování události by se měla zastavit.  
  
 Příklady v tomto tématu zadat vlastní metody pro oba `entityChanged` a `entityCollectionChanged` parametry <xref:System.Data.Services.Client.DataServiceCollection%601>. Příklady v tomto tématu ukázková datová služba Northwind a klientská data automaticky generované služby třídy. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Vytvoří na následující stránce použití modelu code-behind pro soubor XAML <xref:System.Data.Services.Client.DataServiceCollection%601> pomocí vlastní metody, které jsou volány při výskytu změn dat, která je vázána na kolekci vazby. Když <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> dojde k události, je zadaná metoda zabraňuje položku, která byla odebrána z kolekce vazby odstranit z datové služby. Když <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> dojde k události, `ShipDate` hodnota je ověřena k zajištění, že objednávky, které byly dodány již nejsou provedeny změny.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Příklad  
 Následující XAML definuje v okně z předchozího příkladu.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
