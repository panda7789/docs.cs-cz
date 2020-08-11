---
title: global.json – přehled
description: Naučte se používat global.jsv souboru k nastavení verze .NET Core SDK při spouštění .NET Core CLIch příkazů.
ms.topic: how-to
ms.date: 05/01/2020
ms.custom: updateeachrelease
ms.openlocfilehash: a9558090b1ef48f376334fbc826f6265a58908da
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062792"
---
# <a name="globaljson-overview"></a>global.json – přehled

**Tento článek se týká:** ✔️ .net Core 2,0 SDK a novějších verzí

*global.jsv* souboru umožňuje definovat, která verze .NET Core SDK se používá při spuštění .NET Core CLI příkazů. Výběr .NET Core SDK je nezávislý na určení modulu runtime, který cílí na projekt. Verze .NET Core SDK označuje, které verze .NET Core CLI se používají.

Obecně platí, že chcete použít nejnovější verzi nástrojů SDK, takže není potřeba žádné *global.jsv* souboru. V některých pokročilých scénářích můžete chtít řídit verzi nástrojů sady SDK a tento článek vysvětluje, jak to provést.

Další informace o určení modulu runtime místo toho naleznete v tématu [cílová rozhraní](../../standard/frameworks.md).

.NET Core SDK vyhledá *global.jsv* souboru v aktuálním pracovním adresáři (což není nutně stejné jako adresář projektu) nebo jeden z jeho nadřazených adresářů.

## <a name="globaljson-schema"></a>global.jsve schématu

### <a name="sdk"></a>SDK

Textový`object`

Určuje informace o .NET Core SDK k výběru.

#### <a name="version"></a>verze

- Textový`string`

- Dostupné od verze: .NET Core 1,0 SDK.

Verze .NET Core SDK, která se má použít

Toto pole:

- Nemá podporu zástupných znaků, to znamená, že je nutné zadat úplné číslo verze.
- Nepodporuje rozsahy verzí.

#### <a name="allowprerelease"></a>allowPrerelease

- Textový`boolean`

- Dostupné od verze: .NET Core 3,0 SDK.

Určuje, zda má Řešitel sady SDK zvážit předprodejní verze při výběru verze sady SDK, která se má použít.

Pokud tuto hodnotu nenastavíte explicitně, bude výchozí hodnota záviset na tom, jestli spouštíte ze sady Visual Studio:

- Pokud nejste **v aplikaci** Visual Studio, výchozí hodnota je `true` .
- Pokud jste v aplikaci Visual Studio, použije se požadovaný stav předprodejní verze. To znamená, že pokud používáte verzi Preview sady Visual Studio nebo pokud nastavíte náhled **použití pro .NET Core SDK** možnosti (v části **nástroje**  >  **Možnosti**  >  **prostředí**  >  **verze Preview**), výchozí hodnota je. `true` v opačném případě `false` .

#### <a name="rollforward"></a>Dopředné obnovení

- Textový`string`

- Dostupné od verze: .NET Core 3,0 SDK.

