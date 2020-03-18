---
title: global.json – přehled
description: Přečtěte si, jak pomocí souboru global.json nastavit verzi sady .NET Core SDK při spouštění příkazů rozhraní PŘÍKAZOVÉHO PŘÍKAZU .NET Core.
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 70257566e1ff30f5c97212a5e0e3c308c27738b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625992"
---
# <a name="globaljson-overview"></a>global.json – přehled

**Tento článek se týká:** ✔️ .NET Core 2.0 SDK a novější verze

Soubor *global.json* umožňuje definovat, která verze sady .NET Core SDK se používá při spuštění příkazů rozhraní PŘÍKAZOVÉHO PŘÍKAZU .NET Core. Výběr sady .NET Core SDK je nezávislý na určení běhu cílů projektu. Verze sady .NET Core SDK označuje, které verze rozhraní PŘÍKAZU .NET Core CLI se používají.

Obecně chcete použít nejnovější verzi nástrojů sady SDK, takže není potřeba žádný soubor *global.json.* V některých pokročilých scénářích můžete chtít řídit verzi nástrojů sady SDK a tento článek vysvětluje, jak to provést.

Další informace o určení runtime místo toho naleznete v tématu [cílové architektury](../../standard/frameworks.md).

Sada .NET Core SDK hledá soubor *global.json* v aktuálním pracovním adresáři (který nemusí být nutně stejný jako adresář projektu) nebo v jednom z nadřazených adresářů.

## <a name="globaljson-schema"></a>schéma global.json

### <a name="sdk"></a>SDK

Typ:`object`

Určuje informace o vybertece sady .NET Core SDK.

#### <a name="version"></a>version

- Typ:`string`

- K dispozici od: .NET Core 1.0 SDK.

Verze sady .NET Core SDK, která má být používána.

Toto pole:

- Nemá podporu zástupných symbolů, to znamená, že musí být zadáno číslo plné verze.
- Nepodporuje rozsahy verzí.

#### <a name="allowprerelease"></a>allowPředběžné vydání

- Typ:`boolean`

- K dispozici od: .NET Core 3.0 SDK.

Označuje, zda by měl překladač sady SDK zvážit předběžné verze při výběru verze sady SDK, která má být používána.

Pokud tuto hodnotu nenastavíte explicitně, výchozí hodnota závisí na tom, jestli používáte z Visual Studia:

- Pokud **nejste** ve Visual Studiu, výchozí `true`hodnota je .
- Pokud jste v sadě Visual Studio, používá požadovaný stav předběžné verze. To znamená, že pokud používáte verzi Preview sady Visual Studio nebo nastavíte možnost Použít náhledy sady **.NET Core SDK** (v části Funkce**náhledu** >  **prostředí tools** > **Options** > **Environment ),** je `true`výchozí hodnota ; v `false`opačném případě .

#### <a name="rollforward"></a>rollForward

- Typ:`string`

- K dispozici od: .NET Core 3.0 SDK.

