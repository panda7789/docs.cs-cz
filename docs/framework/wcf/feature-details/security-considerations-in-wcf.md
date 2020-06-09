---
title: Důležité informace o zabezpečení ve službě WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: ed0f018e0151e68afeb9a4747bf8a260faa184b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601033"
---
# <a name="security-considerations-in-wcf"></a>Důležité informace o zabezpečení ve službě WCF
Témata v této části uvádějí různé položky související se zabezpečením, které je potřeba vzít v úvahu při navrhování aplikace Windows Communication Foundation (WCF).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zpřístupnění informací](information-disclosure.md)  
 Tento článek popisuje různé způsoby, jak mohou být informace zveřejněné nebo napadené a jak je zmírnit.  
  
 [Zvýšení oprávnění](elevation-of-privilege.md)  
 Tento článek popisuje důsledky udělení oprávnění k autorizaci útočníka nad rámec původně udělených a jak ho zmírnit.  
  
 [Útok DoS](denial-of-service.md)  
 Popisuje, co se stane, když systém nemůže správně zpracovat zprávy a jak ho zmírnit.  
  
 [Falšování](tampering.md)  
 Popisuje změny zpráv nebo doručování zpráv a jejich omezení.  
  
 [Útoky opakováním](replay-attacks.md)  
 Tento článek popisuje, co se stane, když útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehraje datový proud na jednu nebo více smluvních stran, a jak to zmírnit.  
  
 [Důležité informace o zabezpečení pro zabezpečené relace](security-considerations-for-secure-sessions.md)  
 Popisuje následující položky, které mají vliv na zabezpečení při implementaci zabezpečených relací.  
  
 [Nepodporované scénáře](unsupported-scenarios.md)  
 Obsahuje seznam různých scénářů, které nepodporují konkrétní aspekt zabezpečení a je třeba se vyhnout nebo je zvážit.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Související oddíly  
 [Informace o zabezpečení a doporučené postupy](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení](security.md)
