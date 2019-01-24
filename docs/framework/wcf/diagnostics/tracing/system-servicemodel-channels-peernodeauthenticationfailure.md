---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 1ed037c548f1d833f2a20118ee1e017cd19e3391
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628237"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
Bezpečnostní ověření typu handshake s potenciální souseda nebyla úspěšná.  
  
## <a name="description"></a>Popis  
 Vyvolá se při pokusu o navázání připojení k sousedovi zabezpečené tohoto trasování. K tomu může dojít z důvodu nedostatečné nebo nesprávné přihlašovací údaje.  
  
 Kanál PeerChannel rozpozná jeden typ tokenu pro silné identifikaci certifikáty X.509, které poskytují model využívá silné identity na základě typu ověřování a autorizaci, které je možné implementovat. Kanál PeerChannel také poskytuje podporu pro jednoduché aplikace pomocí hesla. Hesla je možné pouze do relace; položku Povolit nelze použít k provedení ověřování zpráv. Je to proto, že symetrický token, které sdílejí skupiny partnerských uzlů je obtížné a nevhodný pro účely ověření zdroje.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Ujistěte se, že všechny sousední mají příslušná zabezpečovací přihlašovací údaje.  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečení protokolem Peer Channel](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
