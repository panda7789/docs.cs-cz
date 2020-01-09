---
title: global.json – přehled
description: Naučte se používat soubor Global. JSON k nastavení verze .NET Core SDK při spouštění příkazů .NET Core CLI.
ms.date: 12/03/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 4da703266e98b209cdd031f4ea856b4d7c83930c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714175"
---
# <a name="globaljson-overview"></a>global.json – přehled

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

Soubor *Global. JSON* umožňuje definovat, která verze .NET Core SDK se používá při spuštění příkazů .NET Core CLI. Výběr .NET Core SDK je nezávislý na určení modulu runtime, který cílí na projekt. Verze .NET Core SDK označuje, které verze .NET Core CLIch nástrojů se používají. Obecně platí, že chcete použít nejnovější verzi nástrojů, takže není potřeba žádný soubor *Global. JSON* .

Další informace o určení modulu runtime místo toho naleznete v tématu [cílová rozhraní](../../standard/frameworks.md).

.NET Core SDK vyhledá soubor *Global. JSON* v aktuálním pracovním adresáři (to není nutně stejný jako adresář projektu) nebo v jednom z jeho nadřazených adresářů.

## <a name="globaljson-schema"></a>Global. JSON – schéma

### <a name="sdk"></a>sdk

Typ: Object

Určuje informace o .NET Core SDK k výběru.

#### <a name="version"></a>Verze nástroje

Typ: Řetězec

Verze .NET Core SDK, která se má použít

Všimněte si, že toto pole:

- Nemá podporu pro expanzi, to znamená, že je nutné zadat úplné číslo verze.
- Nepodporuje rozsahy verzí.

Následující příklad ukazuje obsah souboru *Global. JSON* :

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>Global. JSON a .NET Core CLI

Je užitečné znát, které verze jsou k dispozici, aby je bylo možné nastavit v *globálním souboru. JSON* . Úplný seznam podporovaných dostupných sad SDK najdete na stránce [stáhnout jádro .NET Core](https://dotnet.microsoft.com/download/dotnet-core) . Počínaje sadou .NET Core 2,1 SDK můžete spuštěním následujícího příkazu ověřit, které verze sady SDK jsou na vašem počítači již nainstalovány:

```dotnetcli
dotnet --list-sdks
```

Pokud chcete na svém počítači nainstalovat další .NET Core SDK verze, navštivte stránku [Stáhnout .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .

Nový soubor *Global. JSON* můžete v aktuálním adresáři vytvořit spuštěním příkazu [dotnet New](dotnet-new.md) , podobně jako v následujícím příkladu:

```dotnetcli
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a>Pravidla pro porovnání

> [!NOTE]
> Pravidla pro porovnání se řídí apphost, který je součástí modulu runtime .NET Core.
> K dispozici je nejnovější verze hostitele, pokud máte více nainstalovaných modulů runtime vedle sebe.

Počínaje rozhraním .NET Core 2,0 se při určování používané verze sady SDK použijí následující pravidla:

- Pokud nebyl nalezen soubor *Global. JSON* nebo soubor *Global. JSON* neurčuje verzi sady SDK, bude použita nejnovější nainstalovaná verze sady SDK. Nejnovější verze sady SDK může být buď vydání verze, nebo předběžná verze – nejvyšší číslo verze služby WINS.
- Pokud *Global. JSON* určí verzi sady SDK:
  - Pokud je v počítači nalezena zadaná verze sady SDK, je použita tato přesná verze.
  - Pokud se zadaná verze sady SDK v tomto počítači nenajde, použije se nejnovější nainstalovaná **verze opravy** SDK této verze. Nejnovější nainstalovaná **verze opravy** sady SDK může být buď vydání verze, nebo předběžná verze – nejvyšší číslo verze služby WINS. V .NET Core 2,1 a novějších **verzích opravy** nižší, než je zadaná **verze opravy** , se v výběru sady SDK ignorují.
  - Pokud není nalezena zadaná verze sady SDK a příslušná **verze opravy** sady SDK, je vyvolána chyba.

Verze sady SDK se v současné době skládá z následujících částí:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

**Verze .NET Core SDK funkce** je vyjádřena první číslicí (`x`) v poslední části čísla (`xyz`) pro sady SDK verze 2.1.100 a vyšší. Obecně platí, že .NET Core SDK má rychlejší cyklus vydávání verzí než .NET Core.

**Verze opravy** je definována posledními dvěma číslicemi (`yz`) v poslední části čísla (`xyz`) pro sady SDK verze 2.1.100 a vyšší. Například pokud zadáte `2.1.300` jako verzi sady SDK, výběr sady SDK vyhledá až `2.1.399`, ale `2.1.400` není považována za verzi opravy `2.1.300`.

.NET Core SDK verze `2.1.100` prostřednictvím `2.1.201` byly vydány během přechodu mezi schématy čísel verzí a nesprávně nezpracovávají `xyz` notace. Důrazně doporučujeme, pokud zadáte tyto verze v souboru *Global. JSON* , abyste zajistili, že zadané verze jsou na cílových počítačích.

Pokud jste v .NET Core SDK 1. x zadali verzi a nebyla nalezena žádná přesná shoda, použila se nejnovější nainstalovaná verze sady SDK. Nejnovější verze sady SDK může být buď vydání verze, nebo předběžná verze – nejvyšší číslo verze služby WINS.

## <a name="troubleshooting-build-warnings"></a>Řešení potíží s upozorněními sestavení

> [!WARNING]
> Pracujete s verzí Preview .NET Core SDK. Verzi sady SDK můžete definovat prostřednictvím globálního souboru. JSON v aktuálním projektu. Další na <https://go.microsoft.com/fwlink/?linkid=869452>

Toto upozornění znamená, že projekt je kompilován pomocí verze Preview .NET Core SDK, jak je vysvětleno v části pravidla pro [porovnání](#matching-rules) . Verze .NET Core SDK mají historii a závazek vysoké kvality. Pokud ale nechcete používat verzi Preview, přidejte soubor *Global. JSON* do struktury hierarchie projektu, abyste určili, kterou verzi SDK chcete použít, a pomocí `dotnet --list-sdks` ověřit, jestli je verze v počítači nainstalovaná. Při vydání nové verze, pokud chcete použít novou verzi, odeberte soubor *Global. JSON* nebo ho aktualizujte tak, aby používal novější verzi.

> [!WARNING]
> Spouštěcí projekt {startupProject} cílí na rozhraní Framework. NETCoreApp verze {targetFrameworkVersion}. Tato verze nástrojů příkazového řádku Entity Framework Core .NET podporuje pouze verzi 2,0 nebo vyšší. Informace o použití starších verzí nástrojů najdete v tématu <https://go.microsoft.com/fwlink/?linkid=871254>

Počínaje sadou .NET Core 2,1 SDK (verze 2.1.300) se v sadě SDK nachází příkaz `dotnet ef`. Toto upozornění znamená, že projekt cílí na EF Core 1,0 nebo 1,1, což není kompatibilní s .NET Core 2,1 SDK a novějšími verzemi. Chcete-li zkompilovat projekt, nainstalujte sadu .NET Core 2,0 SDK (verze 2.1.201) a dřívější na váš počítač a definujte požadovanou verzi sady SDK pomocí souboru *Global. JSON* . Další informace o příkazu `dotnet ef` najdete v tématu [EF Core nástroje příkazového řádku .NET](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Viz také:

- [Jak se řeší sady SDK projektu](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
