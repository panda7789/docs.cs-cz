---
title: 'Postupy: přizpůsobení chování datových vazeb (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: 453562dd1b86756bf9fc1684dc649dba1c24c578
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569166"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Postupy: přizpůsobení chování datových vazeb (WCF Data Services)
Pomocí WCF Data Services můžete dodat vlastní logiku, která je volána <xref:System.Data.Services.Client.DataServiceCollection%601> při přidání nebo odebrání objektu z kolekce vazby nebo při zjištění změny vlastnosti. Tato vlastní logika je poskytována jako metody, na které se odkazuje jako <xref:System.Func%602> delegáti, která vrací hodnotu `false` v případě, že by se vlastní chování mělo provést i v případě, že se vlastní metoda dokončí a `true` při dalším zpracování události by se měla zastavit.  
  
 Příklady v tomto tématu poskytují vlastní metody pro parametry `entityChanged` a `entityCollectionChanged` <xref:System.Data.Services.Client.DataServiceCollection%601>. Příklady v tomto tématu používají ukázkovou datovou službu Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující stránka s kódem na pozadí pro soubor XAML vytvoří <xref:System.Data.Services.Client.DataServiceCollection%601> s vlastními metodami, které jsou volány, když dojde ke změně dat vázaných na kolekci vazeb. Když dojde k události <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged>, dodaná Metoda brání položce, která byla odebrána z kolekce vazeb z odstranění z datové služby. Když dojde k události <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged>, ověří se hodnota `ShipDate`, aby se zajistilo, že se změny v objednávkách, které už byly dodány, neudělaly.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Příklad  
 Následující kód XAML definuje okno pro předchozí příklad.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
