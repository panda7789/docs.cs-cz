---
title: Publikování aplikací
description: Přečtěte si o způsobech publikování aplikace .NET Core. .NET Core můžete publikovat aplikace specifické pro platformu nebo aplikace pro různé platformy. Aplikaci můžete publikovat jako samostatnou nebo závislou na běhu. Každý režim ovlivňuje způsob, jakým uživatel spouští vaši aplikaci.
ms.date: 01/31/2020
ms.openlocfilehash: 3b9c3b7f29af12477874b7a31ef0de4750719de0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399061"
---
# <a name="net-core-application-publishing-overview"></a>Přehled publikování aplikace .NET Core

Aplikace, které vytvoříte pomocí .NET Core, lze publikovat ve dvou různých režimech a režim ovlivňuje způsob, jakým uživatel spouští vaši aplikaci.

Publikování aplikace jako *samostatné* vytvoří aplikaci, která obsahuje běh .NET Core runtime a knihovny a vaše aplikace a její závislosti. Uživatelé aplikace ji mohou spustit v počítači, ve které není nainstalován anainstalován runtime .NET Core.

Publikování aplikace jako *závislé na běhu* vytvoří aplikaci, která zahrnuje pouze samotnou aplikaci a její závislosti. Uživatelé aplikace musí samostatně nainstalovat runtime .NET Core.

Oba režimy publikování ve výchozím nastavení vytvářejí spustitelný soubor specifický pro platformu. Aplikace závislé na modulu runtime lze vytvořit bez spustitelného souboru a tyto aplikace jsou napříč platformami.

Při vytvoření spustitelného souboru můžete určit cílovou platformu s identifikátorem modulu runtime (RID). Další informace o ridech naleznete [v tématu .NET Core RID Catalog](../rid-catalog.md).

Následující tabulka popisuje příkazy používané k publikování aplikace jako závislé na běhu nebo samostatné verze sady SDK:

