---
title: Přehled Global.JSON
description: Zjistěte, jak použít soubor global.json se nastavit verzi .NET Core SDK, při spuštění příkazů rozhraní příkazového řádku .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 07/30/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 05ec296c4c8210c63c7c1b5ce63ef598ca6ac719
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838075"
---
# <a name="globaljson-overview"></a>Přehled Global.JSON

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

*Global.json* souboru můžete zadat, která verze rozhraní .NET Core SDK se používá při spuštění příkazů rozhraní příkazového řádku .NET Core. Výběr sady .NET Core SDK je nezávislý na určení modulu runtime váš projekt cílí. .NET Core SDK verze označuje, které verze nástroje .NET Core CLI používají. Obecně platí, kterou chcete použít nejnovější verzi nástrojů, proto není *global.json* soubor nepotřebujete.

Další informace o zadávání místo toho modul runtime, naleznete v tématu [platforem](../../standard/frameworks.md).

Sada .NET core SDK hledá *global.json* soubor v aktuálním pracovním adresáři (který není nutně stejné jako adresář projektu) nebo v některém z jeho nadřazené adresáře.

## <a name="globaljson-schema"></a>Global.JSON schématu

### <a name="sdk"></a>Sady SDK

Typ: objekt

Určuje informace o .NET Core SDK k výběru.

#### <a name="version"></a>verze

Typ: řetězec

Verze .NET Core SDK používat.

Všimněte si, že toto pole:

- Nebude mít podporu podpory zástupných znaků, to znamená, celé číslo verze musí být zadaný.
- Nepodporuje rozsahů verzí.

Následující příklad ukazuje obsah *global.json* souboru:

```json
{
  "sdk": {
    "version": "2.1.300"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>Global.JSON a .NET Core CLI

Je užitečné vědět, jaké verze jsou k dispozici, aby bylo možné nastavit jednu *global.json* souboru. Najdete úplný seznam podporovaných sad SDK k dispozici na [.NET stáhne](https://www.microsoft.com/net/download/all) lokality. Spouští se sadou .NET Core SDK 2.1, můžete spustit následující příkaz k ověření, které verze sady SDK jsou již nainstalovány na vašem počítači:

```console
dotnet --list-sdks
```

Pokud chcete nainstalovat další verze sady SDK .NET Core na počítači, přejděte [.NET stáhne](https://www.microsoft.com/net/download/all) lokality.

Můžete vytvořit nový *global.json* soubor v aktuálním adresáři pomocí provádí [dotnet nové](dotnet-new.md) příkazu, podobně jako v následujícím příkladu:

```console
dotnet new globaljson --sdk-version 2.1.300
```

## <a name="matching-rules"></a>Odpovídající pravidla

> [!NOTE]
> Pravidla pro porovnávání se řídí apphost, který je součástí modulu runtime .NET Core.
> Pokud máte více modulů runtime nainstalovaný – souběžně se používá nejnovější verzi hostitele.

Od verze rozhraní .NET Core 2.0, platí následující pravidla při určování, kterou verzi sady SDK používat:

- Pokud ne *global.json* nalezen soubor nebo *global.json* nemá určenou verzi sady SDK se používá nejnovější nainstalovaná verze sady SDK. Nejnovější verze sady SDK může být verze nebo předběžné verze-wins nejvyšší číslo verze.
- Pokud *global.json* specifikovat verzi sady SDK:
  - Pokud zadaná verze SDK je nalezen na počítači, použije se tento přesnou verzi.
  - Pokud zadaná verze SDK nebyl nalezen na počítači, nainstaluje nejnovější SDK **verzi opravy** , který je použita verze. Nainstalovat nejnovější verzi sady SDK **verzi opravy** může být verze nebo předběžné verze nejvyšší číslo wins. V rozhraní .NET Core 2.1 a vyšší **oprava verze** nižší než **verzi opravy** zadané jsou ignorovány ve výběru sady SDK.
  - Pokud zadaná verze sady SDK a vhodnou sadu SDK **verzi opravy** nebyl nalezen, je vržena chyba.

Verze sady SDK se aktuálně skládá z následujících částí:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

**Funkce uvolnění** sady .NET Core SDK je reprezentována první číslice (`x`) v poslední část čísla (`xyz`) pro sadu SDK verze 2.1.100 a vyšší. Obecně platí .NET Core SDK má rychlejší cyklu vydávání verzí, než .NET Core.

**Verzi opravy** je definován posledních dvou číslic (`yz`) v poslední část čísla (`xyz`) pro sadu SDK verze 2.1.100 a vyšší. Pokud zadáte například `2.1.300` jako verzi sady SDK, vyhledá SDK výběr až `2.1.399` ale `2.1.400` není považováno za verzi opravy pro `2.1.300`.

Sada .NET core SDK verze `2.1.100` prostřednictvím `2.1.201` vydané během přechodu mezi schémata číslo verze a nezpracovávají správně `xyz` zápis. Důrazně doporučujeme, pokud zadáte tyto verze v *global.json* souboru, který je zajistit, že jsou zadané verze na cílových počítačích.

S .NET Core SDK byl nalezen 1.x, pokud jste zadali, verzi a přesná shoda není, byl použit nejnovější nainstalovaná verze sady SDK. Nejnovější verze sady SDK může být verze nebo předběžné verze-wins nejvyšší číslo verze.

## <a name="troubleshooting-build-warnings"></a>Řešení potíží s upozorněními sestavení

> [!WARNING]
> Pracujete s předběžnou verzi .NET Core SDK. Verze sady SDK prostřednictvím souboru global.json můžete definovat v aktuálním projektu. Informace najdete na <https://go.microsoft.com/fwlink/?linkid=869452>

Toto upozornění signalizuje, že váš projekt se kompiluje ve verzi preview sady .NET Core SDK, jak je vysvětleno v [pravidel](#matching-rules) oddílu. Verze .NET core SDK mají historie a bez závazků toho, že vysoce kvalitní. Nicméně, pokud už nechcete používat verzi preview, přidejte *global.json* soubor struktuře hierarchie projektu zadat verzi sady SDK, která se má použít a použijte `dotnet --list-sdks` potvrďte, že na svém počítači je nainstalována verze. Po vydání nové verze, na použití nové verze, buď odeberte *global.json* souboru nebo ji chcete používat novější verzi.

> [!WARNING]
> Při spuštění projektu "{výchozí projekt}" cíleného na rozhraní framework '. NETCoreApp' verze {targetFrameworkVersion}. Tato verze nástroje příkazového řádku .NET Core Entity Framework podporuje pouze verze 2.0 nebo vyšší. Informace o používání starší verze nástrojů najdete v tématu <https://go.microsoft.com/fwlink/?linkid=871254>

Spouští se sadou .NET Core SDK 2.1 (vs. 2.1.300) `dotnet ef` příkaz je zahrnutý v sadě SDK. Toto upozornění signalizuje, že váš projekt cílí na EF Core 1.0 a 1.1, který není kompatibilní s .NET Core SDK 2.1 a novějších verzích. Chcete-li zkompilovat váš projekt, nainstalujte .NET Core SDK 2.0 (vs. 2.1.201) a starších na vašem počítači a definovat požadovanou verzi sady SDK pomocí *global.json* souboru. Další informace o `dotnet ef` naleznete [nástroje příkazového řádku .NET Core EF](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Viz také:

* [Způsob řešení projekt sady SDK](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
