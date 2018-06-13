---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 633f497950ab14d7715537eed8f5cc80e7a350a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33479850"
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
