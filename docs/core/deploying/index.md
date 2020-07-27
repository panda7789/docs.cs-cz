---
title: Publikování aplikace
description: Přečtěte si o způsobech publikování aplikace .NET Core. .NET Core může publikovat aplikace pro konkrétní platformy nebo pro různé platformy. Aplikaci můžete publikovat jako samostatnou nebo jako závislou na modulu runtime. Každý režim má vliv na to, jak uživatel spouští vaši aplikaci.
ms.date: 04/01/2020
ms.openlocfilehash: 201363ad314373ec3be44eb8496f92a8e0c8e418
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164933"
---
# <a name="net-core-application-publishing-overview"></a>Přehled publikování aplikace .NET Core

Aplikace, které vytvoříte pomocí .NET Core, se dají publikovat ve dvou různých režimech a režim má vliv na to, jak uživatel aplikaci spustí.

Publikování aplikace jako *samostatné* vytvoří aplikaci, která zahrnuje modul runtime a knihovny .NET Core a vaši aplikaci a její závislosti. Uživatelé aplikace ji mohou spustit na počítači, ve kterém není nainstalován modul .NET Core Runtime.

Publikování aplikace jako *závislé na běhu* (dříve označované jako *závislé na rozhraní*) Vytvoří aplikaci, která obsahuje pouze vlastní aplikaci a její závislosti. Uživatelé aplikace musí samostatně nainstalovat modul runtime .NET Core.

Oba režimy publikování vytvoří ve výchozím nastavení spustitelný soubor specifický pro platformu. Aplikace závislé na modulu runtime lze vytvořit bez spustitelného souboru a tyto aplikace jsou pro různé platformy.

Když je vytvořen spustitelný soubor, můžete zadat cílovou platformu s identifikátorem modulu runtime (RID). Další informace o identifikátorů RID najdete v [katalogu .NET Core RID Catalog](../rid-catalog.md).

Následující tabulka popisuje příkazy, které slouží k publikování aplikace jako závislé na modulu runtime nebo samostatné, na verzi sady SDK:

