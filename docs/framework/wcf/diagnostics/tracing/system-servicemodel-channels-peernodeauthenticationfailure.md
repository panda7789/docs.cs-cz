---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: cb7019f1e4b47bde7c98b0109afa7b0125b7ef63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84577302"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
Bezpečnostní Metoda handshake s potenciálním sousedem nebyla úspěšná.  
  
## <a name="description"></a>Popis  
 K tomuto trasování dojde při pokusu o navázání zabezpečeného sousedního připojení. K tomu může dojít z důvodu nedostatečných nebo nesprávných přihlašovacích údajů.  
  
 PeerChannel rozpoznává jeden typ tokenu pro silnou identifikaci, a to pomocí certifikátů X. 509, které poskytují model silné identity na základě typu ověřování a autorizace, které lze implementovat. PeerChannel také poskytuje podporu pro jednoduché aplikace pomocí hesel. Hesla se dají použít jenom k povolení položky pro relaci. nelze je použít k ověření zprávy. Důvodem je to, že symetrický token, který má skupinu partnerských vztahů, je obtížné a nevhodný pro použití při ověřování zdroje.  
  
## <a name="troubleshooting"></a>Řešení potíží  
 Ujistěte se, že všechny sousední sousedi mají příslušná zabezpečovací pověření.  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení protokolem Peer Channel](../../feature-details/peer-channel-security.md)
- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
