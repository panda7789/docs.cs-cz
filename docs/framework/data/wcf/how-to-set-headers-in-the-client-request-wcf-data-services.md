---
title: 'Postup: Nastavení záhlaví v požadavku klienta (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 9267f0e5b68823516764891a40e1435c1325b77f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174339"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Postup: Nastavení záhlaví v požadavku klienta (WCF Data Services)
Při použití klientské knihovny WCF Data Services pro přístup k datové službě, která podporuje protokol OData (Open Data Protocol), klientská knihovna automaticky nastaví požadované hlavičky HTTP v požadavcích zpráv odeslaných datové službě. Klientská knihovna však neví, nastavit záhlaví zpráv, které jsou požadovány v určitých případech, například když datová služba vyžaduje ověřování založené na deklaracích identity nebo soubory cookie. Další informace naleznete [v tématu Zabezpečení služby WCF Data Services](securing-wcf-data-services.md#clientAuthentication). V těchto případech je nutné ručně nastavit záhlaví zpráv ve zprávě požadavku před odesláním. Příklad v tomto tématu ukazuje, jak zpracovat <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> událost přidat novou hlavičku do zprávy požadavku před odesláním datové službě.  
  
 Příklad v tomto tématu používá ukázkovou datovou službu Northwind a třídy automaticky generovaných klientských datových služeb. Tato služba a třídy dat klienta jsou vytvořeny po dokončení [rychlého startu služby WCF Data Services](quickstart-wcf-data-services.md). Můžete také použít [ukázkovou datovou službu Northwind,](https://services.odata.org/Northwind/Northwind.svc/) která je publikována na webu OData; Tato ukázková datová služba je jen pro čtení a pokus o uložení změn vrátí chybu. Ukázkové datové služby na webu OData umožňují anonymní ověřování.  
  
## <a name="example"></a>Příklad  
 Následující příklad zaregistruje obslužnou rutinu <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> pro událost a potom provede dotaz proti datové službě.  
  
> [!NOTE]
> Pokud datová služba vyžaduje ruční nastavení záhlaví zprávy pro každý požadavek, <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zvažte registraci obslužné rutiny pro událost přepsáním `OnContextCreated` částečné metody v kontejneru entity, která představuje datovou službu, což je `NorthwindEntities`v tomto případě .  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Příklad  
 Následující metoda zpracovává <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> událost a přidá záhlaví ověřování k požadavku.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení datových služeb WCF Data Services](securing-wcf-data-services.md)
- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
