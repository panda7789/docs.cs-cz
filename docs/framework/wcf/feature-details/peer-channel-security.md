---
title: Zabezpečení rovnocenného kanálu
ms.date: 03/30/2017
ms.assetid: 2c59b164-3729-44f0-a967-f247c42de662
ms.openlocfilehash: 09979cee48522355631c79e0bdf4c0fba6be782e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541752"
---
# <a name="peer-channel-security"></a>Zabezpečení rovnocenného kanálu
Rovnocenný kanál umožňuje různé typy distribuovaných aplikací, které jsou závislé na éře zasílání zpráv. Mezi příklady patří distribuce obsahu internetovém měřítku, kde důvěryhodným zdrojem slouží k distribuci obsahu (jako jsou média nebo aktualizací softwaru), skupinou přátel vyměnit music a fotografie nebo tým vaši kolegové spolupracovat úpravy dokumentu. Každý z těchto scénářů vyžaduje jedinečnou model. Model zabezpečení rovnocenného kanálu je navržená k řešení těchto scénářů a poskytuje model zabezpečení pro příslušné potřebám různých modelů identity, ověřování a autorizace.  
  
## <a name="security-scenarios"></a>Scénáře zabezpečení  
 Scénář distribuce obsahu vyžaduje, aby každý příjemce obsahu identifikovat zdroj obsahu. Z důvodu distribuovaná povaha scénář není vždy možné znáte a kterým důvěřujete dodavatelů tohoto procesu nebo zachycení zpráv. Efektivně zmírnit hrozby, které prostředník nedůvěryhodné mohou manipulovat s zprávy, můžete aplikace zabezpečit zprávu na odesílatele tak, aby se snadno zjistí všechny zneužitím pokusy. V takovém případě v závislosti na důvěrnost obsah šifrování může být potřeba.  
  
 Scénáře využívající spolupráci, jako jsou skupiny dokumentu spolupráci často vyžaduje, aby každý člen účastní relace se jednotlivě identifikovat a ověření. To znamená, že mechanismus k definování skupin uživatelů a ověřování na základě těchto skupin je potřeba mít zabezpečenou relaci. Kromě toho aplikace mohou vyžadovat trasování každou zprávu pomocí ověřování na úrovni zprávy. V těchto typech aplikací může být výkon publikovaný silnější zabezpečení systému.  
  
 Relace komunikace mezi skupinu příležitostné uživatelů může vyžadovat modely neformální zabezpečení, jako je znalost běžné tajného klíče mezi skupině. Pro tyto typy aplikací je mnohem důležitější než s nejúčinnější způsob ověřování nebo které uvádějí neodvolatelnost míry s model zabezpečení, který je vhodné vytvořit a nakonfigurovat. Pro tyto scénáře mechanismus ověřování pomocí hesla pomáhá se zabezpečením komunikační vrstva zároveň umožní pro ověřování zpráv. Zabezpečení založené na heslech je výchozí nastavení pro rovnocenného kanálu.  
  
## <a name="token-types"></a>Typy tokenů  
 Rovnocenný kanál rozpozná jeden typ tokenu pro silné identifikaci certifikáty X.509, které poskytují model využívá silné identity na základě typu ověřování a autorizaci, které je možné implementovat. Důvěrnost a integrita jsou snadno k dispozici pomocí certifikátů. Certifikáty X.509 však může být obtížně používala a nasadíme.  
  
 Rovnocenný kanál také poskytuje podporu pro jednoduché aplikace pomocí hesla. Aplikace můžete nastavit rychlé a jednoduché rovnocennými skupinami na základě zadaného hesla. V takovém případě vlastník skupiny rozhodne a komunikuje heslo na členy. Každý člen musíte se přihlásit pomocí tohoto hesla předtím, než bylo možné připojit ke relace. Hesla je možné pouze do relace; položku Povolit nelze použít k provedení ověřování zpráv. Je to proto, že symetrický token, které sdílejí skupiny partnerských uzlů je obtížné a nevhodný pro účely ověření zdroje.  
  
## <a name="security-model"></a>Model zabezpečení  
 Rovnocenný kanál umožňuje zabezpečit jednotlivé odkazy mezi rovnocennými počítači. To znamená, že zpráva nikdy toky na nezabezpečenou odkaz (z hlediska aplikací). Interně každý odkaz (přenosový kanál mezi dva partnerské uzly) je zabezpečený pomocí zabezpečení TLS (Transport Layer). To znamená, že pokud odesílatel lze kombinovat a odešle zprávu, to se odesílají prostřednictvím zabezpečeného přenosu u každého okamžité partneři, kteří přístup ke zprávě a pak odeslat zprávu do jejich okamžité partnerské uzly přes zabezpečené připojení. Toto zabezpečení funguje pouze na přenos na úrovni a je nezávislý na modely zabezpečení zprávy.  
  
 Rovnocenný kanál také poskytuje způsob, jak zabezpečit zprávy bez ohledu na jejich zabezpečení přenosu použít. V tomto modelu je zpráva zabezpečena na zdroj, který používá token zabezpečení zdroj, i když jsou podporovaná momentálně se podporuje jenom certifikáty X.509. Zabezpečené zprávy je pak přenést přes síť partnera. Každý přijímajícího partnera můžete ověřit pravost zdroje. Všimněte si, že je zpráva zabezpečena, takže prostředníci nelze manipulovat s ním.  
  
 K zajištění důvěrnosti, můžete využívat aplikace zabezpečení přenosu se schématy členství silné skupiny k zabránění neoprávněnému přístupu ke zprávě.  
  
 Protokolu peer Channel nevyžaduje konkrétní identitu modelu, tak dlouho, dokud aplikace vybere jeden z podporovaných typů tokenu. Aplikace zcela vlastní životní cyklus těchto identit a ověřování rozhodnutí.  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečení aplikací protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [Koncepce protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