| Typ                                                                                 | SDK 2.1 | Sada SDK 3.x | Příkaz |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [spustitelný soubor závislý na](#publish-runtime-dependent) aktuální platformě. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [spustitelný soubor závislý na](#publish-runtime-dependent) konkrétním platformě.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [binární binární soubor závislý na runtime na více platformách](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [samostatný spustitelný soubor](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

Další informace naleznete v tématu [příkaz publikování dotnet .NET Core](../tools/dotnet-publish.md).

## <a name="produce-an-executable"></a>Vytvoření spustitelného souboru

Spustitelné soubory nejsou napříč platformami. Jsou specifické pro operační systém a architekturu procesoru. Při publikování aplikace a vytváření spustitelného souboru můžete aplikaci publikovat jako [samostatnou aplikaci](#publish-self-contained) nebo [závislou na modulu runtime](#publish-runtime-dependent). Publikování aplikace jako samostatné zahrnuje .NET Core runtime s aplikací a uživatelé aplikace se nemusí starat o instalaci .NET Core před spuštěním aplikace. Aplikace publikované jako závislé na běhu nezahrnují zaběhu .NET Core a knihovny. zahrnuty jsou pouze závislosti aplikace a třetích stran.

Následující příkazy vytvářejí spustitelný soubor:

| Typ                                                                                 | SDK 2.1 | Sada SDK 3.x | Příkaz |
| ------------------------------------------------------------------------------------ | ------- | ------- | ------- |
| [spustitelný soubor závislý na](#publish-runtime-dependent) aktuální platformě. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [spustitelný soubor závislý na](#publish-runtime-dependent) konkrétním platformě.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [samostatný spustitelný soubor](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>Vytvoření binárního souboru pro různé platformy

Binární soubory mezi platformami se vytvářejí při publikování aplikace jako [závislé na běhu](#publish-runtime-dependent)ve formě souboru *dll.* Soubor *dll* je pojmenován po projektu. Pokud například máte aplikaci s názvem **word_reader**, vytvoří se soubor s názvem *word_reader.dll.* Aplikace publikované tímto způsobem `dotnet <filename.dll>` jsou spouštěny pomocí příkazu a lze je spouštět na libovolné platformě.

Binární soubory mezi platformami lze spustit v libovolném operačním systému, pokud je již nainstalován cílový runtime .NET Core. Pokud není nainstalován cílový runtime jádra .NET, aplikace může běžet pomocí novějšího běhu, pokud je aplikace nakonfigurovaná pro přechod vpřed. Další informace naleznete v tématu [aplikace závislé na běhu posunout vpřed](../versions/selection.md#framework-dependent-apps-roll-forward).

Následující příkaz vytvoří binární soubor pro více platforem:

| Typ                                                                                 | SDK 2.1 | Sada SDK 3.x | Příkaz |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [binární binární soubor závislý na runtime na více platformách](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-runtime-dependent"></a>Publikovat závislé na běhu

Aplikace publikované jako závislé na běhu jsou napříč platformami a nezahrnují zaběhový čas .NET Core. Uživatel vaší aplikace je povinen nainstalovat runtime .NET Core.

Publikování aplikace jako závislé na modulu runtime vytvoří [binární soubor pro více platforem](#produce-a-cross-platform-binary) jako soubor *dll* a [spustitelný soubor specifický pro platformu,](#produce-an-executable) který cílí na vaši aktuální platformu. *DLL* je multiplatformní, zatímco spustitelný soubor není. Pokud například publikujete aplikaci s názvem **word_reader** a cílový systém Windows, vytvoří se spolu s *souborem word_reader.dll*spustitelný soubor *word_reader.exe* . Při cílení na Linux nebo macOS se vytvoří *word_reader* spustitelný soubor spolu s *word_reader.dll*. Další informace o ridech naleznete [v tématu .NET Core RID Catalog](../rid-catalog.md).

> [!IMPORTANT]
> Sada .NET Core SDK 2.1 nevytváří spustitelné soubory specifické pro platformu při publikování závislé na běhu aplikace.

Binární soubor mezi platformami vaší aplikace `dotnet <filename.dll>` lze spustit pomocí příkazu a lze jej spustit na libovolné platformě. Pokud aplikace používá balíček NuGet, který má implementace specifické pro platformu, všechny závislosti platforem se zkopírují do složky publikování spolu s aplikací.

Spustitelný soubor pro konkrétní platformu můžete `-r <RID> --self-contained false` vytvořit předáním parametrů příkazu. [`dotnet publish`](../tools/dotnet-publish.md) Pokud `-r` je parametr vynechán, vytvoří se spustitelný soubor pro aktuální platformu. Všechny balíčky NuGet, které mají závislosti specifické pro platformu pro cílovou platformu jsou zkopírovány do složky publikování.

### <a name="advantages"></a>Výhody

- **Malé nasazení**\
Distribuují se pouze vaše aplikace a její závislosti. Runtime .NET Core a knihovny jsou nainstalovány uživatelem a všechny aplikace sdílejí runtime.

- **Napříč platformami**\
Vaše aplikace a všechny . Knihovna net založená na jiných operačních systémech. Pro vaši aplikaci nemusíte definovat cílovou platformu. Informace o formátu souboru .NET naleznete v tématu [.NET Assembly File Format](../../standard/assembly/file-format.md).

- **Používá nejnovější opravený runtime**\
Aplikace používá nejnovější runtime (v rámci cílové minor-minor rodiny .NET Core) nainstalované v cílovém systému. To znamená, že vaše aplikace automaticky používá nejnovější opravenou verzi runtime .NET Core. Toto výchozí chování může být přepsáno. Další informace naleznete v tématu [aplikace závislé na běhu posunout vpřed](../versions/selection.md#framework-dependent-apps-roll-forward).

### <a name="disadvantages"></a>Nevýhody

- **Vyžaduje předinstalaci runtime**\
Vaše aplikace může běžet pouze v případě, že verze .NET Core vaše cíle aplikace je již nainstalován v hostitelském systému. Můžete nakonfigurovat chování pro převrácení aplikace tak, aby vyžadovalo určitou verzi rozhraní .NET Core nebo povolilo novější verzi rozhraní .NET Core. Další informace naleznete v tématu [aplikace závislé na běhu posunout vpřed](../versions/selection.md#framework-dependent-apps-roll-forward).

- **Jádro .NET se může změnit.**\
Je možné, že běh .NET Core a knihovny aktualizovat v počítači, kde je spuštěna aplikace. Ve výjimečných případech to může změnit chování vaší aplikace, pokud používáte knihovny .NET Core, což většina aplikací. Můžete nakonfigurovat, jak vaše aplikace používá novější verze .NET Core. Další informace naleznete v tématu [aplikace závislé na běhu posunout vpřed](../versions/selection.md#framework-dependent-apps-roll-forward).

Následující nevýhoda platí pouze pro .NET Core 2.1 SDK.

- **Spuštění `dotnet` aplikace pomocí příkazu**\
Uživatelé musí `dotnet <filename.dll>` spustit příkaz pro spuštění aplikace. Sada .NET Core 2.1 SDK nevytváří spustitelné soubory specifické pro platformu pro aplikace publikované v závislosti na modulu runtime.

### <a name="examples"></a>Příklady

Publikujte aplikaci závislou na běhu na příčce platformy. Spolu se souborem *dll* je vytvořen spustitelný soubor, který cílí na aktuální platformu.

```dotnet
dotnet publish
```

Publikujte aplikaci závislou na běhu na příčce platformy. 64bitový spustitelný soubor systému Linux je vytvořen spolu se souborem *dll.* Tento příkaz nefunguje s .NET Core SDK 2.1.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>Publikovat samostatné

Publikování aplikace jako samostatné vytvoří spustitelný soubor specifický pro platformu. Výstupní složka publikování obsahuje všechny součásti aplikace, včetně knihoven .NET Core a cílového běhu runtime. Aplikace je izolovaná od jiných aplikací .NET Core a nepoužívá místně nainstalovaný sdílený runtime. Uživatel aplikace není nutné stáhnout a nainstalovat .NET Core.

Spustitelný binární soubor je vytvořen pro zadanou cílovou platformu. Pokud například máte aplikaci s názvem **word_reader**a publikujete samostatný spustitelný soubor pro Systém Windows, vytvoří se soubor *word_reader.exe.* Publikování pro Linux nebo macOS, *word_reader* soubor je vytvořen. Cílová platforma a architektura je [`dotnet publish`](../tools/dotnet-publish.md) zadána s parametrem `-r <RID>` pro příkaz. Další informace o ridech naleznete [v tématu .NET Core RID Catalog](../rid-catalog.md).

Pokud aplikace má závislosti specifické pro platformu, jako je například balíček NuGet obsahující závislosti specifické pro platformu, tyto jsou zkopírovány do složky publikování spolu s aplikací.

### <a name="advantages"></a>Výhody

- **Řízení verze jádra rozhraní .NET**\
Můžete určit, která verze rozhraní .NET Core se nasadí s vaší aplikací.

- **Cílení specifické pro platformu**\
Vzhledem k tomu, že aplikaci musíte publikovat pro každou platformu, víte, kde bude aplikace spuštěna. Pokud rozhraní .NET Core zavádí novou platformu, uživatelé nemohou spustit vaši aplikaci na této platformě, dokud neuvolníte verzi zaměřenou na tuto platformu. Před spuštěním aplikace na nové platformě můžete aplikaci otestovat na problémy s kompatibilitou.

### <a name="disadvantages"></a>Nevýhody

- **Větší nasazení**\
Vzhledem k tomu, že vaše aplikace obsahuje runtime .NET Core a všechny vaše závislosti aplikací, velikost stahování a požadované místo na pevném disku je větší než verze [závislá na běhu.](#publish-runtime-dependent)

  > [!TIP]
  > Velikost nasazení v systémech Linux můžete zmenšit přibližně o 28 MB pomocí [*invariantního režimu*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).NET Core . To vynutí, aby vaše aplikace zacházet se všemi jazyky jako [invariantní jazykovou verzi](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).

- **Je těžší aktualizovat verzi jádra rozhraní .NET**\
.NET Core Runtime (distribuované s vaší aplikací) lze upgradovat pouze uvolněním nové verze aplikace. Jste zodpovědní za poskytování aktualizovanou verzi aplikace pro opravy zabezpečení do rozhraní .NET Core Runtime.

### <a name="examples"></a>Příklady

Publikujte aplikaci samostatnou. Vytvoří se 64bitový spustitelný soubor macOS.

```dotnet
dotnet publish -r osx-x64
```

Publikujte aplikaci samostatnou. Vytvoří se 64bitový spustitelný soubor systému Windows.

```dotnet
dotnet publish -r win-x64
```

## <a name="see-also"></a>Viz také

- [Nasazení základních aplikací .NET pomocí rozhraní CLI jádra rozhraní .NET.](deploy-with-cli.md)
- [Nasazení základních aplikací .NET pomocí sady Visual Studio.](deploy-with-vs.md)
- [Balíčky, metabalíčky a rámce.](../packages.md)
- [Katalog RID (.NET Core Runtime Runtime).](../rid-catalog.md)
- [Vyberte verzi .NET Core, kterou chcete použít.](../versions/selection.md)
