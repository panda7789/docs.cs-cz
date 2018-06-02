---
title: .NET core globální nástroje
description: Přehled o jaké jsou .NET Core globální nástroje a příkazy .NET Core rozhraní příkazového řádku pro ně k dispozici.
author: KathleenDollard
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 077ffd53f1ba2988c80a637aaa109a66139736b0
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697089"
---
# <a name="net-core-global-tools-overview"></a>Přehled .NET core globální nástroje

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

Nástroj globální .NET Core je speciální balíčku NuGet, který obsahuje aplikace konzoly. Nástroj globální může být nainstalovaný na počítači, na výchozí umístění, která je zahrnutá v proměnné prostředí PATH nebo do vlastního umístění.

Pokud chcete použít nástroj globální .NET Core:

* Najdete informace o nástroji (obvykle web nebo GitHub stránce).
* Zkontrolujte autora a statistiky na domovské stránce pro informační kanál (obvykle NuGet.org).
* Nainstalujte nástroj.
* Volání nástroj.
* Aktualizujte nástroj.
* Odinstalujte nástroj.

> [!IMPORTANT]
> .NET core globální nástroje se zobrazují v cestu a spustit v režimu plné důvěryhodnosti. .NET Core globální nástroje nainstalujte pouze v případě, že důvěřujete autorovi.

## <a name="find-a-net-core-global-tool"></a>Najít nástroj globální .NET Core

V současné době není k dispozici funkce vyhledávání globální nástroj v rozhraní .NET Core rozhraní příkazového řádku (CLI).

