---
title: Zabezpečení rovnocenného kanálu
ms.date: 03/30/2017
ms.assetid: 2c59b164-3729-44f0-a967-f247c42de662
ms.openlocfilehash: f8015f41254d17f908f3665db65af3d82eaa2b6a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576080"
---
# <a name="peer-channel-security"></a>Zabezpečení rovnocenného kanálu
Partnerský kanál umožňuje nejrůznější typy distribuovaných aplikací, které jsou závislé na zasílání zpráv s více částmi. Mezi příklady patří distribuce obsahu v internetovém měřítku, kde důvěryhodný zdroj distribuuje obsah (například multimédia nebo aktualizace softwaru), skupinu přátel, kteří si vyměňují hudbu a fotky nebo tým spolupracujících spolupracujících s dokumentem. Každý z těchto scénářů vyžaduje jedinečný model zabezpečení. Model zabezpečení pro rovnocenné kanály je navržený tak, aby řešení těchto scénářů a poskytoval model zabezpečení pro příslušné potřeby různých modelů identity, ověřování a autorizace.  
  
## <a name="security-scenarios"></a>Scénáře zabezpečení  
 Scénář distribuce obsahu vyžaduje, aby každý příjemce obsahu identifikoval zdroj obsahu. Z důvodu distribuované povahy scénáře není vždy možné znát a důvěřovat zprostředkovatelům, kteří zpracovávají nebo zachycují zprávy. Aby bylo možné efektivně zmírnit riziko, že nedůvěryhodný zprostředkovatel může manipulovat se zprávami, aplikace mohou zabezpečit zprávu odesílatelem, aby byly snadno zjištěny jakékoli pokusy o manipulaci. V takovém případě může být šifrování nutné v závislosti na důvěrnosti obsahu.  
  
 Scénáře spolupráce, jako je spolupráce s dokumenty skupiny, často vyžadují, aby se každý člen účastnící se relace jednotlivě identifikoval a ověřil. To znamená, že mechanismus pro definování skupin uživatelů a ověřování u těchto skupin je nezbytný k tomu, aby měl zabezpečenou relaci. Kromě toho můžou aplikace vyžadovat trasování každé zprávy podle ověření na úrovni zprávy. V těchto typech aplikací může být výkon u silnějšího schématu zabezpečení usmrcen.  
  
 Komunikační relace mezi skupinou příležitostného uživatele může vyžadovat neformální modely zabezpečení, jako je například znalost společného tajného klíče mezi skupinou. U těchto typů aplikací je model zabezpečení, který je vhodný pro navázání a konfiguraci, důležitější, než má nejúčinnější formu ověřování nebo poskytnutí neneodvolatelnosti měr. V těchto scénářích pomáhá mechanismus ověřování založený na heslech zabezpečit komunikační vrstvu a zároveň umožnit ověřování zpráv. Zabezpečení založené na heslech je výchozí nastavení pro rovnocenný kanál.  
  
## <a name="token-types"></a>Typy tokenů  
 Partnerský kanál rozpoznává jeden typ tokenu pro silnou identifikaci certifikátů X. 509, které poskytují model silné identity na základě typu ověřování a autorizace, které lze implementovat. Důvěrnost a integrita se snadno poskytují pomocí certifikátů. Certifikáty X. 509 ale můžou být obtížné použít a nasadit.  
  
 Partnerský kanál také poskytuje podporu pro jednoduché aplikace pomocí hesel. Aplikace se můžou rozhodnout pro nastavení rychlých a jednoduchých partnerských skupin na základě zadaného hesla. V takovém případě se vlastník skupiny rozhodne a sdělí heslo pro členy. Každý člen se musí přihlásit pomocí tohoto hesla, aby se mohl připojit k relaci. Hesla se dají použít jenom k povolení položky pro relaci. nelze je použít k ověření zprávy. Důvodem je to, že symetrický token, který má skupinu partnerských vztahů, je obtížné a nevhodný pro použití při ověřování zdroje.  
  
## <a name="security-model"></a>Model zabezpečení  
 Partnerský kanál nabízí možnost zabezpečit jednotlivá propojení mezi partnerskými uzly. To znamená, že zpráva nikdy nepokračuje na nezabezpečeném odkazu (z perspektivy aplikace). Interně je každý odkaz (transportní kanál mezi dvěma partnerskými uzly) zabezpečený pomocí protokolu TLS (Transport Layer Security). To znamená, že když odesilatel vytvoří a pošle zprávu, pošle se přes zabezpečený přenos do každého z jeho bezprostředních partnerských uzlů, kteří budou přistupovat ke zprávě, a zase pošle zprávu svým bezprostředním partnerům přes zabezpečená připojení. Toto zabezpečení funguje pouze na úrovni přenosu a je nezávislé na modelech zabezpečení zpráv.  
  
 Partnerský kanál také poskytuje způsob, jak zabezpečit zprávy nezávisle na používaném zabezpečení přenosu. V tomto modelu je zpráva zabezpečená ve zdroji pomocí tokenu zabezpečení zdroje, i když jsou teď podporované jenom certifikáty X. 509. Zabezpečená zpráva se pak přenáší přes síť partnera. Každý přijímající partner může ověřit pravost zdroje. Všimněte si, že zpráva je zabezpečená, aby je s ní nemohly prostředníkem manipulovat.  
  
 Pro zajištění důvěrnosti můžou aplikace využívat zabezpečení přenosu se silnými systémy členství ve skupině, aby se zabránilo neoprávněnému přístupu ke zprávě.  
  
 Partnerský kanál nevyžaduje konkrétní model identity, pokud aplikace zvolí jeden z podporovaných typů tokenu. Aplikace zcela vlastní životní cyklus těchto identit a rozhodnutí o ověřování.  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení aplikací rovnocenného kanálu](securing-peer-channel-applications.md)
- [Koncepce protokolu Peer Channel](peer-channel-concepts.md)
- [Vytvoření aplikace protokolu Peer Channel](building-a-peer-channel-application.md)
