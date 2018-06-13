---
title: 'Postupy: nastavení hlavičky v požadavku klienta (služby WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: e6b9b01f18e8412857a38a8e22fadfa88faf9d24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361783"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Postupy: nastavení hlavičky v požadavku klienta (služby WCF Data Services)
Při použití [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny pro přístup ke službě data, která podporuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], klientské knihovny automaticky nastaví požadované hlavičky HTTP v žádosti o zprávy odeslané do služby data. Klientská knihovna však neví nastavit hlavičky zpráv, které jsou potřeba v některých případech, například když službu data vyžaduje ověřování založené na deklaracích nebo soubory cookie. Další informace najdete v tématu [zabezpečení služby WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md#clientAuthentication). V těchto případech musíte ručně nastavit hlavičky zpráv ve zprávě požadavku, před odesláním. V příkladu v tomto tématu ukazuje způsob zpracování <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> událost, která má-li přidat nový hlavičku do zprávu požadavku, před odesláním do služby data.  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Můžete také [Northwind ukázková data služby](http://go.microsoft.com/fwlink/?LinkId=187426) , je publikována na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] webu; Tato ukázková data služby je jen pro čtení a pokus o uložení změn vrátí chybu. Ukázková data služby na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] webu povolit anonymní ověřování.  
  
## <a name="example"></a>Příklad  
 Následující příklad zaregistruje obslužnou rutinu <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> událostí a potom provede dotaz na službu data.  
  
> [!NOTE]
>  Při datové služby, musíte ručně nastavit záhlaví zprávy pro každý požadavek, vezměte v úvahu obslužnou rutinu pro registraci <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> událostí přepsáním `OnContextCreated` služby částečné metoda v kontejneru entit, který představuje data, která v je v tomto případě `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Příklad  
 Následující metoda zpracovává <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> událostí a přidá hlavičku ověřování k této žádosti.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení datových služeb WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
