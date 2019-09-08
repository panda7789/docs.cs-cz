---
title: 'Postupy: Přizpůsobení chování datových vazeb (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: c878096cba7d31e0b48727213ee1bb8239b8f690
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790759"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Postupy: Přizpůsobení chování datových vazeb (WCF Data Services)
Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]můžete předat vlastní logiku, která je volána <xref:System.Data.Services.Client.DataServiceCollection%601> při přidání nebo odebrání objektu z kolekce vazby nebo při zjištění změny vlastnosti. Tato vlastní logika je poskytována jako metody, na <xref:System.Func%602> které se odkazuje jako delegáti, `false` která vrací hodnotu, pokud má být výchozí chování provedeno i po dokončení vlastní `true` metody a při následném zpracování událost by se měla zastavit.  
  
 Příklady v tomto tématu poskytují vlastní metody pro `entityChanged` parametry <xref:System.Data.Services.Client.DataServiceCollection%601>a `entityCollectionChanged` . Příklady v tomto tématu používají ukázkovou datovou službu Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující stránka <xref:System.Data.Services.Client.DataServiceCollection%601> s kódem na pozadí pro soubor XAML vytvoří s vlastními metodami, které jsou volány, když dojde ke změně dat vázaných na kolekci vazeb. Když dojde k události, dodaná metoda zabrání položce, která byla odebrána z kolekce vazeb z odstranění z datové služby. <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> Když dojde k `ShipDate` <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> události, ověří se hodnota, aby se zajistilo, že se změny v objednávkách, které už dodaly, neudělaly.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Příklad  
 Následující kód XAML definuje okno pro předchozí příklad.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
