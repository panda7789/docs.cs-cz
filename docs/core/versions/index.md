---
title: Jak jsou verze prostředí .NET Core Runtime a sady SDK
description: Tento článek vás seznámí s tím, jak jsou .NET Core SDK a modul runtime ve verzi (podobně jako sémantická Správa verzí).
ms.date: 07/26/2018
ms.openlocfilehash: c85a2112b439768068663688947960ac814de824
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777320"
---
# <a name="overview-of-how-net-core-is-versioned"></a>Přehled toho, jak je verze .NET Core

.NET Core odkazuje na modul runtime .NET Core a .NET Core SDK, který obsahuje nástroje, které potřebujete pro vývoj aplikací. Sady .NET Core SDK jsou navržené tak, aby fungovaly s jakoukoli předchozí verzí modulu runtime .NET Core. Tento článek popisuje strategii modulu runtime a verze sady SDK. Vysvětlení čísel verzí pro .NET Standard najdete v článku Úvod do [.NET Standard](../../standard/net-standard.md#net-implementation-support).

Modul runtime .NET Core a .NET Core SDK přidávají nové funkce v jiné míře – obecně .NET Core SDK poskytuje aktualizované nástroje rychleji než modul runtime .NET Core mění modul runtime, který používáte v produkčním prostředí.

## <a name="versioning-details"></a>Podrobnosti správy verzí

.NET Core 2,1 odkazuje na číslo verze modulu runtime .NET Core. Modul runtime .NET Core má přístup k hlavnímu/dílčímu/opravnému způsobu správy verzí, který následuje po [sémantické verzi](#semantic-versioning).

.NET Core SDK nedodržuje sémantickou správu verzí. .NET Core SDK vydává rychlejší a jejich verze musí komunikovat se zarovnaným modulem runtime i s vlastními podverzemi sady SDK a verzemi oprav. První dvě pozice .NET Core SDK verze jsou uzamčeny modulem runtime .NET Core vydaným pomocí. Každá verze sady SDK může vytvářet aplikace pro tento modul runtime nebo jakoukoli nižší verzi.

Třetí pozice čísla verze sady SDK komunikuje s podverzem a číslem opravy. Vedlejší verze je vynásobena 100. Dílčí verze 1, verze patch 2 by byla reprezentovaná jako 102. Poslední dvě číslice reprezentují číslo opravy. Například vydání .NET Core 2,2 může vytvořit vydání jako v následující tabulce:

| Změna                | .NET Core Runtime | .NET Core SDK (\*) |
|-----------------------|-------------------|-------------------|
| Původní vydaná verze       | 2.2.0             | 2.2.100           |
| Oprava sady SDK             | 2.2.0             | 2.2.101           |
| Modul runtime a oprava sady SDK | 2.2.1             | 2.2.102           |
| Změna funkce sady SDK    | 2.2.1             | 2.2.200           |

(\*) Tento graf jako příklad používá modul runtime 2,2 .NET Core, protože historický artefakt znamenal první sadu SDK pro .NET Core 2,1 je 2.1.300. Další informace najdete v části [Výběr verze .NET Core](selection.md).

Poznámka

- Pokud sada SDK obsahuje 10 aktualizací funkcí před aktualizací běhové funkce, čísla verzí se převádějí do řady 1000 s čísly, jako je například 2.2.1000, jako je verze funkce následující po 2.2.900. Tato situace se neočekává.
- neprojeví se verze opravy 99 bez vydání funkce. Pokud k tomuto číslu přistupuje verze, vynutí vydání funkce.

Další podrobnosti můžete zobrazit v prvním návrhu v úložišti [dotnet/Designs](https://github.com/dotnet/designs/pull/29) .

## <a name="semantic-versioning"></a>Sémantická verze

*Modul runtime* .NET Core zhruba dodržuje [sémantickou správu verzí (SemVer)](https://semver.org/)a přijímá použití `MAJOR.MINOR.PATCH` verzí, a to pomocí různých částí čísla verze, které popisují stupeň a typ změny.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Volitelné `PRERELEASE` a `BUILDNUMBER` části nejsou nikdy součástí podporovaných vydání a existují pouze v noci buildech, místních sestaveních ze zdrojových cílů a nepodporovaných verzích Preview.

### <a name="understand-runtime-version-number-changes"></a>Principy změn v číslech verzí modulu runtime

`MAJOR` se zvýší, když:

- Dojde k významným změnám produktu nebo novému směru produktu.
- Byly provedeny zásadní změny. K přijetí nejnovějších změn je k dispozici vysoký pás.
- Stará verze už není podporovaná.
- Je přijata novější `MAJOR` verze stávající závislosti.

`MINOR` se zvýší, když:

- Přidala se plocha veřejné rozhraní API.
- Bylo přidáno nové chování.
- Je přijata novější `MINOR` verze stávající závislosti.
- Zavádí se nová závislost.

`PATCH` se zvýší, když:

- Byly provedeny opravy chyb.
- Přidala se podpora pro novější platformu.
- Je přijata novější `PATCH` verze stávající závislosti.
- Jakékoli jiné změny nespadají do jednoho z předchozích případů.

V případě více změn se zvýší nejvyšší prvek ovlivněný jednotlivými změnami a následující hodnoty jsou vynulovány na nulu. Například při zvýšení `MAJOR` `MINOR` a `PATCH` se resetují na nula. Když se `MINOR` zvýší, `PATCH` se resetuje na nulu, zatímco `MAJOR` zůstane beze změny.

## <a name="version-numbers-in-file-names"></a>Čísla verzí v názvech souborů

Soubory stažené pro .NET Core obsahují verzi, například `dotnet-sdk-2.1.300-win10-x64.exe`.

### <a name="preview-versions"></a>Verze Preview

Verze Preview mají `-preview[number]-([build]|"final")` připojit k verzi. Například `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Verze údržby

Po vyzkoušení vydání vydaných verzí větve vydaných verzí většinou ukončí vytváření každodenních sestavení a místo toho začnou vytvářet servisní sestavení. Verze obsluhy mají `-servicing-[number]` připojeny k verzi. Například `2.0.1-servicing-006924`.

## <a name="relationship-to-net-standard-versions"></a>Vztah k .NET Standard verzí

.NET Standard se skládá z referenčního sestavení .NET. K dispozici je více implementací specifických pro jednotlivé platformy. Referenční sestavení obsahuje definici rozhraní API .NET, která jsou součástí dané .NET Standard verze. Každá implementace splňuje .NET Standard kontraktu na konkrétní platformě. Další informace o .NET Standard najdete v článku o [.NET Standard](../../standard/net-standard.md) v příručce .NET.

.NET Standard referenční sestavení používá schéma `MAJOR.MINOR`ch verzí. úroveň `PATCH` není užitečná pro .NET Standard, protože zpřístupňuje jenom specifikaci rozhraní API (žádná implementace) a podle definice jakákoliv změna rozhraní API by představovala změnu v sadě funkcí, a proto novou verzi `MINOR`.

Implementace na jednotlivých platformách se můžou aktualizovat, obvykle jako součást verze platformy, a nemusejí být zřejmé pro programátory, kteří používají .NET Standard na této platformě.

Každá verze rozhraní .NET Core implementuje verzi .NET Standard. Implementace verze .NET Standard implikuje podporu pro předchozí verze .NET Standard. Verze .NET Standard a .NET Core nezávisle. Je to koshoda, kterou .NET Core 2,0 implementuje .NET Standard 2,0. Rozhraní .NET Core 2,1 také implementuje .NET Standard 2,0. .NET Core bude podporovat budoucí verze .NET Standard, jakmile budou k dispozici.

| .NET Core | .NET Standard |
|-----------|---------------|
| 1.0       | až 1,6     |
| 2.0       | až 2,0     |
| 2.1       | až 2,0     |
| 2.2       | až 2,0     |
| 3,0       | až 2,1     |

## <a name="see-also"></a>Viz také:

- [Cílové architektury](../../standard/frameworks.md)
- [Vytváření distribučních balíčků .NET Core](../build/distribution-packaging.md)
- [Tabulka faktů pro životní cyklus podpory .NET Core](https://dotnet.microsoft.com/platform/support/policy)
- [Vazba .NET Core 2 + verze](https://github.com/dotnet/designs/issues/3)
- [Image Docker pro .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/)
