---
title: global.json – přehled
description: Naučte se používat soubor Global. JSON k nastavení verze .NET Core SDK při spouštění příkazů .NET Core CLI.
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: f02c9129a707ddddb2c5e1975b75cc35abc5cd55
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733975"
---
# <a name="globaljson-overview"></a>global.json – přehled

**Tento článek se týká:** ✔️ .net Core 2,0 SDK a novějších verzí

Soubor *Global. JSON* umožňuje definovat, která verze .NET Core SDK se používá při spuštění příkazů .NET Core CLI. Výběr .NET Core SDK je nezávislý na určení modulu runtime, který cílí na projekt. Verze .NET Core SDK označuje, které verze .NET Core CLIch nástrojů se používají.

Obecně platí, že chcete použít nejnovější verzi nástrojů SDK, takže není potřeba žádný soubor *Global. JSON* . V některých pokročilých scénářích můžete chtít řídit verzi nástrojů sady SDK a tento článek vysvětluje, jak to provést.

Další informace o určení modulu runtime místo toho naleznete v tématu [cílová rozhraní](../../standard/frameworks.md).

.NET Core SDK vyhledá soubor *Global. JSON* v aktuálním pracovním adresáři (to není nutně stejný jako adresář projektu) nebo v jednom z jeho nadřazených adresářů.

## <a name="globaljson-schema"></a>Global. JSON – schéma

### <a name="sdk"></a>sdk

Zadejte: `object`

Určuje informace o .NET Core SDK k výběru.

#### <a name="version"></a>Verze nástroje

- Zadejte: `string`

- Dostupné od verze: .NET Core 1,0 SDK.

Verze .NET Core SDK, která se má použít

Toto pole:

- Nemá podporu zástupných znaků, to znamená, že je nutné zadat úplné číslo verze.
- Nepodporuje rozsahy verzí.

#### <a name="allowprerelease"></a>allowPrerelease

- Zadejte: `boolean`

- Dostupné od verze: .NET Core 3,0 SDK.

Určuje, zda má Řešitel sady SDK zvážit předprodejní verze při výběru verze sady SDK, která se má použít.

Pokud tuto hodnotu nenastavíte explicitně, bude výchozí hodnota záviset na tom, jestli spouštíte ze sady Visual Studio:

- Pokud nejste **v aplikaci** Visual Studio, výchozí hodnota je `true`.
- Pokud jste v aplikaci Visual Studio, použije se požadovaný stav předprodejní verze. To znamená, že pokud používáte verzi Preview sady Visual Studio nebo jste nastavili náhledy **použití možnosti .NET Core SDK** (v části **nástroje** > **Možnosti** ** >  > ** funkce ve **verzi Preview**), výchozí hodnota je `true`; v opačném případě `false`.

#### <a name="rollforward"></a>Dopředné obnovení

- Zadejte: `string`

- Dostupné od verze: .NET Core 3,0 SDK.

