---
title: Zpracování chyb WCF
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 7e5c65da3fa13a3640c7a6948f1284d0c6ffdfc4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319933"
---
# <a name="wcf-error-handling"></a>Zpracování chyb WCF
Chyby zjištěné aplikací WCF patří do jedné ze tří skupin:  
  
1. Chyby komunikace  
  
2. Chyby proxy/kanálu  
  
3. Chyby aplikace  
  
 K chybám komunikace dojde, když síť není k dispozici, klient používá nesprávnou adresu, nebo hostitel služby nenaslouchá příchozím zprávám. Chyby tohoto typu jsou vraceny klientovi jako <xref:System.ServiceModel.CommunicationException> nebo @no__t třídy odvozené od -1.  
  
 Chyby proxy/kanálu jsou chyby, ke kterým dochází v rámci samotného kanálu nebo proxy serveru. Mezi chyby tohoto typu patří: pokus o použití proxy serveru nebo kanálu, který byl uzavřen, existuje neshoda kontraktu mezi klientem a službou nebo přihlašovací údaje klienta jsou službou odmítnuty. Existuje mnoho různých typů chyb v této kategorii, takže seznam je příliš velký. Chyby tohoto typu jsou vraceny klientovi, jak je (žádná transformace není provedena na objektech výjimek).  
  
 Při provádění operace služby dojde k chybám aplikace. Chyby tohoto druhu jsou odesílány klientovi jako <xref:System.ServiceModel.FaultException> nebo <xref:System.ServiceModel.FaultException%601>.  
  
 Zpracování chyb v WCF je prováděno jedním nebo více z následujících způsobů:  
  
- Přímo se zpracovává vyvolaná výjimka. To se provádí jenom pro chyby komunikace a proxy/kanálu.  
  
- Použití smluv o selhání  
  
- Implementace rozhraní <xref:System.ServiceModel.Dispatcher.IErrorHandler>  
  
- Zpracování událostí <xref:System.ServiceModel.ServiceHost>  
  
## <a name="fault-contracts"></a>Smlouvy o selhání  
 Smlouvy o selhání umožňují definovat chyby, ke kterým může dojít během operace služby, a to nezávisle na platformě. Ve výchozím nastavení budou všechny výjimky vyvolané v rámci operace služby vráceny klientovi jako objekt <xref:System.ServiceModel.FaultException>. Objekt <xref:System.ServiceModel.FaultException> bude obsahovat velmi málo informací. Můžete řídit informace odesílané klientovi tak, že definujete kontrakt chyby a vrátíte chybu jako <xref:System.ServiceModel.FaultException%601>. Další informace najdete v tématu [určení a zpracování chyb v kontraktech a službách](specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>IErrorHandler  
 Rozhraní <xref:System.ServiceModel.Dispatcher.IErrorHandler> umožňuje větší kontrolu nad tím, jak vaše aplikace WCF reaguje na chyby.  Poskytuje plnou kontrolu nad chybovou zprávou vrácenou klientovi a umožňuje provádět vlastní zpracování chyb, jako je protokolování.  Další informace o @no__t 0 a [rozšíření kontroly nad zpracováním chyb a vytváření sestav](./samples/extending-control-over-error-handling-and-reporting.md)  
  
## <a name="servicehost-events"></a>Události ServiceHost  
 Třída <xref:System.ServiceModel.ServiceHost> hostuje služby a definuje několik událostí, které mohou být potřeba ke zpracování chyb. Příklad:  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 Další informace najdete v tématu <xref:System.ServiceModel.ServiceHost>.