Zásada pro převzetí služeb při obnovení, která se má použít při výběru verze sady SDK, a to buď jako záložní, pokud konkrétní verze sady SDK chybí, nebo jako direktiva pro použití vyšší verze. [Verze](#version) musí být zadána s `rollForward` hodnotou, pokud ji nenastavujete na `latestMajor` .

Pro pochopení dostupných zásad a jejich chování zvažte následující definice verze sady SDK ve formátu `x.y.znn` :

- `x`je hlavní verze.
- `y`je vedlejší verze.
- `z`je pásmo funkce.
- `nn`je verze opravy.

V následující tabulce jsou uvedeny možné hodnoty pro `rollForward` klíč:

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

### <a name="msbuild-sdks"></a>MSBuild – sady SDK

Textový`object`

Umožňuje řídit verzi sady SDK projektu na jednom místě a nikoli v jednotlivých projektech. Další informace najdete v tématu [jak se řeší sady SDK projektu](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).

## <a name="examples"></a>Příklady

Následující příklad ukazuje, jak používat předprodejní verze:

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

Následující příklad ukazuje, jak použít nejvyšší nainstalovanou verzi, která je větší nebo rovna zadané verzi. Zobrazený kód JSON nepovoluje žádnou verzi sady SDK starší než 2.2.200 a umožňuje 2.2.200 nebo jakoukoliv novější verzi, včetně 3.0.xxx a 3.1.xxx.

```json
{
  "sdk": {
    "version": "2.2.200",
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

Následující příklad ukazuje, jak použít nejnovější panel funkcí a nainstalovanou verzi opravy pro konkrétní hlavní a dílčí verzi. Zobrazený kód JSON nepovoluje žádnou verzi sady SDK starší než 3.1.102 a umožňuje 3.1.102 nebo jakoukoliv novější verzi 3.1.xxx, jako je například 3.1.103 nebo 3.1.200.

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestFeature"
  }
}
```

Následující příklad ukazuje, jak použít nejvyšší verzi opravy nainstalovanou specifickou verzí. Zobrazený kód JSON nepovoluje žádnou verzi sady SDK starší než 3.1.102 a umožňuje 3.1.102 nebo jakékoli pozdější verze 3.1.1 xx, jako je 3.1.103 nebo 3.1.199.

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.jsa .NET Core CLI

Je užitečné zjistit, které verze SDK jsou nainstalovány na vašem počítači, abyste je nastavili v *global.jsv* souboru. Další informace o tom, jak to provést, najdete v tématu [Jak ověřit, že je rozhraní .NET Core již nainstalováno](../install/how-to-detect-installed-versions.md#check-sdk-versions).

Pokud chcete na svém počítači nainstalovat další .NET Core SDK verze, navštivte stránku [Stáhnout .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .

Můžete vytvořit nový *global.js* v souboru v aktuálním adresáři spuštěním příkazu [dotnet New](dotnet-new.md) , podobně jako v následujícím příkladu:

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>Pravidla pro porovnání

> [!NOTE]
> Pravidla pro porovnání se řídí `dotnet.exe` vstupním bodem, který je společný pro všechny nainstalované moduly runtime .NET Core nainstalované v. Pravidla pro porovnání pro nejnovější nainstalovanou verzi modulu runtime .NET Core se používají, když máte více nainstalovaných modulů runtime vedle sebe.

## <a name="net-core-3x"></a>[.NET Core 3. x](#tab/netcore3x)

Počínaje rozhraním .NET Core 3,0 se při určování používané verze sady SDK použijí následující pravidla:

- Pokud se *v* souboru nenajde žádnáglobal.jsnebo pokud *global.js* neurčí verzi sady SDK ani `allowPrerelease` hodnotu, použije se nejvyšší nainstalovaná verze sady SDK (ekvivalent nastavení `rollForward` `latestMajor` ). Informace o tom, zda jsou verze předprodejních sad zvažovány, závisí na způsobu `dotnet` jejich vyvolání.
  - Pokud nejste **v aplikaci** Visual Studio, předprodejní verze se považují za.
  - Pokud jste v aplikaci Visual Studio, použije se požadovaný stav předprodejní verze. To znamená, že pokud používáte verzi Preview sady Visual Studio nebo jste nastavili verze Preview pro **použití .NET Core SDK** (v části **nástroje**  >  **Možnosti**  >  **prostředí**  >  **verze Preview**), jsou předprodejní verze zváženy. v opačném případě jsou zváženy pouze verze Release.
- Pokud je nalezen *global.jsv* souboru, který neurčuje verzi sady SDK, ale určí `allowPrerelease` hodnotu, použije se nejvyšší nainstalovaná verze sady SDK (ekvivalent nastavení `rollForward` `latestMajor` ). Bez ohledu na to, zda může být verze sady SDK nebo předběžná verze nejnovější, závisí na hodnotě `allowPrerelease` . `true`označuje, že předprodejní verze jsou zváženy; `false`indikuje, že se považují jenom verze Release.
- Pokud je nalezen *global.jspro* soubor a určuje verzi sady SDK:

  - Pokud `rollFoward` není nastavená žádná hodnota, použije se `latestPatch` jako výchozí `rollForward` zásada. V opačném případě Ověřte všechny hodnoty a jejich chování v části [dopředné obnovení](#rollforward) .
  - Bez ohledu na to, jestli jsou předprodejní verze zvážené a jaké je výchozí chování, když není `allowPrerelease` nastavené, je popsané v části [allowPrerelease](#allowprerelease) .

## <a name="net-core-2x"></a>[.NET Core 2. x](#tab/netcore2x)

V sadě .NET Core 2. x SDK se při určování používané verze sady SDK použijí následující pravidla:

- Pokud se *v* souboru nenajdeglobal.jsnebo *global.js* neurčí verzi sady SDK, použije se nejnovější nainstalovaná verze sady SDK. Nejnovější verze sady SDK může být verze nebo předběžná verze – nejvyšší číslo verze služby WINS.
- Pokud *global.json* , zadejte verzi sady SDK:
  - Pokud je v počítači nalezena zadaná verze sady SDK, je použita tato přesná verze.
  - Pokud se zadaná verze sady SDK v tomto počítači nenajde, použije se nejnovější nainstalovaná **verze opravy** SDK této verze. Nejnovější nainstalovaná **verze opravy** sady SDK může být buď verze, nebo předprodejní verze – nejvyšší číslo verze služby WINS. V .NET Core 2,1 a novějších **verzích opravy** nižší, než je zadaná **verze opravy** , se v výběru sady SDK ignorují.
  - Pokud není nalezena zadaná verze sady SDK a příslušná **verze opravy** sady SDK, je vyvolána chyba.

Verze sady SDK se skládá z následujících částí:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

**Verze .NET Core SDK funkce** je vyjádřena první číslicí ( `x` ) v poslední části čísla ( `xyz` ) pro sadu SDK verze 2.1.100 a vyšší. Obecně platí, že .NET Core SDK má rychlejší cyklus vydávání verzí než .NET Core.

**Verze opravy** je definována posledními dvěma číslicemi ( `yz` ) v poslední části čísla ( `xyz` ) pro sadu SDK verze 2.1.100 a vyšší. Pokud například zadáte `2.1.300` jako verzi sady SDK, výběr sady SDK vyhledá, `2.1.399` ale `2.1.400` nepovažuje se za verzi opravy pro `2.1.300` .

.NET Core SDK verze `2.1.100` prostřednictvím `2.1.201` byly vydány během přechodu mezi schématy čísel verzí a nesprávně nezpracovávají `xyz` zápis. Důrazně doporučujeme, pokud zadáte tyto verze v souboru *global.json* , abyste zajistili, že zadané verze jsou na cílových počítačích.

---

## <a name="troubleshoot-build-warnings"></a>Řešení potíží s upozorněními sestavení

* Následující upozornění indikuje, že projekt byl zkompilován pomocí předprodejní verze .NET Core SDK:

  > Pracujete s verzí Preview .NET Core SDK. Verzi sady SDK můžete definovat pomocí global.jsv souboru v aktuálním projektu. Další informace najdete na adrese <https://go.microsoft.com/fwlink/?linkid=869452> .

  Verze .NET Core SDK mají historii a závazek vysoké kvality. Pokud ale nechcete použít předběžnou verzi, Projděte si různé strategie, které můžete použít se sadou .NET Core 3,0 SDK nebo novější verzí v části [allowPrerelease](#allowprerelease) . Pro počítače, které nikdy nemají nainstalovanou sadu .NET Core 3,0 nebo novější modul runtime nebo sadu SDK, je třeba vytvořit *global.jsv* souboru a zadat přesnou verzi, kterou chcete použít.

* Následující upozornění indikuje, že projekt cílí na EF Core 1,0 nebo 1,1, což není kompatibilní s .NET Core 2,1 SDK a novějšími verzemi:

  > Spouštěcí projekt {startupProject} cílí na rozhraní Framework. NETCoreApp verze {targetFrameworkVersion}. Tato verze nástrojů příkazového řádku Entity Framework Core .NET podporuje pouze verzi 2,0 nebo vyšší. Informace o použití starších verzí nástrojů naleznete v tématu <https://go.microsoft.com/fwlink/?linkid=871254> .

  Počínaje sadou .NET Core 2,1 SDK (verze 2.1.300) se `dotnet ef` příkaz vloží do sady SDK. Pro zkompilování projektu nainstalujte sadu .NET Core 2,0 SDK (verze 2.1.201) nebo starší na svém počítači a definujte požadovanou verzi sady SDK pomocí *global.jsv* souboru. Další informace o příkazu naleznete `dotnet ef` v tématu [EF Core nástroje příkazového řádku .NET](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Viz také

- [Jak se řeší sady SDK projektu](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