Zásada pro převzetí služeb při obnovení, která se má použít při výběru verze sady SDK, a to buď jako záložní, pokud konkrétní verze sady SDK chybí, nebo jako direktiva pro použití vyšší verze. Pokud nenastavujete `latestMajor`, je nutné zadat [verzi](#version) s `rollForward` hodnotou.

Pro pochopení dostupných zásad a jejich chování zvažte následující definice verze sady SDK ve formátu `x.y.znn`:

- `x` je hlavní verze.
- `y` je vedlejší verze.
- `z` je pásmo funkcí.
- `nn` je verze opravy.

Následující tabulka uvádí možné hodnoty pro `rollForward` klíč:

| Hodnota         | Chování |
| ------------- | ---------- |
| `patch`       | Používá zadanou verzi. <br> Pokud se nenajde, vrátí se k nejnovější úrovni oprav. <br> Pokud se nenalezne, dojde k chybě. <br><br> Tato hodnota je starší verze chování z dřívějších verzí sady SDK. |
| `feature`     | Používá nejnovější úroveň opravy pro zadaný hlavní, vedlejší a funkční pásmo. <br> Pokud se nenajde, vrátí se k nejbližšímu novému pásma funkce v rámci stejné hlavní nebo dílčí funkce a použije nejnovější úroveň opravy pro daný panel funkcí. <br> Pokud se nenalezne, dojde k chybě. |
| `minor`       | Používá nejnovější úroveň opravy pro zadaný hlavní, vedlejší a funkční pásmo. <br> Pokud se nenajde, vrátí se k nejbližšímu pásmu funkce v rámci stejné hlavní nebo dílčí verze a použije se nejnovější úroveň opravy pro tento panel funkcí. <br> Pokud se nenalezne, vrátí se k nejbližšímu vyššímu menšímu množství a rozstupnému pásma funkcí v rámci stejné hlavní úrovně a použije se nejnovější úroveň opravy pro daný panel funkcí. <br> Pokud se nenalezne, dojde k chybě. |
| `major`       | Používá nejnovější úroveň opravy pro zadaný hlavní, vedlejší a funkční pásmo. <br> Pokud se nenajde, vrátí se k nejbližšímu pásmu funkce v rámci stejné hlavní nebo dílčí verze a použije se nejnovější úroveň opravy pro tento panel funkcí. <br> Pokud se nenalezne, vrátí se k nejbližšímu vyššímu menšímu množství a rozstupnému pásma funkcí v rámci stejné hlavní úrovně a použije se nejnovější úroveň opravy pro daný panel funkcí. <br> Pokud se nenalezne, vrátí se k nejbližšímu většímu hornímu, vedlejšímu a funkčnímu pásmu a použije se nejnovější úroveň opravy pro daný panel funkcí. <br> Pokud se nenalezne, dojde k chybě. |
| `latestPatch` | Používá nejnovější nainstalovanou úroveň opravy, která odpovídá požadovanému hlavnímu, vedlejšímu a funkčnímu pásmu funkce s úrovní oprav a která je větší nebo rovna zadané hodnotě. <br> Pokud se nenalezne, dojde k chybě. |
| `latestFeature` | Používá nejvyšší instalovaný pruh funkcí a úroveň oprav odpovídající požadovanému hlavnímu a dílčímu pásmu s pásem funkcí, který je větší nebo roven zadané hodnotě. <br> Pokud se nenalezne, dojde k chybě. |
| `latestMinor` | Používá nejvyšší instalovaný podřízený, panel funkcí a úroveň oprav, které odpovídají požadované hlavní hodnotě, která je větší nebo rovna zadané hodnotě. <br> Pokud se nenalezne, dojde k chybě. |
| `latestMajor` | Používá nejvyšší nainstalované .NET Core SDK s větší nebo rovnou zadané hodnotě. <br> Pokud se nenalezne, selže. |
| `disable`     | Nevede k posunutí. Požaduje se přesná shoda. |

## <a name="examples"></a>Příklady

Následující příklad ukazuje, jak používat předprodejní verze:

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

Následující příklad ukazuje, jak použít nejvyšší nainstalovanou verzi, která je větší nebo rovna zadané verzi:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

Následující příklad ukazuje, jak použít přesně určenou verzi:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

Následující příklad ukazuje, jak použít nejvyšší verzi opravy nainstalovanou specifickou verzi (ve formuláři, 3.1.1 xx):

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>Global. JSON a .NET Core CLI

Je užitečné zjistit, které verze sady SDK jsou nainstalovány na vašem počítači, aby je bylo možné nastavit v *globálním souboru. JSON* . Další informace o tom, jak to provést, najdete v tématu [Jak ověřit, že je rozhraní .NET Core již nainstalováno](../install/how-to-detect-installed-versions.md#check-sdk-versions).

Pokud chcete na svém počítači nainstalovat další .NET Core SDK verze, navštivte stránku [Stáhnout .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .

Nový soubor *Global. JSON* můžete v aktuálním adresáři vytvořit spuštěním příkazu [dotnet New](dotnet-new.md) , podobně jako v následujícím příkladu:

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>Pravidla pro porovnání

> [!NOTE]
> Pravidla pro porovnání se řídí vstupním bodem `dotnet.exe`, který je společný pro všechny nainstalované moduly runtime .NET Core nainstalované v. Pravidla pro porovnání pro nejnovější nainstalovanou verzi modulu runtime .NET Core se používají, když máte více nainstalovaných modulů runtime vedle sebe.

## <a name="net-core-3xtabnetcore3x"></a>[.NET Core 3. x](#tab/netcore3x)

Počínaje rozhraním .NET Core 3,0 se při určování používané verze sady SDK použijí následující pravidla:

- Pokud není nalezen žádný soubor *Global. JSON* , nebo soubor *Global. JSON* neurčuje verzi sady SDK ani hodnotu `allowPrerelease`, použije se nejvyšší nainstalovaná verze sady sdk (ekvivalent nastavení `rollForward` `latestMajor`). Informace o `dotnet` tom, zda jsou vyvolány verze předprodejní verze sady SDK, závisí na tom, jak je
  - Pokud nejste **v aplikaci** Visual Studio, předprodejní verze se považují za.
  - Pokud jste v aplikaci Visual Studio, použije se požadovaný stav předprodejní verze. To znamená, že pokud používáte verzi Preview sady Visual Studio nebo jste nastavili náhledy **použití možnosti .NET Core SDK** (v části **nástroje** > **Možnosti** ** >  > ** **funkce verze Preview**), předprodejní verze se považují za. v opačném případě jsou zváženy pouze verze Release.
- Pokud je nalezen soubor *Global. JSON* , který neurčuje verzi sady SDK, ale určuje `allowPrerelease` hodnotu, použije se nejvyšší nainstalovaná verze sady SDK (ekvivalent nastavení `rollForward` `latestMajor`). Bez ohledu na to, zda může být vydání nejnovější verze sady SDK nebo předběžná verze, závisí na hodnotě `allowPrerelease`. `true` označuje, že předprodejní verze jsou zváženy. `false` označuje, že se považují jenom verze Release.
- Pokud je nalezen soubor *Global. JSON* a určuje verzi sady SDK:

  - Pokud není nastavená žádná `rollFoward` hodnota, použije se jako výchozí zásada pro `rollForward` `latestPatch`. V opačném případě Ověřte všechny hodnoty a jejich chování v části [dopředné obnovení](#rollforward) .
  - Bez ohledu na to, jestli jsou předprodejní verze zvážené a jaké je výchozí chování, když `allowPrerelease` není nastavené, je popsané v části [allowPrerelease](#allowprerelease) .

## <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

V sadě .NET Core 2. x SDK se při určování používané verze sady SDK použijí následující pravidla:

- Pokud nebyl nalezen soubor *Global. JSON* nebo soubor *Global. JSON* neurčuje verzi sady SDK, bude použita nejnovější nainstalovaná verze sady SDK. Nejnovější verze sady SDK může být verze nebo předběžná verze – nejvyšší číslo verze služby WINS.
- Pokud *Global. JSON* určí verzi sady SDK:
  - Pokud je v počítači nalezena zadaná verze sady SDK, je použita tato přesná verze.
  - Pokud se zadaná verze sady SDK v tomto počítači nenajde, použije se nejnovější nainstalovaná **verze opravy** SDK této verze. Nejnovější nainstalovaná **verze opravy** sady SDK může být buď verze, nebo předprodejní verze – nejvyšší číslo verze služby WINS. V .NET Core 2,1 a novějších **verzích opravy** nižší, než je zadaná **verze opravy** , se v výběru sady SDK ignorují.
  - Pokud není nalezena zadaná verze sady SDK a příslušná **verze opravy** sady SDK, je vyvolána chyba.

Verze sady SDK se skládá z následujících částí:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

**Verze .NET Core SDK funkce** je vyjádřena první číslicí (`x`) v poslední části čísla (`xyz`) pro sady SDK verze 2.1.100 a vyšší. Obecně platí, že .NET Core SDK má rychlejší cyklus vydávání verzí než .NET Core.

**Verze opravy** je definována posledními dvěma číslicemi (`yz`) v poslední části čísla (`xyz`) pro sady SDK verze 2.1.100 a vyšší. Například pokud zadáte `2.1.300` jako verzi sady SDK, výběr sady SDK vyhledá až `2.1.399`, ale `2.1.400` není považována za verzi opravy `2.1.300`.

.NET Core SDK verze `2.1.100` prostřednictvím `2.1.201` byly vydány během přechodu mezi schématy čísel verzí a nesprávně nezpracovávají `xyz` notace. Důrazně doporučujeme, pokud zadáte tyto verze v souboru *Global. JSON* , abyste zajistili, že zadané verze jsou na cílových počítačích.

---

## <a name="troubleshooting-build-warnings"></a>Řešení potíží s upozorněními sestavení

> [!WARNING]
> Pracujete s verzí Preview .NET Core SDK. Verzi sady SDK můžete definovat prostřednictvím globálního souboru. JSON v aktuálním projektu. Další na <https://go.microsoft.com/fwlink/?linkid=869452>

Toto upozornění znamená, že projekt byl zkompilován pomocí předprodejní verze .NET Core SDK. Verze .NET Core SDK mají historii a závazek vysoké kvality. Pokud ale nechcete použít předběžnou verzi, Projděte si různé strategie, které můžete použít se sadou .NET Core 3,0 SDK nebo novější verzí v části [allowPrerelease](#allowprerelease) . Pro počítače, které nikdy nemají nainstalovanou sadu .NET Core 3,0 nebo novější modul runtime nebo sadu SDK, je třeba vytvořit soubor *Global. JSON* a zadat přesnou verzi, kterou chcete použít.

> [!WARNING]
> Spouštěcí projekt {startupProject} cílí na rozhraní Framework. NETCoreApp verze {targetFrameworkVersion}. Tato verze nástrojů příkazového řádku Entity Framework Core .NET podporuje pouze verzi 2,0 nebo vyšší. Informace o použití starších verzí nástrojů najdete v tématu <https://go.microsoft.com/fwlink/?linkid=871254>

Počínaje sadou .NET Core 2,1 SDK (verze 2.1.300) se v sadě SDK nachází příkaz `dotnet ef`. Toto upozornění znamená, že projekt cílí na EF Core 1,0 nebo 1,1, což není kompatibilní s .NET Core 2,1 SDK a novějšími verzemi. Chcete-li zkompilovat projekt, nainstalujte sadu .NET Core 2,0 SDK (verze 2.1.201) a dřívější na váš počítač a definujte požadovanou verzi sady SDK pomocí souboru *Global. JSON* . Další informace o příkazu `dotnet ef` najdete v tématu [EF Core nástroje příkazového řádku .NET](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Viz také:

- [Jak se řeší sady SDK projektu](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
