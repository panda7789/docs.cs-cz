---
title: "Zpracování chyb WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26dfea83400b5d601fabc5cfb52bc71a4d5e4f6f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-error-handling"></a>Zpracování chyb WCF
Chyby, kterými aplikace WCF patřit do jedné ze tří skupin:  
  
1.  Chyby komunikace  
  
2.  Proxy server/kanál chyby  
  
3.  Chyby aplikace  
  
 Dochází k chybám komunikace, když síť není k dispozici, klient používá adresu nesprávný nebo hostitele služby nenaslouchá pro příchozí zprávy. Chyby tohoto typu se vrátí klientovi jako <xref:System.ServiceModel.CommunicationException> nebo <xref:System.ServiceModel.CommunicationException>-odvozených třídách.  
  
 Proxy server/kanál chyby jsou chyby, které se vyskytují v kanálu nebo proxy, sám sebe. Chyby tohoto typu patří: pokouší použít server proxy nebo kanálu, který byl uzavřen, existuje neshoda kontrakt mezi klientem a službou nebo odmítne pověření klienta služby. Existuje mnoho různých typů chyb v této kategorii příliš mnoho seznam sem. Chyby tohoto typu se vrátí klientovi jako-je (na objekty výjimek není provedena žádná transformace).  
  
 Chyby aplikace, ke kterým došlo během provádění operace služby. Chyby tohoto druhu, jsou odeslány klientovi jako <xref:System.ServiceModel.FaultException> nebo <xref:System.ServiceModel.FaultException%601>.  
  
 Zpracování chyb v WCF se provádí jednou nebo více z následujících akcí:  
  
-   Přímo zpracování došlo k výjimce. Důvodem je pouze pro komunikaci a proxy serveru nebo kanály.  
  
-   Použití kontraktů selhání  
  
-   Implementace <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní  
  
-   Zpracování <xref:System.ServiceModel.ServiceHost> události  
  
## <a name="fault-contracts"></a>Kontrakty selhání  
 Kontrakty selhání umožňují definovat chybách, ke kterým může dojít během operace služby na platformě nezávislý způsobem. Ve výchozím nastavení všechny výjimky vyvolány z v rámci operace služby bude vrácen do klienta jako <xref:System.ServiceModel.FaultException> objektu. <xref:System.ServiceModel.FaultException> Objektu bude obsahovat velmi málo informací. Můžete řídit informace odesílané do klienta definování kontraktu odolnost a vrací chybu jako <xref:System.ServiceModel.FaultException%601>. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Určování a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>IErrorHandler  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler> Rozhraní vám umožní větší kontrolu nad jak aplikace WCF reagují na chyby.  Nabízí plnou kontrolu nad chybová zpráva, která je vrácen do klienta a umožňuje provádět vlastní chyba při zpracování například protokolování.  [!INCLUDE[crdefault](../../../includes/crabout-md.md)]<xref:System.ServiceModel.Dispatcher.IErrorHandler> a [rozšíření kontroly nad zpracováním a vykazováním chyb](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)  
  
## <a name="servicehost-events"></a>Hostitel služby události  
 <xref:System.ServiceModel.ServiceHost> Třídy hostitelů služby a definuje několik událostí, které mohou být potřebné pro zpracování chyb. Příklad:  
  
1.  <!--zz <xref:System.ServiceModel.ServiceHost.Faulted>-->  `System.ServiceModel.ServiceHost.Faulted`
  
2. <!--zz  <xref:System.ServiceModel.ServiceHost.UnknownMessageReceived>  --> `System.ServiceModel.ServiceHost.UnknownMessageReceived`
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<xref:System.ServiceModel.ServiceHost>
