---
title: 'Postupy: povolení přístupu ke službě Data (služby WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: e383fd493326b417002818d8cf32dc5251bd9c6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Postupy: povolení přístupu ke službě Data (služby WCF Data Services)
V [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], je nutné explicitně udělit přístup k prostředkům, které jsou vystavené datové služby. To znamená, že po vytvoření nové datové služby, je nutné stále explicitně zadat přístup k jednotlivým prostředkům jako sady entit. Toto téma ukazuje, jak povolit čtení a zápis do pěti entity nastaví ve službě Northwind data, která se vytvoří při dokončení [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Protože <xref:System.Data.Services.EntitySetRights> je výčet definován pomocí <xref:System.FlagsAttribute>, můžete použít logickou nebo nastavit operátor zadat více oprávnění pro jednu entitu.  
  
> [!NOTE]
>  Libovolného klienta, který můžete přístup k aplikaci ASP.NET můžete také přístup k prostředkům vystavené službu data. V produkčním datové služby aby se zabránilo neoprávněnému přístupu k prostředkům, je nutné také zabezpečit vlastní aplikace. Další informace najdete v tématu [NIB: zabezpečení ASP.NET](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).  
  
### <a name="to-enable-access-to-the-data-service"></a>Chcete-li povolit přístup ke službě data  
  
-   V kódu pro službu data, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     To umožňuje klientům ke čtení a zápis `Orders` a `Order_Details` sad entit a přístup jen pro čtení k `Customers` sady entit.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vývoj datové služby WCF ve službě IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [Konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
