---
title: Zpracování chyb WCF
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: d70edacd2447fbe0b0b6db42b93f699ce7c17003
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306284"
---
# <a name="wcf-error-handling"></a>Zpracování chyb WCF
Chyb zjištěných aplikací WCF patří do jedné ze tří skupin:  
  
1. Chybám komunikace  
  
2. Chyby serveru proxy nebo kanálu  
  
3. Chyby aplikace  
  
 Pokud síť není k dispozici, klient použije nesprávnou adresu nebo hostitele služby není naslouchání pro příchozí zprávy dojít k chybám komunikace. Chyby tohoto typu se vrátí ke klientovi jako <xref:System.ServiceModel.CommunicationException> nebo <xref:System.ServiceModel.CommunicationException>-odvozené třídy.  
  
 Proxy server nebo kanálu chyby jsou chyby, ke kterým dochází v rámci kanálu nebo proxy, samotného. Zahrnout chyby tohoto typu: Pokus použít proxy server nebo kanálu, který bylo ukončeno, existuje neshoda kontraktů mezi klientem a službou nebo odmítají pověření klienta službou. Existuje mnoho různých typů chyb v této kategorii pro zobrazení zde příliš mnoho. Chyby tohoto typu se vrátí ke klientovi jako-je (na objektech výjimek není provedena žádná transformace).  
  
 Při provádění operace služby dojít k chybám aplikace. Chyby tohoto druhu jsou odesílány ke klientovi jako <xref:System.ServiceModel.FaultException> nebo <xref:System.ServiceModel.FaultException%601>.  
  
 Zpracování chyb v WCF provádí jeden nebo více z následujících akcí:  
  
-   Přímo zpracování výjimky. To je pouze pro komunikaci a chyby proxy nebo kanálu.  
  
-   Použití kontraktů selhání  
  
-   Implementace <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní  
  
-   Zpracování <xref:System.ServiceModel.ServiceHost> události  
  
## <a name="fault-contracts"></a>Kontrakty selhání  
 Kontrakty selhání umožňují definovat chyby, které se můžou objevit během operace služby na platformě nezávisle. Ve výchozím nastavení budou vráceny všechny výjimky vyvolané z v rámci operace služby ke klientovi jako <xref:System.ServiceModel.FaultException> objektu. <xref:System.ServiceModel.FaultException> Objekt bude obsahovat velmi málo informací. Můžete určit informace o klientovi definováním kontrakt chyby a vrátí chyba jako <xref:System.ServiceModel.FaultException%601>. Další informace najdete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>IErrorHandler  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler> Rozhraní vám umožní větší kontrolu nad jak aplikaci WCF reagují na chyby.  Poskytuje plnou kontrolu nad chybová zpráva, která je vrácen do klienta a umožňuje provádět vlastní chyba při zpracování jako je například protokolování.  Další informace o <xref:System.ServiceModel.Dispatcher.IErrorHandler> a [rozšíří ovládací prvek průběhu zpracování chyb a vytváření sestav](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)  
  
## <a name="servicehost-events"></a>ServiceHost Events  
 <xref:System.ServiceModel.ServiceHost> Třída hostitele služby a definuje několik událostí, které mohou být nezbytné pro zpracování chyb. Příklad:  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 Další informace naleznete v tématu <xref:System.ServiceModel.ServiceHost>
