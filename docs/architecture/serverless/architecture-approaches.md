---
title: Přístupy k architektuře – aplikace bez serveru
description: Úvod k přístupům architektury pro vytváření cloudových podnikových aplikací, od n-vrstvých architektur až po bezserverové.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522894"
---
# <a name="architecture-approaches"></a>Přístupy k architektuře

Principy stávajících přístupů k navrhování podnikových aplikací pomáhají objasnit roli, kterou hrají serverové služby. Existuje mnoho přístupů a vzorů, které se vyvíjely v průběhu desetiletí vývoje softwaru, a všechny mají své vlastní klady a zápory. V mnoha případech nemusí konečné řešení zahrnovat rozhodování o jednotném přístupu, ale může integrovat několik přístupů. Scénáře migrace často zahrnují přechod z jednoho přístupu architektury na jiný prostřednictvím hybridního přístupu.

Tato kapitola obsahuje přehled logických i fyzických vzorů architektury pro podnikové aplikace.

## <a name="architecture-patterns"></a>Vzory architektury

Moderní obchodní aplikace se řídí různými vzory architektury. Tato část představuje přehled běžných vzorů. Vzory zde uvedené nejsou nutně všechny osvědčené postupy, ale ilustrují různé přístupy.

Další informace najdete v [tématu Architektura aplikací Azure průvodce](https://docs.microsoft.com/azure/architecture/guide/).

## <a name="monoliths"></a>Monolity

Mnoho obchodních aplikací se řídí vzorem monolitu. Starší aplikace jsou často implementovány jako monolity. Ve vzoru monolitu jsou všechny obavy aplikace obsaženy v jednom nasazení. Vše od uživatelského rozhraní až po volání databáze je součástí stejného základu kódu.

![Monolitová architektura](./media/monolith-architecture.png)

Přístup monolitu má několik výhod. Často je snadné stáhnout jeden základ kódu a začít pracovat. Doba rozjetí může být kratší a vytváření testovacích prostředí je stejně jednoduché jako poskytnutí nové kopie. Monolit může být navržen tak, aby zahrnoval více součástí a aplikací.

Bohužel, monolit vzor má tendenci se rozkládat ve velkém měřítku. Mezi hlavní nevýhody monolitového přístupu patří:

- Obtížné pracovat paralelně ve stejném základu kódu.
- Každá změna, bez ohledu na to, jak triviální, vyžaduje nasazení nové verze celé aplikace.
- Refaktoring potenciálně ovlivňuje celou aplikaci.
- Často jediným řešením škálování je vytvořit více kopií monolitu náročné na prostředky.
- Jak se systémy rozšiřují nebo získávají jiné systémy, integrace může být obtížná.
- Může být obtížné testovat z důvodu nutnosti konfigurovat celý monolit.
- Opakované použití kódu je náročné a často jiné aplikace skončí s vlastní kopie kódu.

Mnoho firem se na cloud dívá jako na příležitost k migraci monolitových aplikací a zároveň je refaktorovat na použitelnější vzory. Je běžné prolomit jednotlivé aplikace a součásti, aby mohly být udržovány, nasazovány a škálovány samostatně.

## <a name="n-layer-applications"></a>N-vrstvé aplikace

Aplikační logika oddílu n vrstvy do konkrétních vrstev. Mezi nejběžnější vrstvy patří:

- Uživatelské rozhraní
- Obchodní logika
- Přístup k datům

Ostatní vrstvy mohou zahrnovat middleware, dávkové zpracování a rozhraní API. Je důležité si uvědomit, že vrstvy jsou logické. I když jsou vyvinuty izolovaně, mohou být všechny nasazeny na stejnou cílovou platformu.

![Architektura N-Layer](./media/n-layer-architecture.png)

Přístup N-Layer má několik výhod, včetně:

- Refaktoring je izolován do vrstvy.
- Týmy mohou nezávisle vytvářet, testovat, nasazovat a udržovat samostatné vrstvy.
- Vrstvy lze vyměnit, například datová vrstva může přistupovat k více databázím bez nutnosti změn vrstvy uj.

Bez serveru lze použít k implementaci jedné nebo více vrstev.

## <a name="microservices"></a>Mikroslužby

**[Architektury mikroslužeb](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** obsahují společné charakteristiky, které zahrnují:

- Aplikace se skládají z několika malých služeb.
- Každá služba běží ve svém vlastním procesu.
- Služby jsou zarovnány kolem obchodních domén.
- Služby komunikovat přes zjednodušené api, obvykle pomocí protokolu HTTP jako přenos.
- Služby lze nasadit a upgradovat nezávisle.
- Služby nejsou závislé na jednom úložišti dat.
- Systém je navržen s ohledem na selhání a aplikace může stále běžet i v případě, že některé služby selžou.

Mikroslužeb nemusí vzájemně vylučovat jiné architektury přístupy. Například n-vrstvé architektury můžete použít mikroslužeb pro střední vrstvy. Je také možné implementovat mikroslužeb různými způsoby, od virtuálních adresářů na hostitelích služby IIS až po kontejnery. Vlastnosti mikroslužeb, aby byly obzvláště ideální pro implementace bez serveru.

![Architektura mikroslužeb](./media/microservices-architecture.png)

Mezi profesionály architektury mikroslužeb patří:

- Refaktoring je často izolován do jedné služby.
- Služby lze upgradovat nezávisle na sobě.
- Odolnost a pružnost lze vyladit podle požadavků jednotlivých služeb.
- Vývoj může probíhat souběžně napříč různorodými týmy a platformami.
- Je jednodušší psát komplexní testy pro izolované služby.

Mikroslužby přicházejí s vlastními výzvami, včetně:

- Určení, jaké služby jsou k dispozici a jak je nazývat.
- Správa životního cyklu služeb.
- Pochopení toho, jak služby zapadají do celkové aplikace.
- Úplné testování systému volání uskutečněných napříč různorodými službami.

Nakonec existují řešení pro řešení všech těchto problémů, včetně využití výhod bez serveru, které jsou popsány později.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](architecture-deployment-approaches.md)
