---
title: .NET Portability Analyzeru – .NET
description: Další informace o použití nástroje .NET Portability Analyzeru vyhodnotit, jak přenosné váš kód je mezi různé implementace .NET, včetně .NET Core, .NET Standard, UPW a Xamarin.
author: blackdwarf
ms.author: mairaw
ms.date: 07/26/2017
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 515dd7a393d87811377aa5d9fb02de35943b6966
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44205754"
---
# <a name="the-net-portability-analyzer"></a>.NET Portability Analyzeru

Chcete si vytvořit multiplatformní knihovny? Chcete zobrazit, kolik práce je nutná, aby vaše aplikace kompatibilní s jinými implementace .NET a profily, včetně .NET Core, .NET Standard, UPW a Xamarin pro iOS, Android a Mac? [.NET Portability Analyzeru](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) je nástroj, který vám poskytne podrobnou zprávu o jak flexibilní program je implementace .NET díky analýze sestavení. Analyzátor přenositelnosti se nabízí jako rozšíření sady Visual Studio a konzolové aplikace.

## <a name="new-targets"></a>Nové cíle

* [.NET core](../../core/index.md): má modulárního návrhu, využívá vedle sebe a cílí na scénáře napříč platformami. Vedle sebe umožňuje přijmout nové verze .NET Core bez porušení dalších aplikací.
* [ASP.NET Core](/aspnet/core): je moderní webové – architektura založená na .NET Core, což vývojářům stejné výhody.
* [Univerzální platforma Windows](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): zvýšení výkonu aplikací Windows Store, které běží na x64 a počítačů ARM pomocí statické kompilace .NET Native. 
* .NET core a rozšíření platformy: Zahrnuje rozhraní API .NET Core kromě jiných rozhraní API v ekosystému .NET, jako je například WCF, ASP.NET Core, FSharp a Azure.
* .NET standard a rozšíření platformy: Obsahuje standardní rozhraní API .NET kromě jiných ekosystému .NET, jako je například WCF, ASP.NET Core, FSharp a Azure.

## <a name="how-to-use-portability-analyzer"></a>Jak používat Portability Analyzeru

Pokud chcete začít používat .NET Portability Analyzeru, musíte nejprve stáhnout a nainstalovat rozšíření z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). To funguje v sadě Visual Studio 2015 a Visual Studio 2017. Můžete vytvořit v sadě Visual Studio prostřednictvím **analyzovat** > **nastavení analyzátor přenositelnosti** a vyberte cílové platformy.

![Snímek obrazovky s přenositelností](./media/portability-analyzer/portability-screenshot.png)

Pokud chcete analyzovat celý projekt, klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a vyberte **analyzovat přenositelnost sestavení**. V opačném případě přejděte **analyzovat** nabídky a vybereme **analyzovat přenositelnost sestavení**. Tam pak vyberete spustitelný soubor projektu nebo knihovny DLL.

![Průzkumník řešení přenositelnosti](./media/portability-analyzer/portability-solution-explorer.png)

Po spuštění analýzy, zobrazí se sestavy přenositelnost .NET. Pouze v seznamu se zobrazí typy, které jsou nepodporuje cílovou platformu a můžete zkontrolovat doporučení ve službě **zprávy** kartu **seznam chyb**. Můžete také přejít na problémových oblastí přímo **zprávy** kartu.

![Přenositelnost sestavy](./media/portability-analyzer/portability-report.png)

Nechcete používat Visual Studio? Můžete také použít Portability Analyzeru z příkazového řádku. Stáhnout pouze [API Portability Analyzeru](https://www.microsoft.com/download/details.aspx?id=42678).

*   Zadejte následující příkaz, který analýza aktuálním adresáři: `\...\ApiPort.exe analyze -f .`
*   Pokud chcete analyzovat konkrétního seznamu souborů DLL, zadejte následující příkaz: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

Sestavy .NET Portability je uložen jako soubor aplikace Excel (*.xlsx*) v aktuálním adresáři. **Podrobnosti** karty v sešitu aplikace Excel obsahuje další informace.

Další informace o .NET Portability Analyzeru najdete [dokumentaci na Githubu](https://github.com/Microsoft/dotnet-apiport#documentation) a [A stručný podívejte se na .NET Portability Analyzeru](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) videa Channel 9.
