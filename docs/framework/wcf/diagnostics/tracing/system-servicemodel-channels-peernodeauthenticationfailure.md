---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b09d7fc476d5eed7f7c534fdde46cb18eeac30d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
Bezpečnostní ověření typu handshake s potenciální sousedním nebyla úspěšná.  
  
## <a name="description"></a>Popis  
 Při pokusu o vytvoření zabezpečeného sousedním připojení dojde k trasování. K tomu dochází z důvodu nedostatečné nebo nesprávné přihlašovací údaje.  
  
 PeerChannel rozpozná jeden typ tokenu pro silné identifikaci X.509 – certifikáty, které poskytují model silné identity na základě typu ověřování a autorizace, který může být implementováno. PeerChannel taky poskytuje podporu pro jednoduché aplikace pomocí hesla. Hesla je možné jenom do relace; položku Povolit nelze použít k provedení ověřování zpráv. Je to proto symetrický token, který sdílet skupiny partnerských uzlů je obtížné a nevhodných používané při ověřování zdroje.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Zajistěte, aby všechny okolí příslušná zabezpečovací přihlašovací údaje.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení rovnocenného kanálu](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
