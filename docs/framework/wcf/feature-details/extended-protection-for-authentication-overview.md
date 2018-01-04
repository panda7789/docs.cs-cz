---
title: "Rozšířená ochrana pro ověřování – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d2ceffe-a7bf-4bd9-a5a2-9406423bd7f8
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b061f9395c3917c196030678ede007071e681027
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="extended-protection-for-authentication-overview"></a>Rozšířená ochrana pro ověřování – přehled
Rozšířená ochrana ověřování pomáhá chránit před útoky (typu MITM) man-in-the-middle, ve kterých útočník zachytává klientské přihlašovací údaje a předává je na server.  
  
 Představte si třeba situaci s tři účastníky: klienta, serveru a útočník. Adresa URL má server `https://server`, zatímco útočník má adresu URL `https://attacker`. Útočník triky klienta do přístup k útočník, jako kdyby nebylo serveru. Útočník pak odešle požadavek na server. Pokud útočník se pokouší o přístup k prostředkům zabezpečené, serveru reaguje na útočník s hlavička WWW-Authenticate. Útočník nemá informace o ověřování, takže odešle hlavička WWW-Authenticate ke klientovi. Klient odešle hlavičku autorizace útočník a útočník odesílá hlavičku k serveru a získá přístup k zabezpečeným prostředkům pomocí pověření klienta.  
  
 V současné době při klientskou aplikaci se ověří na serveru pomocí protokolu Kerberos, Digest nebo protokol NTLM pomocí protokolu HTTPS, je nejprve vytvořit kanál úroveň zabezpečení TLS (Transport) a ověřování probíhá pomocí tohoto kanálu. Však neexistuje žádná vazba mezi vygenerované nástrojem vrstvy SSL (Secure Sockets) klíč relace a klíč relace, který je generován během ověřování. Ano, v předchozím scénáři, pokud komunikaci přes protokol TLS (např. kanál protokolu HTTPS), trvá místech existují dvě SSL kanály, vytvořit: jeden mezi klientem a útočník a jiné mezi útočník a serverem. Pověření klienta jsou odeslaných z klienta na server nejprve prostřednictvím kanálu SSL mezi klientem a útočník a pak přes kanál mezi útočník a serverem. Jakmile pověření klienta připojit k serveru, server ověřuje přihlašovací údaje bez zjišťování, jestli se útočník a není klient pochází kanál, přes které byly odeslány tyto přihlašovací údaje.  
  
 Řešení je k používání vnější kanál TLS zabezpečené a ověření klienta vnitřní kanálem a předat kanálu vazby tokenu (CBT) serveru. CBT vlastnost zabezpečené TLS vnější kanál a slouží pro vazbu vnější kanál ke konverzaci přes kanál vnitřní ověření klienta.  
  
 V předchozím scénáři je CBT TLS kanálu klienta útočník sloučen s informace o ověření, která je odeslána na server. Server využívající technologii CBT porovná CBT obsažené v informace o ověřování klienta odpovídá klienta útočník kanál, do CBT připojená ke kanálu útočník serveru. CBT je specifické pro cílové kanál, takže útočník klienta CBT neodpovídá server útočník CBT. To umožňuje serveru zjistit útoky typu MITM a odmítnout žádosti o ověření.  
  
 Na straně klienta nevyžaduje žádné nastavení konfigurace. Jakmile klient byl aktualizovaný, aby CBT předat serveru, vždy dělá to tak. Pokud server také aktualizován, dá se použít CBT nebo ji ignorovat. Pokud se neaktualizovala, ignoruje se.  
  
 Server může mít následující úrovně ochrany:  
  
-   Žádné Žádný kanál vazby ověřování. Toto chování se použije ve všech serverech, které nebyly aktualizovány.  
  
-   Částečné. Všichni klienti, které byly aktualizovány musíte zadat informace o vazbě kanál k serveru. Uděláte to tak nemají klienti, které nebyly aktualizovány. Toto je zprostředkující možnost, která umožňuje pro kompatibilitu aplikací.  
  
-   Úplná. Všichni klienti musíte zadat informace o vazbě kanálu. Server odmítne ověřování přicházejících od klientů, které nejsou tak učinit.  
  
 Další informace najdete v tématu ukázka Win7 CBT/Rozšířená ochrana.  
  
## <a name="see-also"></a>Viz také  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
