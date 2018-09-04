---
title: 'Postupy: nastavení hlaviček v požadavku klienta (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 659bbb81f0ff36d99b5b836b50dfd229b39f2d5c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505286"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Postupy: nastavení hlaviček v požadavku klienta (WCF Data Services)
Při použití [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientskou knihovnu pro přístup ke službě data, která podporuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], klientské knihovny automaticky nastaví povinné hlavičky HTTP v žádosti o zprávy odeslané do datové služby. Klientská knihovna však nezná nastavit hlavičky zpráv, které jsou nutné v některých případech, například když datová služba vyžaduje ověřování nezaloženého na deklaracích nebo soubory cookie. Další informace najdete v tématu [zabezpečení služeb WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md#clientAuthentication). V těchto případech je nutné ručně nastavit hlavičky zpráv ve zprávě požadavku před jejím odesláním. V příkladu v tomto tématu ukazuje, jak zpracovat <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> události a přidejte novou hlavičku zprávy s požadavkem, před odesláním do datové služby.  
  
 V příkladu v tomto tématu se používá Northwind ukázková data service a automaticky vygenerovaných tříd klientské datové služby. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Můžete také použít [ukázková datová služba Northwind](https://go.microsoft.com/fwlink/?LinkId=187426) , který je publikovaný na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] webové stránky; Tato ukázková data service je jen pro čtení a pokusu o uložení změny vrátí chybu. Ukázková data services – na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] webovou stránku Povolit anonymní ověřování.  
  
## <a name="example"></a>Příklad  
 Následující příklad registruje obslužnou rutinu pro <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> události a pak provede dotaz na datovou službu.  
  
> [!NOTE]
>  Když datové služby je potřeba ručně nastavte záhlaví zprávy pro každý požadavek, vezměte v úvahu registruje se obslužná rutina pro <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> události tak, že přepíšete `OnContextCreated` služby částečné metody v kontejneru entity, která představuje data, která v Tento případ je `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Příklad  
 Následující metoda obslužné rutiny <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> událostí a přidá hlavičku ověřování k této žádosti.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení datových služeb WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
