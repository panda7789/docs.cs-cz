---
title: 'Postupy: nastavení hlaviček v žádosti klienta (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: c8b20fc16b75b0d5267079db19ed55ae08604ff0
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568987"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Postupy: nastavení hlaviček v žádosti klienta (WCF Data Services)
Při použití klientské knihovny WCF Data Services pro přístup k datové službě, která podporuje protokol OData (Open Data Protocol), Klientská knihovna automaticky nastaví požadované hlavičky protokolu HTTP v žádostech odesílaných na datovou službu. Klientská knihovna však neví, že v některých případech nastavuje záhlaví zpráv, která jsou vyžadována v některých případech, například pokud datová služba vyžaduje ověřování založené na deklaracích nebo soubory cookie. Další informace najdete v tématu [zabezpečení WCF Data Services](securing-wcf-data-services.md#clientAuthentication). V těchto případech je před odesláním nutné ručně nastavit záhlaví zpráv ve zprávě požadavku. V příkladu v tomto tématu se dozvíte, jak zpracovat událost <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>, abyste před odesláním do datové služby přidali do zprávy požadavku novou hlavičku.  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md). Můžete také použít [ukázkovou datovou službu Northwind](https://go.microsoft.com/fwlink/?LinkId=187426) , která je publikována na webu OData. Tato ukázková datová služba je jen pro čtení a při pokusu o uložení změn se vrátí chyba. Služba ukázkových dat na webu OData povoluje anonymní ověřování.  
  
## <a name="example"></a>Příklad  
 Následující příklad zaregistruje obslužnou rutinu pro událost <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> a pak provede dotaz na datovou službu.  
  
> [!NOTE]
> Pokud datová služba vyžaduje, abyste ručně nastavili hlavičku zprávy pro každý požadavek, zvažte registraci obslužné rutiny pro událost <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> přepsáním `OnContextCreated` částečné metody v kontejneru entit, který představuje datovou službu, která je v tomto případě `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Příklad  
 Následující metoda zpracuje událost <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> a přidá do žádosti hlavičku ověřování.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení datových služeb WCF Data Services](securing-wcf-data-services.md)
- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