| Typ                                                                                 | SDK 2.1 | Sada SDK 3. x | Příkaz |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [spustitelný soubor závislý na modulu runtime](#publish-runtime-dependent) pro aktuální platformu. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [spustitelný soubor závislý na modulu runtime](#publish-runtime-dependent) pro konkrétní platformu.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [binární soubor pro více platforem závislý na modulu runtime](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [samostatně obsažený spustitelný soubor](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

Další informace naleznete v tématu [.NET Core dotnet Publish Command](../tools/dotnet-publish.md).

## <a name="produce-an-executable"></a>Získání spustitelného souboru

Spustitelné soubory nejsou pro různé platformy. Jsou specifické pro operační systém a architekturu procesoru. Při publikování aplikace a vytvoření spustitelného souboru můžete aplikaci publikovat jako [samostatnou](#publish-self-contained) nebo [závislou na běhu](#publish-runtime-dependent). Publikování aplikace jako samostatné zahrnuje modul runtime .NET Core s aplikací a uživatelé aplikace se nemusí starat o instalaci .NET Core před spuštěním aplikace. Aplikace publikované jako nezávisle na modulu runtime nezahrnují modul runtime a knihovny .NET Core. jsou zahrnuté jenom závislosti aplikace a třetí strany.

Následující příkazy vyprodukuje spustitelný soubor:

| Typ                                                                                 | SDK 2.1 | Sada SDK 3. x | Příkaz |
| ------------------------------------------------------------------------------------ | ------- | ------- | ------- |
| [spustitelný soubor závislý na modulu runtime](#publish-runtime-dependent) pro aktuální platformu. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [spustitelný soubor závislý na modulu runtime](#publish-runtime-dependent) pro konkrétní platformu.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [samostatně obsažený spustitelný soubor](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>Vytvoření binárního souboru pro různé platformy

Binární soubory pro různé platformy se vytvářejí při publikování aplikace jako závislé na [modulu runtime](#publish-runtime-dependent)ve formě souboru *DLL* . Soubor *DLL* se jmenuje po vašem projektu. Například pokud máte aplikaci s názvem **word_reader**, vytvoří se soubor s názvem *word_reader.dll* . Aplikace publikované tímto způsobem jsou spouštěny s `dotnet <filename.dll>` příkazem a lze je spustit na libovolné platformě.

Binární soubory pro různé platformy můžou běžet v jakémkoli operačním systému, pokud je už nainstalovaný cílový modul runtime .NET Core. Pokud není cílový modul runtime .NET Core nainstalovaný, může se aplikace spustit s novějším modulem runtime, pokud je aplikace nakonfigurovaná tak, aby se předalo. Další informace najdete v tématu [posunutí aplikací závislých na modulu runtime](../versions/selection.md#framework-dependent-apps-roll-forward).

Následující příkaz vytvoří binární soubor pro různé platformy:

| Typ                                                                                 | SDK 2.1 | Sada SDK 3. x | Příkaz |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [binární soubor pro více platforem závislý na modulu runtime](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-runtime-dependent"></a>Publikování – závislé na modulu runtime

Aplikace publikované jako modul Runtime závisí na různých platformách a nezahrnují modul runtime .NET Core. K instalaci modulu runtime .NET Core je nutný uživatel vaší aplikace.

Publikování aplikace jako závislé na běhu vytvoří binární soubor pro [více platforem](#produce-a-cross-platform-binary) jako soubor *DLL* a spustitelný soubor specifický pro [platformu](#produce-an-executable) , který cílí na aktuální platformu. *Knihovna DLL* je více než platforma, zatímco spustitelný soubor není. Pokud například publikujete aplikaci s názvem **word_reader** a cílovým systémem Windows, vytvoří se *word_reader.exe* spustitelný soubor společně s *word_reader.dll*. Při cílení na Linux nebo macOS se vytvoří spustitelný soubor *word_reader* společně s *word_reader.dll*. Další informace o identifikátorů RID najdete v [katalogu .NET Core RID Catalog](../rid-catalog.md).

> [!IMPORTANT]
> .NET Core SDK 2,1 nevytváří spustitelné soubory specifické pro platformu při publikování závislého modulu runtime aplikace.

Binární soubor pro více platforem aplikace můžete spustit pomocí `dotnet <filename.dll>` příkazu a můžete ho spustit na libovolné platformě. Pokud aplikace používá balíček NuGet, který má implementace specifické pro platformu, zkopírují se všechny závislosti platforem do složky pro publikování společně s aplikací.

Pro konkrétní platformu můžete vytvořit spustitelný soubor předáním `-r <RID> --self-contained false` parametrů [`dotnet publish`](../tools/dotnet-publish.md) příkazu. Pokud `-r` je parametr vynechán, vytvoří se spustitelný soubor pro vaši aktuální platformu. Všechny balíčky NuGet, které mají závislosti specifické pro platformu pro cílovou platformu, se zkopírují do složky pro publikování.

### <a name="advantages"></a>Výhody

- **Malé nasazení**\
Distribuuje se jenom vaše aplikace a její závislosti. Modul runtime .NET Core a knihovny jsou nainstalovány uživatelem a všechny aplikace sdílejí modul runtime.

- **Pro různé platformy**\
Vaše aplikace a všechny. Knihovna založená na síti běží na jiných operačních systémech. Pro vaši aplikaci nemusíte definovat cílovou platformu. Informace o formátu souboru .NET naleznete v tématu [Formát souboru sestavení .NET](../../standard/assembly/file-format.md).

- **Používá nejnovější opravený modul runtime.**\
Aplikace používá nejnovější modul runtime (v rámci cílové hlavní řady rozhraní .NET Core) nainstalovaného v cílovém systému. To znamená, že vaše aplikace automaticky používá nejnovější opravenou verzi modulu runtime .NET Core. Toto výchozí chování lze přepsat. Další informace najdete v tématu [posunutí aplikací závislých na modulu runtime](../versions/selection.md#framework-dependent-apps-roll-forward).

### <a name="disadvantages"></a>Nevýhody

- **Vyžaduje předběžnou instalaci modulu runtime.**\
Vaše aplikace může běžet jenom v případě, že je v hostitelském systému už nainstalovaná verze .NET Core, na kterou vaše aplikace cílí. V případě, že chcete, aby aplikace vyžadovala určitou verzi rozhraní .NET Core nebo umožňovala novější verzi .NET Core, můžete nakonfigurovat chování při přeposílání. Další informace najdete v tématu [posunutí aplikací závislých na modulu runtime](../versions/selection.md#framework-dependent-apps-roll-forward).

- **Může dojít ke změně .NET Core**\
Modul runtime a knihovny .NET Core je možné aktualizovat v počítači, na kterém je aplikace spuštěná. Ve výjimečných případech to může změnit chování aplikace, pokud používáte knihovny .NET Core, které dělají většina aplikací. Můžete nakonfigurovat, jak vaše aplikace používá novější verze .NET Core. Další informace najdete v tématu [posunutí aplikací závislých na modulu runtime](../versions/selection.md#framework-dependent-apps-roll-forward).

Následující nevýhody platí jenom pro .NET Core 2,1 SDK.

- **Použití `dotnet` příkazu ke spuštění aplikace**\
Uživatelé musí spustit `dotnet <filename.dll>` příkaz pro spuštění aplikace. Sada .NET Core 2,1 SDK nevytváří spustitelné soubory specifické pro platformu pro aplikace publikované modulem runtime.

### <a name="examples"></a>Příklady

Publikování aplikace závislé na prostředí runtime pro různé platformy. Spustitelný soubor, který cílí na aktuální platformu, se vytvoří společně se souborem *DLL* .

```dotnet
dotnet publish
```

Publikování aplikace závislé na prostředí runtime pro různé platformy. Společně se souborem *DLL* je vytvořen spustitelný soubor Linux 64. Tento příkaz nefunguje s .NET Core SDK 2,1.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>Publikování samostatného kontejneru

Publikování aplikace jako samostatně obsahuje spustitelný soubor specifický pro platformu. Výstupní složka pro publikování obsahuje všechny komponenty aplikace včetně knihoven .NET Core a cílového modulu runtime. Aplikace je izolovaná od ostatních aplikací .NET Core a nepoužívá místně nainstalovaný sdílený modul runtime. Uživatel vaší aplikace není potřebný ke stažení a instalaci .NET Core.

Spustitelný soubor executable je vytvořen pro zadanou cílovou platformu. Pokud máte například aplikaci s názvem **word_reader**a publikujete samostatně uložený spustitelný soubor pro Windows, vytvoří se soubor *word_reader.exe* . Publikování pro Linux nebo macOS se vytvoří soubor *word_reader* . Cílová platforma a architektura se zadává pomocí `-r <RID>` parametru pro [`dotnet publish`](../tools/dotnet-publish.md) příkaz. Další informace o identifikátorů RID najdete v [katalogu .NET Core RID Catalog](../rid-catalog.md).

Pokud má aplikace závislosti specifické pro platformu, například balíček NuGet obsahující závislosti specifické pro danou platformu, zkopírují se do složky publikování společně s aplikací.

### <a name="advantages"></a>Výhody

- **Řízení verze .NET Core**\
Můžete řídit, která verze .NET Core se nasazuje s vaší aplikací.

- **Cílení na konkrétní platformu**\
Vzhledem k tomu, že je nutné aplikaci publikovat pro každou platformu, víte, kde bude aplikace spuštěna. Pokud .NET Core zavádí novou platformu, uživatelé nemůžou svou aplikaci na této platformě spustit, dokud neuvolníte verzi, která cílí na tuto platformu. Před spuštěním vaší aplikace na nové platformě můžete aplikaci otestovat pro problémy s kompatibilitou.

### <a name="disadvantages"></a>Nevýhody

- **Větší nasazení**\
Vzhledem k tomu, že vaše aplikace zahrnuje modul runtime .NET Core a všechny závislosti aplikací, velikost stahovaných a požadované místo na pevném disku je větší než verze [závislá na modulu runtime](#publish-runtime-dependent) .

  > [!TIP]
  > Velikost nasazení v systémech Linux můžete zmenšit přibližně o 28 MB pomocí [*režimu invariantování globalizace*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).NET Core. To vynutí, aby vaše aplikace považovala všechny kultury jako [invariantní jazykovou verzi](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).

- **Těžší aktualizace verze .NET Core**\
Modul runtime .NET Core (distribuovaný s vaší aplikací) se dá upgradovat jenom vydáním nové verze vaší aplikace. Zodpovídáte za poskytnutí aktualizované verze vaší aplikace pro opravy zabezpečení modulu runtime .NET Core.

### <a name="examples"></a>Příklady

Publikujte samostatně obsaženou aplikaci. Je vytvořen macOS 64 bitový spustitelný soubor.

```dotnet
dotnet publish -r osx-x64
```

Publikujte samostatně obsaženou aplikaci. Je vytvořen spustitelný soubor systému Windows 64.

```dotnet
dotnet publish -r win-x64
```

## <a name="see-also"></a>Viz také

- [Nasazení aplikací .NET Core pomocí .NET Core CLI.](deploy-with-cli.md)
- [Nasazení aplikací .NET Core pomocí sady Visual Studio.](deploy-with-vs.md)
- [Katalog identifikátorů runtime .NET Core (RID)](../rid-catalog.md)
- [Vyberte verzi rozhraní .NET Core, kterou chcete použít.](../versions/selection.md)
