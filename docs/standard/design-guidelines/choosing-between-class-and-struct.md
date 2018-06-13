---
title: Volba mezi třídy a struktury
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bb05b825113c025781a790dc206d500633a3b08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573578"
---
# <a name="choosing-between-class-and-struct"></a>Volba mezi třídy a struktury
Jeden základní rozhodnutí o návrhu, které každý framework Návrhář otočená je ohledně návrhu typu třídy (typu odkazu.) nebo jako struktury (typ hodnoty). Dobrou znalost jazyka rozdíly v chování odkazové typy a typy hodnot je velmi důležité při vytvoření tato volba.  
  
 První nesouhlasí odkazové typy a typy hodnot, které jsme zvažovat je, že odkazové typy jsou přidělené v haldě a uklizeny, zatímco typy hodnot, které jsou přiděleny buď v zásobníku nebo vložené v obsahující typy a kdy navrácena zásobníku unwinds nebo při jejich obsahující typ získá navrácena. Přidělování a navrácení typů hodnot, proto jsou v obecné levnějších než přidělování a navrácení odkazové typy.  
  
 V dalším kroku pole odkaz, který typy jsou přidělené se na řádku, což znamená pole, které jsou elementy jenom odkazy k instancím typu odkazu, který je umístěný v haldě. Hodnota typu pole jsou přiděleny vložené, což znamená, že elementy pole jsou instance skutečný typ hodnoty. Přidělování a navrácení hodnota typu pole jsou proto výrazně levnější než přidělování a navrácení odkaz na typ pole. Kromě toho ve většině případů hodnota typu pole vykazovat mnohem lepší polohu odkazu.  
  
 Další rozdíl se týká využití paměti. Typy hodnot získat do pole, když přetypovat na typ odkazu nebo jednomu z rozhraní, která implementují. Získají nezabalený při převést zpět na typ hodnoty. Protože polí jsou objekty, které mají při přidělování v haldě a uvolňování paměti, příliš mnoho zabalení a rozbalení může mít negativní dopad na haldě, bude systém uvolňování a nakonec i výkon aplikace.  Naproti tomu žádný takový zabalení nastane jako odkazové typy jsou přetypování.  
  
 Odkaz na typ přiřazení zkopírujte odkaz, zatímco hodnota typu přiřazení zkopírujte celou hodnotu. Přiřazení velké referenční typy jsou proto levnějších než přiřazení typů velkých hodnot.  
  
 Nakonec odkazové typy jsou předávány odkazem, zatímco typů hodnot se předávají podle hodnoty. Změny instance typu odkaz ovlivní všechny odkazy na instanci. Instance typu hodnota se zkopírují, pokud je předaná hodnota. Při změně instanci typu hodnoty samozřejmě neovlivňuje žádné jeho kopie. Protože kopie nejsou explicitně vytvořený uživatelem, ale implicitně vytvářejí, když se předávají argumentů nebo návratové hodnoty jsou vráceny, může být matoucí pro mnoho uživatelů typy hodnot, které mohou být změněny. Typy hodnot, proto by měl být neměnitelný.  
  
 Existuje pravidlo musí být většinu typů v rámci třídy. Existují však některé situace, ve kterých charakteristiky typ hodnoty Ujistěte se, je vhodnější použít struktury.  
  
 **✓ ZVAŽTE** definice struktury místo třídu, pokud instance typu jsou malé a běžně krátkodobou nebo jsou běžně součástí jiné objekty.  
  
 **X nepoužívejte** definice struktury, pokud má tento typ všechny následující vlastnosti:  
  
-   Logicky reprezentuje jednu hodnotu, podobně jako primitivní typy (`int`, `double`atd.).  
  
-   Ho má velikost instance v části 16 bajtů.  
  
-   Se nedá změnit.  
  
-   Nebude mít často zabaleny.  
  
 Ve všech ostatních případech byste měli definovat vaše typy jako třídy.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
