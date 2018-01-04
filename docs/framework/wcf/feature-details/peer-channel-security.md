---
title: "Zabezpečení rovnocenného kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c59b164-3729-44f0-a967-f247c42de662
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d9b63e4cb056cf72f2e7b4796883f3fc2873a49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="peer-channel-security"></a>Zabezpečení rovnocenného kanálu
Rovnocenného kanálu umožňuje různé typy distribuovaných aplikací, které jsou závislé na více stran zasílání zpráv. Mezi příklady patří distribuce obsahu internetových, kde důvěryhodného zdroje distribuuje obsah (například média nebo aktualizací softwaru), skupinou přátel systému exchange, Hudba a fotografie nebo tým kolegy společně upravit dokumentu. Každý z těchto scénářů vyžaduje jedinečnou modelu. Model zabezpečení rovnocenného kanálu je určen k řešení těchto scénářů a poskytuje model zabezpečení pro na potřeby odlišnými modely identitu, ověřování a autorizace.  
  
## <a name="security-scenarios"></a>Scénáře zabezpečení  
 Scénář distribuce obsahu vyžaduje, aby každý příjemce obsahu identifikovat zdroj obsahu. Z důvodu distribuovaná povaha scénář není vždy možné znáte a kterým důvěřujete dodavatelů tohoto procesu nebo krádež zprávy. Efektivně zmírnit riziko, že prostředník nedůvěryhodné mohou manipulovat s zprávy, můžete aplikace zabezpečit zprávu na odesílatele tak, aby se snadno zjistí jakékoli o zásah. V závislosti na důvěrnost obsah, v takovém případě může být šifrování nutné.  
  
 Scénáře spolupráce, jako je skupina dokumentu často spolupráce vyžadovat, aby každý člen účastní relace jednotlivě identifikovat a ověření. To znamená, že je potřeba mít zabezpečené relace mechanismus pro definování skupiny uživatelů a ověřování na základě těchto skupin. Kromě toho aplikace může vyžadovat trasování každou zprávu pomocí ověřování na úrovni zpráv. V těchto typech aplikací můžete pro silnější zabezpečení schéma odstraněny výkonu.  
  
 Relaci komunikace mezi skupiny běžné uživatelů může vyžadovat modely neformální zabezpečení, jako znalosti běžných tajný klíč mezi skupině. Pro tyto typy aplikací má model zabezpečení, který je vhodné vytvořit a nakonfigurovat je důležitější než nutnosti nejúčinnější způsob ověřování nebo zadáním nepopiratelnosti odpovědnosti míry. Pro tyto scénáře mechanismus ověřování založené na heslech pomáhá se zabezpečením komunikační vrstva zároveň umožňuje pro ověřování zpráv. Zabezpečení založené na heslech je výchozí nastavení pro rovnocenného kanálu.  
  
## <a name="token-types"></a>Typy tokenů  
 Rovnocenného kanálu rozpozná jeden typ tokenu pro silné identifikaci X.509 – certifikáty, které poskytují model silné identity na základě typu ověřování a autorizace, který může být implementováno. Důvěrnost a integrita jsou snadno uvedené pomocí certifikátů. Certifikáty X.509 však může být obtížné a nasadit použít.  
  
 Rovnocenného kanálu taky poskytuje podporu pro jednoduché aplikace pomocí hesla. Aplikace můžete nastavit skupiny rychlé a jednoduché sdílené podle zadané heslo. V takovém případě vlastník skupiny rozhodne a komunikuje heslo na členy. Každý člen musíte se přihlásit pomocí toto heslo, než bylo možné připojit k relaci. Hesla je možné jenom do relace; položku Povolit nelze použít k provedení ověřování zpráv. Je to proto symetrický token, který sdílet skupiny partnerských uzlů je obtížné a nevhodných používané při ověřování zdroje.  
  
## <a name="security-model"></a>Model zabezpečení  
 Rovnocenného kanálu poskytuje možnost zabezpečení jednotlivých propojení mezi rovnocennými počítači. To znamená, že zprávu nikdy toků v rámci nezabezpečené připojení (z pohledu aplikace). Každé propojení (kanál mezi dvěma partnery transport) je interně zabezpečené, pomocí zabezpečení TLS (Transport Layer). To znamená, že když odesílatele vytvoří a odešle zprávu, se odešle přes zabezpečené přenosu na každý z jeho okamžitou partnerské uzly, kteří přístup ke zprávě a pak odeslat zprávu svým spolupracovníkům okamžitou přes zabezpečené připojení. Tato zabezpečení funguje pouze na přenos úrovni a je nezávislý na modely zabezpečení zpráv.  
  
 Rovnocenného kanálu také poskytuje způsob, jak zabezpečit zprávy nezávisle na zabezpečení přenosu, který používá. V tomto modelu je zabezpečená zpráva na zdroji pomocí tokenu zabezpečení zdroje, ačkoliv je aktuálně jedinou certifikáty X.509. Zabezpečené zprávy je pak přenést přes síť partnera. Každý přijímající partnera můžete ověřit pravost zdroje. Všimněte si, že je zpráva zabezpečené tak, aby prostředníci nelze manipulovat s ním.  
  
 K dosažení důvěrnost, můžete použít aplikace zabezpečení přenosu s silné skupiny členství schémata znemožníte neoprávněný přístup ke zprávě.  
  
 Rovnocenného kanálu nevyžaduje konkrétní identity modelu, tak dlouho, dokud aplikace zvolí jeden z podporované typy tokenů. Aplikace úplně vlastní životní cyklus těchto identit a ověření rozhodnutí.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Koncepce protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)  
 [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
