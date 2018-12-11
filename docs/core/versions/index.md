---
title: Jak se systémovou správou verzí modulu Runtime .NET Core a sady SDK
description: V tomto článku se naučíte, jak .NET Core SDK a modulu Runtime se systémovou správou verzí (podobně jako sémantické správy verzí).
author: bleroy
ms.date: 07/26/2018
ms.custom: seodec18
ms.openlocfilehash: 54b09a6b74b2cf213cea781dec95a413ac2ad059
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170714"
---
# <a name="overview-of-how-net-core-is-versioned"></a>Přehled, jak se systémovou správou verzí .NET Core

.NET core odkazuje na modul Runtime .NET Core a .NET Core SDK, který obsahuje nástroje, které potřebujete k vývoji aplikací. .NET core SDK jsou navrženy pro práci s jakékoli předchozí verzi modulu Runtime .NET Core. Tento článek vysvětluje strategii verze sady SDK a modulu runtime. Vysvětlení čísla verzí pro .NET Standard najdete v článku Představujeme [.NET Standard](../../standard/net-standard.md#net-implementation-support).

Modulu Runtime .NET Core a .NET Core SDK přidávání nových funkcí v různých sazbě – obecně .NET Core SDK poskytuje rychlé aktualizaci nástrojů pro více než .NET Core Runtime změny modulu runtime, které se používají v produkčním prostředí. Bohužel tento problém přinesl několik strategií správy verzí během posledních několika let. Informace o historii v následujícím článku na [správy verzí .NET Core](version-history.md).

## <a name="versioning-details"></a>Správa verzí podrobnosti

".NET Core 2.1" odkazuje na číslo verze modulu Runtime .NET Core. Modul Runtime .NET Core má hlavní, vedlejší/opravování přístup pro správu verzí, který následuje [sémantické správy verzí](#semantic-versioning).

.NET Core SDK není postupujte z sémantické správy verzí. .NET Core SDK verze rychleji a jeho verze musí komunikovat zarovnané runtime i v sadě SDK vlastní podverze a oprava vydané verze. Prvních dvou pozic verzi sady SDK .NET Core jsou pevně nastavené na .NET Core Runtime vydané s. Všechny verze sady SDK můžete vytvářet aplikace pro tento modul runtime nebo jakékoli nižší verzi.

Třetí pozici číslo verze sady SDK komunikuje i menší a opravu. Dílčí verze je vynásobené číslem 100. Dílčí verze 1, verze 2 opravy by být vyjádřena jako 102. Poslední dvě číslice představovat číslo opravy. Verze rozhraní .NET Core 2.2 může například vytvořit verze jako v následující tabulce:

| Změna                | .NET core Runtime | .NET core SDK (*) |
|-----------------------|-------------------|-------------------|
| Původní vydaná verze       | 2.2.0             | 2.2.100           |
| Oprava sady SDK             | 2.2.0             | 2.2.101           |
| Oprava sady SDK a modulu runtime | 2.2.1             | 2.2.102           |
| Změna funkce sady SDK    | 2.2.1             | 2.2.200           |

(\*) Tento graf používá budoucí 2.2 .NET Core Runtime jako v příkladu vzhledem k tomu, že historické artefaktů určená první sada SDK pro .NET Core 2.1 je 2.1.300. Další informace najdete v tématu [historie správy verzí .NET Core](version-history.md).

POZNÁMKY:

* Pokud sada SDK má 10 aktualizace funkcí před aktualizace funkcí modulu runtime, čísla verzí vrátit do řad 1000 pomocí čísla jako 2.2.1000 jako vydání funkcí po 2.2.900. Tato situace neočekává.
* 99 opravy verzí bez nedojde, vydání funkce. Pokud se blíží k uvolnění tohoto čísla, vynutí vydání funkce.

Zobrazí se další podrobnosti najdete v počáteční návrh na [dotnet/návrhy](https://github.com/dotnet/designs/pull/29) úložiště.

## <a name="semantic-versioning"></a>Sémantické správy verzí

.NET Core *Runtime* zhruba dodržuje [Semantic Versioning (SemVer)](https://semver.org/), přijetí použití `MAJOR.MINOR.PATCH` správy verzí, popsat stupeň a typ pomocí různých částí čísla verze Změňte.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Volitelný `PRERELEASE` a `BUILDNUMBER` části nikdy jsou součástí podporované verze a existovat pouze na denně automatizovaných buildů, místní sestavení z cíle zdroje a uvolní nepodporované ve verzi preview.

### <a name="understand-runtime-version-number-changes"></a>Pochopit, změní se číslo verze modulu runtime

`MAJOR` se zvýší, když:

* K produktu nebo novým směrem produktu dojde k významné změny.
* Zásadní změny byly provedeny. Existuje vysoká panelu k přijetí nejnovějších změn.
* Starší verze se už nepodporuje.
* Novější `MAJOR` přijaté verze existujícího závislosti.

`MINOR` se zvýší, když:

* Přidání veřejné svrchní oblasti rozhraní API.
* Přidání nové chování.
* Novější `MINOR` přijaté verze existujícího závislosti.
* Nové závislosti se používá.

`PATCH` se zvýší, když:

* Opravy chyb jsou provedeny.
* Je přidaná podpora pro projekty novější platformy.
* Novější `PATCH` přijaté verze existujícího závislosti.
* Jiné změny nevejde jedním z předchozích případů.

Pokud existuje více změn, nejvyšší prvek ovlivněny změnami v jednotlivých se zvýší, a následující dotazy nastaveny na nulu. Například když `MAJOR` se zvýší, `MINOR` a `PATCH` nastaveny na nulu. Když `MINOR` se zvýší, `PATCH` resetuje na nula při `MAJOR` nedotčené.

## <a name="version-numbers-in-file-names"></a>Čísla verzí v názvech souborů

Soubory stáhnout pro .NET Core carry verze, například `dotnet-sdk-2.1.300-win10-x64.exe`.

### <a name="preview-versions"></a>Verze Preview

Verze Preview `-preview[number]-([build]|"final")` připojenou k verzi. Například, `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Údržba verze

Po vydání nedostane mimo větví vydaných verzí obecně stop vytváření denně sestavení a místo zahájení výroby servisní sestavení. Servisní verze mají `-servicing-[number]` připojenou k verzi. Například, `2.0.1-servicing-006924`.

## <a name="relationship-to-net-standard-versions"></a>Relace pro verze .NET Standard

.NET standard se skládá z referenční sestavení .NET. Jsou specifické pro každou platformu víc implementací. Referenční sestavení obsahuje definici rozhraní API .NET, které jsou součástí daného verze .NET Standard. Každá implementace splňuje požadavky na konkrétní platformě .NET Standard kontrakt. Vám může Další informace o .NET Standard v následujícím článku na [.NET Standard](../../standard/net-standard.md) v příručce .NET.

.NET Standard používá odkaz na sestavení `MAJOR.MINOR` schéma vytváření verzí. `PATCH` úroveň není užitečná pro .NET Standard, protože poskytuje pouze rozhraní API specifikaci (bez implementace) a podle definice by všechny změny rozhraní API představují změny v sadě funkcí a proto nové `MINOR` verze.

Může být aktualizován implementace na jednotlivých platformách, obvykle jako součást verze platformy a proto není zřejmé programátorům pomocí .NET Standard na této platformě.

Implementuje každou verzi .NET Core na verzi .NET Standard. Implementace verze .NET Standard zahrnuje podporu pro předchozí verze .NET Standard. Verze .NET standard a .NET Core nezávisle na sobě. Se nezdá, že implementuje rozhraní .NET Core 2.0 rozhraní .NET Standard 2.0. .NET core 2.1 také implementuje rozhraní .NET Standard 2.0. Budoucí verze .NET Standard, jakmile budou k dispozici bude podporovat .NET core.

| .NET Core | .NET Standard |
|-----------|---------------|
| 1.0       | na verzi 1.6     |
| 2.0       | až 2,0     |
| 2.1       | až 2,0     |

## <a name="see-also"></a>Viz také:

* [Cílové verze rozhraní .NET Framework](../../standard/frameworks.md)  
* [Vytváření distribučních balíčků .NET Core](../build/distribution-packaging.md)  
* [.NET core podpory životního cyklu fakt list](https://www.microsoft.com/net/core/support)  
* [Vázání verze rozhraní .NET core 2 +](https://github.com/dotnet/designs/issues/3)  
* [Image dockeru pro .NET Core](https://hub.docker.com/r/microsoft/dotnet/)
