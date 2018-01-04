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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ffca9a587bdb32afc252f9719eb35e3139dd3f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
Bezpečnostní ověření typu handshake s potenciální sousedním nebyla úspěšná.  
  
## <a name="description"></a>Popis  
 Při pokusu o vytvoření zabezpečeného sousedním připojení dojde k trasování. K tomu dochází z důvodu nedostatečné nebo nesprávné přihlašovací údaje.  
  
 PeerChannel rozpozná jeden typ tokenu pro silné identifikaci X.509 – certifikáty, které poskytují model silné identity na základě typu ověřování a autorizace, který může být implementováno. PeerChannel taky poskytuje podporu pro jednoduché aplikace pomocí hesla. Hesla je možné jenom do relace; položku Povolit nelze použít k provedení ověřování zpráv. Je to proto symetrický token, který sdílet skupiny partnerských uzlů je obtížné a nevhodných používané při ověřování zdroje.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Zajistěte, aby všechny okolí příslušná zabezpečovací přihlašovací údaje.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení protokolem Peer Channel](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
