---
title: Jak jsou verzí rozhraní .NET Core Runtime a Sady SDK
description: Tento článek vás naučí, jak jsou verzí sady .NET Core SDK a Runtime (podobně jako sémantická správa verzí).
ms.date: 07/26/2018
ms.openlocfilehash: c85a2112b439768068663688947960ac814de824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75777320"
---
# <a name="overview-of-how-net-core-is-versioned"></a>Přehled verzí rozhraní .NET Core

.NET Core odkazuje na .NET Core Runtime a .NET Core SDK, který obsahuje nástroje potřebné k vývoji aplikací. Sady .NET Core SDK jsou navrženy tak, aby fungovaly s jakoukoli předchozí verzí rozhraní .NET Core Runtime. Tento článek vysvětluje runtime a strategie verze sady SDK. Vysvětlení čísel verzí pro rozhraní .NET Standard naleznete v článku o zavedení [standardu .NET](../../standard/net-standard.md#net-implementation-support).

Sada .NET Core Runtime a .NET Core SDK přidávají nové funkce jinou rychlostí – obecně sada .NET Core SDK poskytuje aktualizované nástroje rychleji, než prostředí .NET Core Runtime změní za běhu, který používáte v produkčním prostředí.

## <a name="versioning-details"></a>Podrobnosti správy verzí

".NET Core 2.1" odkazuje na číslo verze .NET Core Runtime. .NET Core Runtime má hlavní/minor/patch přístup k správu verzí, která následuje [sémantické správu verzí](#semantic-versioning).

Sada .NET Core SDK nesleduje sémantickou správu verzí. Sada .NET Core SDK vydává rychleji a její verze musí komunikovat zarovnané runtime a vlastní dílčí verze sady SDK a opravy. První dvě pozice verze .NET Core SDK jsou uzamčeny na rozhraní .NET Core Runtime, které bylo vydáno. Každá verze sady SDK můžete vytvořit aplikace pro tento runtime nebo nižší verzi.

Třetí pozice čísla verze sady SDK sděluje číslo vedlejší i oplatky. Dílčí verze se vynásobí 100. Dílčí verze 1, oprava verze 2 bude reprezentována jako 102. Poslední dvě číslice představují číslo opravy. Například vydání rozhraní .NET Core 2.2 může vytvořit verze, jako je následující tabulka:

| Změnit                | .NET Core Runtime | Sada SDK jádra .NET (\*) |
|-----------------------|-------------------|-------------------|
| Původní vydaná verze       | 2.2.0             | 2.2.100           |
| Oprava sady SDK             | 2.2.0             | 2.2.101           |
| Oprava runtime a sady SDK | 2.2.1             | 2.2.102           |
| Změna funkce sady SDK    | 2.2.1             | 2.2.200           |

(\*) Tento graf používá 2.2 .NET Core Runtime jako příklad, protože historický artefakt znamená první SDK pro .NET Core 2.1 je 2.1.300. Další informace naleznete ve [výběru verze .NET Core](selection.md).

Poznámky:

- Pokud sada SDK obsahuje 10 aktualizací funkcí před aktualizací funkce runtime, čísla verzí se přetočí do řady 1000 s čísly jako 2.2.1000 jako verze funkce po verzi 2.2.900. Tato situace se neočekává, že nastane.
- 99 vydání oprav bez vydání funkce nedojde. Pokud se vydání přiblíží k tomuto číslu, vynutí vydání prvku.

Další podrobnosti můžete vidět v původním návrhu v úložišti [dotnet/designs.](https://github.com/dotnet/designs/pull/29)

## <a name="semantic-versioning"></a>Sémantická správa verzí

.NET Core *Runtime* zhruba dodržuje [sémantické versioning (SemVer)](https://semver.org/) `MAJOR.MINOR.PATCH` , přijetí použití správy verzí, pomocí různých částí číslo verze k popisu stupně a typu změny.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Volitelné `PRERELEASE` a `BUILDNUMBER` části jsou nikdy součástí podporovaných verzí a existují pouze na noční sestavení, místní sestavení ze zdrojových cílů a nepodporované verze náhledu.

### <a name="understand-runtime-version-number-changes"></a>Principy změn čísel verzí za běhu

`MAJOR`se zintáží, když:

- Dojde k významným změnám produktu nebo nového směru produktu.
- Byly přijaty změny. Je tu vysoká laťka pro přijímání změn.
- Stará verze již není podporována.
- Je přijata novější `MAJOR` verze existující závislosti.

`MINOR`se zintáží, když:

- Veřejné rozhraní API je přidán.
- Je přidáno nové chování.
- Je přijata novější `MINOR` verze existující závislosti.
- Je zavedena nová závislost.

`PATCH`se zintáží, když:

- Opravy chyb jsou prováděny.
- Je přidána podpora novější platformy.
- Je přijata novější `PATCH` verze existující závislosti.
- Žádná jiná změna se nevejde do jednoho z předchozích případů.

Pokud existuje více změn, nejvyšší prvek ovlivněný jednotlivými změnami se zintácí a následující jsou nastaveny na nulu. Například při `MAJOR` zvýšení `MINOR` a `PATCH` jsou obnoveny na nulu. Při `MINOR` zvýšení je resetován na `PATCH` `MAJOR` nulu, zatímco zůstane nedotčena.

## <a name="version-numbers-in-file-names"></a>Čísla verzí v názvech souborů

Soubory stažené pro rozhraní .NET Core nesou `dotnet-sdk-2.1.300-win10-x64.exe`například verzi .

### <a name="preview-versions"></a>Náhled verzí

Verze preview mají `-preview[number]-([build]|"final")` připojený k verzi. Například, `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Servis verzí

Po vydání zhasne, větve verze obecně zastavit výrobu denní sestavení a místo toho začít vyrábět údržbu sestavení. Obsluhující verze mají `-servicing-[number]` připojenk verzi. Například, `2.0.1-servicing-006924`.

## <a name="relationship-to-net-standard-versions"></a>Vztah k verzím .NET Standard

Standard .NET se skládá z referenčního sestavení .NET. Existuje více implementací specifických pro každou platformu. Referenční sestavení obsahuje definici rozhraní API .NET, která jsou součástí dané verze .NET Standard. Každá implementace splňuje .NET Standard smlouvy na konkrétní platformě. Další informace o standardu .NET v článku [o standardu .NET v](../../standard/net-standard.md) průvodci .NET.

Referenční sestavení .NET Standard `MAJOR.MINOR` používá schéma správy verzí. `PATCH`úroveň není užitečná pro standard .NET, protože zveřejňuje pouze specifikaci rozhraní API (bez implementace) a podle definice by `MINOR` jakákoli změna rozhraní API představovala změnu v sadě funkcí a tedy novou verzi.

Implementace na každé platformě mohou být aktualizovány, obvykle jako součást verze platformy, a proto nejsou zřejmé programátorům používajícím na této platformě standard .NET Standard.

Každá verze rozhraní .NET Core implementuje verzi standardu .NET. Implementace verze standardu .NET Znamená podporu pro předchozí verze rozhraní .NET Standard. Verze .NET Standard a .NET Core nezávisle. Je to náhoda, že .NET Core 2.0 implementuje .NET Standard 2.0. .NET Core 2.1 také implementuje standard .NET 2.0. .NET Core bude podporovat budoucí verze standardu .NET, jakmile budou k dispozici.

| .NET Core | .NET Standard |
|-----------|---------------|
| 1.0       | až 1,6     |
| 2.0       | až 2,0     |
| 2.1       | až 2,0     |
| 2,2       | až 2,0     |
| 3.0       | až 2.1     |

## <a name="see-also"></a>Viz také

- [Cílové architektury](../../standard/frameworks.md)
- [Vytváření distribučních balíčků .NET Core](../build/distribution-packaging.md)
- [Přehled faktů o životním cyklu základní podpory .NET](https://dotnet.microsoft.com/platform/support/policy)
- [Vazba verze .NET Core 2+](https://github.com/dotnet/designs/issues/3)
- [Inaje Dockeru pro jádro .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/)
