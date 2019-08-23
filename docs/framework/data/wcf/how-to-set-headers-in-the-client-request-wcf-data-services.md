---
title: 'Postupy: Nastavení hlaviček v žádosti klienta (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 5a72b349526d5cbba229cba627c23b1b1b889678
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943937"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Postupy: Nastavení hlaviček v žádosti klienta (WCF Data Services)
Když použijete [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientskou knihovnu pro přístup k datové službě, která [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]podporuje, knihovna klienta automaticky nastaví požadované hlavičky protokolu HTTP v žádostech odesílaných do datové služby. Klientská knihovna však neví, že v některých případech nastavuje záhlaví zpráv, která jsou vyžadována v některých případech, například pokud datová služba vyžaduje ověřování založené na deklaracích nebo soubory cookie. Další informace najdete v tématu [zabezpečení WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md#clientAuthentication). V těchto případech je před odesláním nutné ručně nastavit záhlaví zpráv ve zprávě požadavku. V příkladu v tomto tématu se dozvíte, jak <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zpracovat událost pro přidání nové hlavičky do zprávy požadavku předtím, než se pošle do datové služby.  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Můžete také použít ukázkovou [datovou službu Northwind](https://go.microsoft.com/fwlink/?LinkId=187426) publikovanou na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] webu. Tato ukázková datová služba je jen pro čtení a pokus o uložení změn vrátí chybu. Vzorové datové služby na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] webu umožňují anonymní ověřování.  
  
## <a name="example"></a>Příklad  
 Následující příklad zaregistruje obslužnou rutinu <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> pro událost a pak provede dotaz na datovou službu.  
  
> [!NOTE]
> Pokud datová služba vyžaduje, abyste ručně nastavili hlavičku zprávy pro každý požadavek, zvažte registraci obslužné rutiny pro <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> událost `OnContextCreated` přepsáním částečné metody v kontejneru entit, který představuje datovou službu, která je v v tomto případě `NorthwindEntities`je to.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Příklad  
 Následující metoda zpracuje <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> událost a přidá do žádosti hlavičku ověřování.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení datových služeb WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)
- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
