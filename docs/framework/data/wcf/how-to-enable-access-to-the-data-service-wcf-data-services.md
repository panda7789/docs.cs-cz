---
title: 'Postupy: povolení přístupu k datové službě (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 0ec9c9a730516b22b4eaa215e042e9393c01d752
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569108"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Postupy: povolení přístupu k datové službě (WCF Data Services)
V WCF Data Services musíte explicitně udělit přístup k prostředkům, které jsou zpřístupněny datovou službou. To znamená, že po vytvoření nové datové služby musíte explicitně poskytnout přístup k jednotlivým prostředkům jako sady entit. V tomto tématu se dozvíte, jak povolit přístup pro čtení a zápis do pěti sad entit v datové službě Northwind, která se vytvoří po dokončení [rychlého](quickstart-wcf-data-services.md)startu. Vzhledem k tomu, že je výčet <xref:System.Data.Services.EntitySetRights> definován pomocí <xref:System.FlagsAttribute>, lze pomocí logického operátoru OR zadat více oprávnění pro jednu sadu entit.  
  
> [!NOTE]
> Každý klient, který má přístup k aplikaci ASP.NET, může také přistupovat k prostředkům vystaveným datovou službou. Pokud chcete zabránit neoprávněnému přístupu k prostředkům, měli byste ve službě produkčních dat také zabezpečit samotnou aplikaci. Další informace najdete v tématu [zabezpečení ASP.NET webů](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
### <a name="to-enable-access-to-the-data-service"></a>Povolení přístupu k datové službě  
  
- V kódu pro datovou službu nahraďte zástupný kód ve funkci `InitializeService` následujícím způsobem:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     To umožňuje klientům mít přístup pro čtení a zápis do `Orders` a `Order_Details` sady entit a přístup jen pro čtení k sadám entit `Customers`.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vývoj datové služby WCF ve službě IIS](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Konfigurace datové služby](configuring-the-data-service-wcf-data-services.md)
