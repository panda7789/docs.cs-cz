---
title: Přístupy k architektuře – aplikace bez serveru
description: Úvod do architektury architektury pro vytváření cloudových podnikových aplikací, od N-vrstvých architektur až po bez serveru.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522894"
---
# <a name="architecture-approaches"></a>Přístupy k architektuře

Porozumění existujícím přístupům k architektům podnikových aplikací je vyjasnění role, kterou prohrála bez serveru. Existuje mnoho přístupů a vzorů, které se vyvinuly během desetiletí vývoje softwaru, a všechny mají své vlastní specialisty a nevýhody. V mnoha případech se může stát, že konečné řešení nezahrnuje rozhodování o jednom přístupu, ale může integrovat několik přístupů. Scénáře migrace často zahrnují přesun z jednoho přístupu architektury do druhého prostřednictvím hybridního přístupu.

V této části najdete přehled logických i fyzických struktur pro podnikové aplikace.

## <a name="architecture-patterns"></a>Vzory architektury

Moderní obchodní aplikace se řídí různými modely architektury. Tato část představuje průzkum běžných vzorů. Zde uvedené příklady nejsou nutně všechny osvědčené postupy, ale ilustrují různé přístupy.

Další informace najdete v tématu [Průvodce architekturou aplikací Azure](https://docs.microsoft.com/azure/architecture/guide/).

## <a name="monoliths"></a>Monolitů

Řada obchodních aplikací dodržuje vzor monolitu. Starší verze aplikací jsou často implementovány jako monolitů. Ve vzorci monolitu jsou všechny aspekty týkající se aplikace obsaženy v jednom nasazení. Vše od uživatelského rozhraní po volání databáze je zahrnuto ve stejném základu kódu.

![Architektura monolitu](./media/monolith-architecture.png)

Přístup k monolitu má několik výhod. Je často snadné stáhnout jeden základ kódu a začít pracovat. Doba provozu může být menší a vytváření testovacích prostředí je stejně snadné jako poskytování nové kopie. Monolitu může být navržený tak, aby zahrnoval více komponent a aplikací.

Monolitu vzor bohužel má tendenci rozlomit se škálováním. Mezi hlavní nevýhody přístupu monolitu patří:

- Obtížně fungovat paralelně ve stejném základu kódu.
- Jakékoli změny bez ohledu na to, jak triviální vyžaduje nasazení nové verze celé aplikace.
- Refaktoring může mít vliv na celou aplikaci.
- Jediným řešením pro horizontální navýšení kapacity je často vytvoření více kopií monolitu náročných na prostředky.
- V případě, že se systémy rozbalí nebo ostatní systémy získávají, může být integrace obtížné.
- Testování může být obtížné kvůli nutnosti nakonfigurovat celou monolitu.
- Opětovné použití kódu je náročné a často jiné aplikace mají vlastní kopie kódu.

Mnohé firmy vypadají v cloudu jako příležitost k migraci aplikací monolitu a ve stejnou dobu refaktorování na více použitelných vzorů. Je běžné rozdělit jednotlivé aplikace a komponenty, aby je bylo možné udržovat, nasadit a škálovat samostatně.

## <a name="n-layer-applications"></a>N-vrstvé aplikace

N-vrstvá aplikace oddíl aplikační logiky do specifických vrstev. Mezi nejběžnější vrstvy patří:

- Uživatelské rozhraní
- Obchodní logika
- Přístup k datům

Další vrstvy můžou zahrnovat middleware, dávkové zpracování a rozhraní API. Je důležité si uvědomit, že vrstvy jsou logické. I když se vyvíjí v izolaci, můžou se všechny nasadit na stejnou cílovou platformu.

![N-vrstvá architektura](./media/n-layer-architecture.png)

K dispozici je několik výhod pro N-vrstvý přístup, včetně:

- Refaktoring je izolovaný s vrstvou.
- Týmy můžou nezávisle sestavovat, testovat, nasazovat a udržovat samostatné vrstvy.
- Vrstvy lze odkládací, například datová vrstva může přistupovat k několika databázím, aniž by vyžadovaly změny ve vrstvě uživatelského rozhraní.

Bez serveru se dá použít k implementaci jedné nebo víc vrstev.

## <a name="microservices"></a>Mikroslužeb

Architektury **[mikroslužeb](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** obsahují běžné charakteristiky, které zahrnují:

- Aplikace se skládají z několika malých služeb.
- Každá služba se spouští ve vlastním procesu.
- Služby jsou zarovnány k obchodním doménám.
- Služby komunikují přes odlehčená rozhraní API, obvykle jako přenos pomocí protokolu HTTP.
- Služby je možné nasadit a upgradovat nezávisle.
- Služby nejsou závislé na jednom úložišti dat.
- Systém je navržený s ohledem na selhání a aplikace může běžet i v případě, že některé služby selžou.

Mikroslužby nemusí být vzájemně exkluzivní pro jiné přístupy k architektuře. N-vrstvá architektura může například používat mikroslužby pro střední vrstvu. Je také možné implementovat mikroslužby mnoha různými způsoby, od virtuálních adresářů hostitelů služby IIS až po kontejnery. Charakteristiky mikroslužeb je zvláště ideální pro implementace bez serveru.

![Architektura mikroslužeb](./media/microservices-architecture.png)

Mezi profesionály architektury mikroslužeb patří:

- Refaktoring se často izoluje u jediné služby.
- Služby je možné upgradovat nezávisle na sobě.
- Odolnost a pružnost je možné vyladit podle požadavků jednotlivých služeb.
- Vývoj může nastat paralelně napříč různými týmy a platformami.
- Napsání komplexních testů pro izolované služby je snazší.

Mikroslužby se dodávají s vlastními výzvami, včetně:

- Určete, jaké služby jsou k dispozici a jak je volat.
- Správa životního cyklu služeb.
- Seznamte se s tím, jak se služby vzájemně vejdou do celkové aplikace.
- Úplné systémové testování volání prováděných napříč různými službami.

Nakonec existují řešení, která řeší všechny tyto výzvy, včetně klepnutí na výhody bez serveru, které jsou popsány později.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](architecture-deployment-approaches.md)