.NET Core globální nástroje můžete najít na [NuGet](https://www.nuget.org). Ale NuGet ještě neumožňuje prohledat speciálně pro .NET Core globální nástroje.

Také je možné nástroj doporučení v příspěvcích na blogu nebo v [natemcmaster/dotnet nástroje](https://github.com/natemcmaster/dotnet-tools) úložiště GitHub.

Můžete také najdete ve zdrojovém kódu pro globální nástroje vytvořený týmem ASP.NET na [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) úložiště GitHub.

## <a name="check-the-author-and-statistics"></a>Zkontrolujte autora a statistiky

Vzhledem k tomu, že .NET Core globální nástroje spustit v režimu plné důvěryhodnosti a jsou obvykle instaluje na cestu, mohou být velmi mocné. Nestahovat nástroje před lidmi, kterým nedůvěřujete.

Pokud tento nástroj je hostovaná na NuGet, můžete zkontrolovat jejich autorovi a statistiky tak, že nástroj.

## <a name="install-a-global-tool"></a>Nainstalujte nástroj globální

Chcete-li nainstalovat nástroj globální, je použít [instalace nástroje pro dotnet](dotnet-tool-install.md) .NET Core rozhraní příkazového řádku příkaz. Následující příklad ukazuje, jak nainstalovat nástroj globální ve výchozím umístění:

```console
dotnet tool install -g dotnetsay
```

Pokud nástroj nelze nainstalovat, zobrazí se chybové zprávy. Zkontrolujte, jsou kontrolovány informační kanály, které jste očekávali.

Pokud se pokoušíte nainstalovat předběžné verze nebo na konkrétní verzi nástroje, můžete zadat číslo verze v následujícím formátu:

```console
dotnet tool install -g <package-name> --version <version-number>
```

Pokud je instalace úspěšná, zobrazí se zpráva zobrazující příkaz používá k volání nástroj od verze nainstalované, podobně jako v následujícím příkladu:

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

Ve výchozím adresáři nebo v konkrétní umístění může být nainstalované nástroje globální. Výchozí adresáře jsou:

| OPERAČNÍ SYSTÉM          | Cesta                          |
|-------------|-------------------------------|
| Linux/systému macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Tato umístění se přidají do cesty uživatele při prvním spuštění sady SDK, takže globální nástroje nainstalované existuje můžete volat přímo.

Upozorňujeme, že globální nástroje jsou specifické pro uživatele, není ve stavu globální. Probíhá specifický pro uživatele znamená, že nemůžete nainstalovat nástroj globální, který je k dispozici pro všechny uživatele počítače. Nástroj je k dispozici pouze pro každý uživatelský profil nainstalovanou nástroj.

Globální nástroje lze také nainstalovat v konkrétní adresář. Při instalaci v konkrétního adresáře, musí se uživatel ujistit příkaz je k dispozici, včetně adresáře v cestě, voláním příkazu se adresář zadaný, nebo volání nástroj v rámci zadaného adresáře.
Rozhraní příkazového řádku .NET Core není toto umístění v tomto případě automaticky přidat do proměnné prostředí PATH.

## <a name="use-the-tool"></a>Pomocí nástroje

Po instalaci nástroje ho můžete volat pomocí jeho příkazu. Všimněte si, že příkaz nemusí být stejný jako název balíčku.

Pokud je příkaz `dotnetsay`, její volání:

```console
dotnetsay
```

Pokud nástroj Autor chtěli nástroj, který se zobrazí v kontextu `dotnet` řádku, může uživatel vytvořil ho způsobem volání jej jako `dotnet <command>`, jako například:

```console
dotnet doc
```

Zjistíte, které nástroje jsou součástí nainstalovaným balíčkem globální nástroj tak, že uvedete nainstalované balíčky pomocí [seznam nástrojů dotnet](dotnet-tool-list.md) příkaz.

Můžete také vyhledat pokyny k použití na webu nástroje nebo zadáním jednoho z následujících příkazů:

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a>Co může dojít k chybě

Globální nástroje jsou [framework závislé aplikace,](../deploying/index.md#framework-dependent-deployments-fdd), což znamená, že spoléhají na .NET Core runtime v počítači nainstalován. Pokud není nalezen očekávaný modulu runtime, se řídí normální .NET Core runtime úplné dopředné pravidla jako:

* Aplikace posunete na nejvyšší verzi opravy systému zadaná verze hlavní a podverze.
* Pokud neexistuje žádný odpovídající runtime s odpovídající hlavní a podverze číslo, použije se další vyšší podverze.
* Dopředné posunutí nedojde mezi verze preview modulu runtime nebo mezi verze preview a verze. Proto globální nástroje, které jsou vytvořené pomocí verze preview musí být znovu sestavit a publikovat autorem a přeinstalovat.
* Další problémy mohou nastat u globální nástrojů vytvořené v rozhraní .NET Core 2.1 Preview 1. Další informace najdete v tématu [.NET Core 2.1 Preview 2 – známé problémy s](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).

Pokud aplikace nemůže najít vhodné modulu runtime, se nezdaří a zobrazí chybová zpráva.

Jiný problém, který může dojít, je, že globální nástroj, který jste vytvořili během starší verze preview nemusí s vaší aktuálně nainstalované moduly runtime .NET Core. Můžete zjistit, jaké moduly runtime jsou nainstalovány na počítači, pomocí následujícího příkazu:

```console
dotnet --list-runtimes
```

Obraťte se na autora nástroj globální a zda lze znovu zkompiluje a znovu publikovat své nástroj balíček NuGet s číslem aktualizovaná verze. Jakmile budou mít aktualizovat balíček na NuGet, můžete aktualizovat svou kopii.

Rozhraní příkazového řádku .NET Core se pokusí přidat výchozí umístění do proměnné prostředí PATH na jeho první použití. Existuje však několik scénářů, kde umístění nemusí být přidat cestu automaticky, jako například:

* Pokud jste nastavili `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` proměnné prostředí.
* V systému macOS, pokud jste nainstalovali pomocí rozhraní .NET Core SDK *. tar.gz* soubory a zda není *.pkg*.
* V systému Linux musíte upravit soubor prostředí shell můžete nastavit CESTU.

## <a name="other-cli-commands"></a>Další příkazy rozhraní příkazového řádku

.NET Core SDK obsahuje jinými příkazy, které podporují .NET Core globální nástroje. Použít některou z `dotnet tool` příkazy s jedním z následujících možností:

* `--global` nebo `-g` Určuje, že příkaz se vztahuje na úrovni uživatele globální nástroje.
* `--tool-path` Určuje vlastní umístění pro globální nástroje.

Chcete-li zjistit, které příkazy, které jsou k dispozici pro globální nástroje:

```console
dotnet tool --help
```

Aktualizace nástroj globální zahrnuje odinstalace a opětovné instalace s nejnovější stabilní verze. Chcete-li aktualizovat nástroj globální, použijte [aktualizace nástrojů dotnet](dotnet-tool-update.md) příkaz:

```console
dotnet tool update -g <packagename>
```

Odeberte nástroj globální pomocí [dotnet odinstalační](dotnet-tool-uninstall.md):

```console
dotnet tool uninstall -g <packagename>
```

Zobrazit všechny nástroje globální aktuálně nainstalovaný v počítači, spolu s jejich verzi a příkazy, pomocí [seznam nástrojů dotnet](dotnet-tool-list.md) příkaz:

```console
dotnet tool list -g
```