Zásady pro předávání vpřed, které se mají použít při výběru verze sady SDK, buď jako záložní, pokud chybí konkrétní verze sady SDK, nebo jako direktivu pro použití vyšší verze. [Verze](#version) musí být zadána s hodnotou, `rollForward` pokud `latestMajor`ji nenastavujete na .

Chcete-li porozumět dostupným zásadám a jejich chování, zvažte následující `x.y.znn`definice pro verzi sady SDK ve formátu :

- `x`je hlavní verze.
- `y`je dílčí verze.
- `z`je pásmo funkcí.
- `nn`je verze opravy.

V následující tabulce jsou uvedeny možné hodnoty `rollForward` klíče:

| Hodnota         | Chování |
| ------------- | ---------- |
| `patch`       | Používá zadanou verzi. <br> Pokud není nalezen, převalí dopředu na nejnovější úroveň opravy. <br> Pokud nebyl nalezen, selže. <br><br> Tato hodnota je starší chování z předchozích verzí sady SDK. |
| `feature`     | Používá nejnovější úroveň opravy pro zadané hlavní, menší a funkční pásmo. <br> Pokud není nalezen, převrátí se na další vyšší pásmo funkcí v rámci stejného hlavního/vedlejšího a použije nejnovější úroveň opravy pro toto pásmo funkcí. <br> Pokud nebyl nalezen, selže. |
| `minor`       | Používá nejnovější úroveň opravy pro zadané hlavní, menší a funkční pásmo. <br> Pokud není nalezen, převrátí se do dalšího vyššího pásma funkcí v rámci stejné hlavní/dílčí verze a použije nejnovější úroveň opravy pro toto pásmo funkcí. <br> Pokud není nalezen, převrátí se na další vyšší minor a pásmo funkcí v rámci stejného hlavního a použije nejnovější úroveň opravy pro toto pásmo funkcí. <br> Pokud nebyl nalezen, selže. |
| `major`       | Používá nejnovější úroveň opravy pro zadané hlavní, menší a funkční pásmo. <br> Pokud není nalezen, převrátí se do dalšího vyššího pásma funkcí v rámci stejné hlavní/dílčí verze a použije nejnovější úroveň opravy pro toto pásmo funkcí. <br> Pokud není nalezen, převrátí se na další vyšší minor a pásmo funkcí v rámci stejného hlavního a použije nejnovější úroveň opravy pro toto pásmo funkcí. <br> Pokud není nalezen, převrátí se na další vyšší hlavní, menší a funkční pásmo a použije nejnovější úroveň opravy pro toto pásmo funkcí. <br> Pokud nebyl nalezen, selže. |
| `latestPatch` | Používá nejnovější nainstalovanou úroveň opravy, která odpovídá požadovanému hlavnímu, menšímu a funkčnímu pásmu s úrovní opravy a která je větší nebo rovna než zadaná hodnota. <br> Pokud nebyl nalezen, selže. |
| `latestFeature` | Používá nejvyšší nainstalované pásmo funkcí a úroveň opravy, která odpovídá požadované mutovi a menší mu, s pásmem prvků, které je větší nebo rovno zadané hodnotě. <br> Pokud nebyl nalezen, selže. |
| `latestMinor` | Používá nejvyšší nainstalované dílčí, pásmo funkcí a úroveň opravy, která odpovídá požadované mutovi, s podřadnou, která je větší nebo rovna zadané hodnotě. <br> Pokud nebyl nalezen, selže. |
| `latestMajor` | Používá nejvyšší nainstalovanou sadu .NET Core SDK s hlavní, která je větší nebo rovna než zadaná hodnota. <br> Pokud není nalezen, selhání. |
| `disable`     | Nekupředu. Přesná shoda nutná. |

## <a name="examples"></a>Příklady

Následující příklad ukazuje, jak nepoužívat předběžné verze:

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

Následující příklad ukazuje, jak používat nejvyšší nainstalovanou verzi, která je větší nebo rovna než zadaná verze:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

Následující příklad ukazuje, jak používat přesně zadanou verzi:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

Následující příklad ukazuje, jak používat nejvyšší verzi opravy nainstalovanou pro konkrétní verzi (ve formuláři 3.1.1xx):

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.json a rozhraní CLI jádra .NET

Je užitečné vědět, které verze sady SDK jsou nainstalovány v počítači a nastavit je v souboru *global.json.* Další informace o tom, jak to provést, naleznete v [tématu Jak zkontrolovat, zda je jádro .NET Core již nainstalováno](../install/how-to-detect-installed-versions.md#check-sdk-versions).

Chcete-li do počítače nainstalovat další verze sady .NET Core SDK, navštivte stránku [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .

Nový soubor *global.json* můžete vytvořit v aktuálním adresáři spuštěním nového příkazu [dotnet,](dotnet-new.md) podobně jako v následujícím příkladu:

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>Pravidla párování

> [!NOTE]
> Pravidla párování se řídí `dotnet.exe` vstupním bodem, který je společný pro všechny nainstalované runtimesy nainstalované rozhraním .NET Core. Pravidla párování pro nejnovější nainstalovanou verzi rozhraní .NET Core Runtime se používají, pokud máte vedle sebe nainstalováno více runtimeů.

## <a name="net-core-3x"></a>[.NET Jádro 3.x](#tab/netcore3x)

Počínaje rozhraním .NET Core 3.0 platí při určování, kterou verzi sady SDK použít, následující pravidla:

- Pokud není nalezen žádný soubor *global.json* nebo *global.json* neurčuje verzi `allowPrerelease` sady SDK ani hodnotu, použije `rollForward` se `latestMajor`nejvyšší nainstalovaná verze sady SDK (ekvivalentní nastavení). Zda předběžné verze sady SDK jsou `dotnet` považovány za závisí na jak je vyvolána.
  - Pokud **nejste** v sadě Visual Studio, jsou považovány za předběžné verze.
  - Pokud jste v sadě Visual Studio, používá požadovaný stav předběžné verze. To znamená, že pokud používáte verzi Preview sady Visual Studio nebo nastavíte **použít náhledy možnosti .NET Core SDK** (v části **Tools** > **Options** > **Environment** > **Preview Features),** budou předběžné verze považovány za; v opačném případě jsou považovány pouze verze verze.
- Pokud je nalezen soubor *global.json,* který neurčuje verzi sady SDK, ale určuje hodnotu, `allowPrerelease` použije se `rollForward` `latestMajor`nejvyšší nainstalovaná verze sady SDK (ekvivalentní nastavení ). To, zda nejnovější verze sady SDK může být `allowPrerelease`vydána nebo předběžná verze, závisí na hodnotě aplikace . `true`označuje, že jsou zváženy předběžné verze; `false` označuje, že jsou považovány pouze verze vydání.
- Pokud je nalezen soubor *global.json* a určuje verzi sady SDK:

  - Pokud `rollFoward` není nastavena žádná `latestPatch` hodnota, `rollForward` použije se jako výchozí zásada. V opačném případě zkontrolujte každou hodnotu a jejich chování v části [rollForward.](#rollforward)
  - Zda předběžné verze jsou považovány za a co `allowPrerelease` je výchozí chování, když není nastavena je popsána v [allowPrerelease](#allowprerelease) části.

## <a name="net-core-2x"></a>[.NET Jádro 2.x](#tab/netcore2x)

V sdk .NET Core 2.x Platí následující pravidla při určování, kterou verzi sady SDK použít:

- Pokud není nalezen žádný soubor *global.json* nebo *global.json* neurčuje verzi sady SDK, použije se nejnovější nainstalovaná verze sady SDK. Nejnovější verze sady SDK může být buď vydána, nebo předběžná verze - nejvyšší číslo verze vyhrává.
- Pokud *global.json* určit verzi sady SDK:
  - Pokud je v počítači nalezena zadaná verze sady SDK, použije se tato přesná verze.
  - Pokud zadanou verzi sady SDK nelze v počítači najít, bude použita nejnovější nainstalovaná **verze opravy** sady SDK této verze. Nejnovější nainstalovaná **verze opravy** Sady SDK může být buď vydána, nebo předběžná verze - nejvyšší číslo verze vyhrává. V rozhraní .NET Core 2.1 a vyšší jsou **verze opravy** nižší než zadaná **verze opravy** ve výběru sady SDK ignorovány.
  - Pokud zadanou verzi sady SDK a příslušnou **verzi opravy** sady SDK nelze najít, je vyvolána chyba.

Verze sady SDK se skládá z následujících částí:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

**Verze funkce** sady .NET Core SDK je reprezentována první číslicí (`x`) v poslední části čísla (`xyz`) pro sady SDK verze 2.1.100 a vyšší. Obecně platí, že sada .NET Core SDK má rychlejší cyklus vydání než .NET Core.

**Verze opravy** je definována posledními`yz`dvěma číslicemi (`xyz`) v poslední části čísla ( ) pro sady SDK verze 2.1.100 a vyšší. Pokud například zadáte `2.1.300` jako verzi sady SDK, výběr `2.1.399` sady `2.1.400` SDK najde až `2.1.300`do, ale není považován za verzi opravy pro .

Verze sady .NET Core `2.1.100` `2.1.201` SDK byly vydány během přechodu mezi schématy čísel verzí a zápis nezpracovávají `xyz` správně. Důrazně doporučujeme, pokud zadáte tyto verze v souboru *global.json,* ujistěte se, že zadané verze jsou na cílových počítačích.

---

## <a name="troubleshoot-build-warnings"></a>Poradce při potížích s upozorněními na sestavení

* Následující upozornění označuje, že váš projekt byl zkompilován pomocí předběžné verze sady .NET Core SDK:

  > Pracujete s verzí preview sady .NET Core SDK. Verzi sady SDK můžete definovat prostřednictvím souboru global.json v aktuálním projektu. Více <https://go.microsoft.com/fwlink/?linkid=869452>na .

  Verze sady .NET Core SDK mají historii a závazek vysoké kvality. Pokud však nechcete používat předběžnou verzi, zkontrolujte různé strategie, které můžete použít s sadou .NET Core 3.0 SDK nebo novější verzí v části [allowPrerelease.](#allowprerelease) U počítačů, které nikdy neměly nainstalovanou runtime .NET Core 3.0 nebo vyšší nebo sdk, je třeba vytvořit soubor *global.json* a zadat přesnou verzi, kterou chcete použít.

* Následující upozornění označuje, že váš projekt cíle EF Core 1.0 nebo 1.1, který není kompatibilní s .NET Core 2.1 SDK a novější verze:

  > Projekt spuštění projektu {startupProject} cílí na rozhraní ". NETCoreApp' verze '{targetFrameworkVersion}'. Tato verze nástrojů příkazového řádku entity Framework .NET .NET podporuje pouze verzi 2.0 nebo vyšší. Informace o používání starších verzí nástrojů <https://go.microsoft.com/fwlink/?linkid=871254>naleznete v tématu .

  Počínaje .NET Core 2.1 SDK (verze 2.1.300), `dotnet ef` příkaz je součástí sady SDK. Chcete-li zkompilovat projekt, nainstalujte do počítače sady .NET Core 2.0 SDK (verze 2.1.201) nebo starší a definujte požadovanou verzi sady SDK pomocí souboru *global.json.* Další informace o `dotnet ef` příkazu naleznete v tématu [EF Core .NET Nástroje příkazového řádku](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Viz také

- [Jak jsou sady SDK projektu vyřešeny](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
