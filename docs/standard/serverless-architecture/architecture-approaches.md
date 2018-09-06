---
title: Architektura přístupy – aplikace bez serveru
description: Úvod do architektury přístupů pro podnikové cloudové aplikace, z N-vrstvou architekturu v Azure k bez serveru.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 21e191f17e7d0b4f2d64454fb14c46a4831a8375
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875896"
---
# <a name="architecture-approaches"></a>Přístupy k architektuře

Principy existujících přístupů k navrhování firemních aplikací pomáhá vysvětlit roli hrají bez serveru. Existuje mnoho přístupů a vzory, které se za desítky let vývoje softwaru, a všechny mají své vlastní výhody a nevýhody. V mnoha případech ultimate řešení nemusí zahrnovat rozhodování o jeden přístup, ale může integrovat několik přístupů. Scénáře migrace často zahrnuje posun od jednoho architektura přístupu do jiné prostřednictvím s hybridním přístupem.

Tato kapitola obsahuje přehled oba vzorky logické a fyzické architektura pro podnikové aplikace.

## <a name="architecture-patterns"></a>Vzory architektury

Moderní firemní aplikace podle různých vzory architektury. Tato část představuje přehled běžných vzorů. Tyto vzory se dají tady nejsou nutně všechny osvědčené postupy, ale ukazují různé přístupy.

Další informace najdete v tématu [Průvodce architekturou aplikací Azure](https://docs.microsoft.com/azure/architecture/guide/).

## <a name="monoliths"></a>Monolitické

Mnoho obchodních aplikací se řídí vzorem monolitu. Starší aplikace, které jsou často implementovány jako monolitické. Ve vzoru monolitu všechny aspekty aplikace jsou obsaženy v jednom nasazení. Všechno, co z uživatelského rozhraní pro volání databáze je součástí stejného základu kódu.

![Architektura monolitu](./media/monolith-architecture.png)

Existuje několik výhod přístupu monolitu. Často je snadné stáhne z jediného základu kódu a začít pracovat. Doba přípravy může být menší, a vytvoření testovací prostředí je stejně jednoduché jako novou kopii. Monolitu může být navržena pro zahrnutí více komponent a aplikací.

Bohužel se obvykle vzor monolitu rozdělit ve velkém měřítku. Hlavní nevýhody monolitu přístupu patří:

* Obtížně pracovat souběžně ve stejném základu kódu.
* Všechny změny, bez ohledu na to, jak jednoduché, vyžaduje nasazení nové verze celé aplikace.
* Refaktoring potenciálně ovlivňuje celou aplikaci.
* Často pouze řešení škálování, je vytvořit víc kopií náročná monolitu.
* Jak rozbalit systémy nebo jinými systémy pořízené, integrace může být obtížné.
* Může být obtížné testu kvůli nutnosti konfigurace celý monolitu.
* Opakované využívání kódu je náročné a často další aplikace skončit s vlastní kopie kódu.

Řada podniků pohlížet jako příležitost k migraci monolitu aplikací a současně refaktorace na další použitelné modely do cloudu. Je běžné rozdělit jednotlivých aplikací a součástí, aby se mohly být udržovány, nasadit a škálovat samostatně.

## <a name="n-layer-applications"></a>Aplikací vrstvy N

Aplikací vrstvy N oddílu aplikace logiky do konkrétní vrstvy. Nejběžnější vrstvy patří:

* Uživatelské rozhraní
* Obchodní logika
* Přístup k datům

Middleware, dávkové zpracování a rozhraní API může obsahovat další vrstvy. Je důležité si uvědomit, že jsou logické vrstvy. I když jsou už vyvinuté v izolaci, jsou všechny jde nasadit do stejné cílové platformy.

![N-vrstev architektury](./media/n-layer-architecture.png)

Má několik výhod pro N-vrstvu přístupu, včetně:

* Refaktoring je izolovaná na vrstvu.
* Týmy mohou nezávisle na sobě vytvořit, otestovat, nasadit a udržovat samostatné vrstvy.
* Vrstvy můžete být automaticky, například datová vrstva může přistupovat k více databází bez nutnosti provádět změny vrstvě uživatelského rozhraní.

Bez serveru slouží k implementaci jednu nebo více vrstev.

## <a name="microservices"></a>Mikroslužby

**[Mikroslužby](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)**  architektury obsahovat běžné vlastnosti, které zahrnují:

* Aplikace se skládají z několika malých služeb.
* Každá služba se spouští ve svém vlastním procesu.
* Služby jsou zarovnány kolem obchodní domény.
* Služby komunikují přes jednoduché rozhraní API, obvykle přenos pomocí protokolu HTTP.
* Služby je možné nasadit a upgraduje samostatně.
* Služby nejsou závislé na jednom datovém úložišti.
* Systém je navržená s chybou v úvahu a aplikace může běžet i v případě selhání některých služeb.

Mikroslužby nemusí být vzájemně se vylučující k jiné přístupy k architektuře. Například může použít N-vrstvou architekturu mikroslužeb pro střední vrstvy. Také je možné implementovat mikroslužby v celou řadu způsobů, z adresáře v hostitelích služby IIS do kontejnerů. Zkontrolujte charakteristiky mikroslužeb je zvláště ideální pro implementace bez serveru.

![Architektura Mikroslužeb](./media/microservices-architecture.png)

Profesionálové mikroslužeb patří:

* Refaktoring často je izolovaná na jednu službu.
* Služby je možné upgradovat nezávisle na sobě.
* Odolnost proti chybám a elasticitu můžete ladit pro požadavky jednotlivých služeb.
* Vývoj, může dojít paralelně napříč různými týmy a platformami.
* Je snazší psát komplexní testy pro izolované služby.

Mikroslužby jsou součástí vlastní výzvy, včetně:

* Určení, jaké služby jsou k dispozici a jak je volat.
* Správa životního cyklu služeb.
* Ke zjištění, jak služby navzájem propojené, v celkové aplikace.
* Úplnou testování volání napříč různými službami.

Nakonec jsou všechny tyto výzvy, včetně proniknutí do výhod prostředí bez serveru, které jsou uvedeny dále vícebodových řešení.

>[!div class="step-by-step"]
[Předchozí](index.md)
[další](architecture-deployment-approaches.md)
