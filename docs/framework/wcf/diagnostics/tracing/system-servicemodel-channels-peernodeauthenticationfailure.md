---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 315122914ebcb3e8e4d72c8d976026a126306168
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219002"
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
