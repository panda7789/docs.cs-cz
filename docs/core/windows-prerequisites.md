---
title: Předpoklady pro .NET Core ve Windows
description: Zjistěte, jaké závislosti potřebujete na počítači s Windows pro vývoj a spouštění aplikací .NET Core.
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: 6885f6c853efb0dcb2cb64b83f07e12b1dc2e3cf
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771958"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Předpoklady pro .NET Core ve Windows

Tento článek ukazuje podporované verze operačního systému, aby bylo možné spouštět aplikace .NET Core ve Windows. Podporované verze operačního systému a závislosti, které následují, se vztahují na tři způsoby vývoje aplikací .NET Core v systému Windows:

* [Příkazový řádek](./tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [Visual Studio Code](https://code.visualstudio.com/)

Pokud vyvíjíte v systému Windows pomocí sady Visual Studio, [požadavky pro vývoj aplikací .NET Core pomocí sady Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) jsou podrobněji popsány v článku o minimálních verzích podporovaných pro vývoj pro .NET Core.

## <a name="net-core-supported-operating-systems"></a>Podporované operační systémy .NET Core

Následující články obsahují úplný seznam podporovaných operačních systémů .NET Core na verzi:

* [.NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)

Odkazy ke stažení a další informace najdete v tématu stažení z [rozhraní .NET](https://dotnet.microsoft.com/download) pro stažení nejnovější verze nebo [archivu ke stažení](https://dotnet.microsoft.com/download/archives#dotnet-core) pro starší verze.

## <a name="net-core-dependencies"></a>Závislosti .NET Core

[Distribuovatelné C++ součásti Microsoft Visual 2015 Update 3](https://www.microsoft.com/download/details.aspx?id=52685) je třeba nainstalovat ručně v těchto případech:

* Instalace .NET Core pomocí [skriptu instalačního programu](./tools/dotnet-install-script.md).
* Nasazení samostatně obsažené aplikace .NET Core.
* Sestavuje se produkt ze zdroje.
* Instalace .NET Core přes soubor *. zip* . To může zahrnovat servery sestavení/CI/CD.

> [!NOTE]
> **Pro Windows 8.1 a starší verze nebo Windows Server 2012 R2 a starší verze:**
>
> Ujistěte se, že je instalace Windows aktuální a zahrnuje [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), která se dá nainstalovat prostřednictvím web Windows Update. Pokud tuto aktualizaci nemáte nainstalovanou, při spuštění aplikace .NET Core se zobrazí chybová zpráva podobná následující: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Pro Windows 7 nebo Windows Server 2008 R2:**
>
> Kromě KB2999226 se ujistěte, že máte nainstalovanou také [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) . Pokud tuto aktualizaci nemáte nainstalovanou, při spuštění aplikace .NET Core se zobrazí chybová zpráva podobná následující: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a>Předpoklady pro vývoj aplikací .NET Core pomocí sady Visual Studio

I když můžete použít libovolný editor pro vývoj aplikací .NET Core pomocí .NET Core SDK, Visual Studio 2017 a novější verze poskytují integrované vývojové prostředí pro aplikace .NET Core ve Windows.

<a name="vs-mapping"></a>

Pro každou verzi .NET Core je vyžadována minimální verze sady Visual Studio. Ověření verze sady Visual Studio:

* V nabídce **help (nápovědu** ) vyberte **informace o Microsoft Visual Studio**.
* V dialogovém okně **o Microsoft Visual Studio** ověřte číslo verze.

Následující tabulka uvádí minimální verzi pro jednotlivé sady SDK:

| Verze .NET Core SDK | Verze sady Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.0                   | Visual Studio 2019 verze 16,3 nebo vyšší. |
| 2,2                   | Visual Studio 2017 verze 15,9 nebo vyšší. |
| 2,1                   | Visual Studio 2017 verze 15,7 nebo vyšší. |
| verze                   | Visual Studio 2017 verze 15,0 nebo vyšší. |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Vývoj aplikací .NET Core v sadě Visual Studio 2019 pomocí sady .NET Core 3,0 SDK:

* [Stáhněte a nainstalujte sadu Visual Studio 2019 verze 16,3 nebo vyšší](/visualstudio/install/install-visual-studio) a vyberte jednu z následujících úloh, které zahrnují .NET Core SDK v závislosti na druhu aplikace, kterou sestavujete:

  * Úloha **vývoje .NET Core pro více platforem** v části **Další sady nástrojů** .
  * Úlohy **vývoje ASP.NET a webu** v části **web & Cloud** .
  * Pracovní proces **vývoje pro NET Desktop** v části **Windows** .

Na následujícím obrázku vidíte úlohy **vývoje .NET Core pro různé platformy** vybrané v uživatelském rozhraní sady Visual Studio:

![Snímek obrazovky s instalací sady Visual Studio 2019 se zvolenou úlohou "vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-2019-workloads.jpg)

Sada Visual Studio 2019 verze 16,3 po instalaci kterékoli z těchto úloh používá standardně sadu .NET Core 3,0 SDK.

Pokud chcete, aby existující projekty používaly nejnovější modul runtime .NET Core, proveďte cílení každého existujícího projektu .NET Core na .NET Core 3,0 pomocí následujících pokynů:

* V nabídce **projekt** klikněte na příkaz **vlastnosti**.
* V nabídce Výběr **cílového rozhraní** nastavte hodnotu na **.NET Core 3,0**.

![Snímek vlastnosti projektu aplikace sady Visual Studio 2019 s vybranou položkou nabídky cílové rozhraní .NET Core 3,0](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

Jakmile máte sadu Visual Studio nakonfigurovanou pomocí sady .NET Core 3,0 SDK, můžete provést následující akce:

* Otevřete, sestavte a spusťte existující projekty .NET Core 1. x a 2. x.
* Proveďte změny cílení na projekty .NET Core 1. x a 2. x na .NET Core 3,0, sestavte a spusťte.
* Vytvořte nové projekty .NET Core 3,0.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2. x](#tab/netcore2x)

Vývoj aplikací .NET Core v sadě Visual Studio 2017 pomocí sady .NET Core 2,2 SDK:

* [Stáhněte a nainstalujte sadu Visual Studio 2019 verze 16,3 nebo vyšší](/visualstudio/install/install-visual-studio) pomocí úlohy **vývoje .NET Core pro různé platformy** (v části **jiné sady nástrojů** ).
* [Stáhněte a nainstalujte si sadu Visual Studio 2017 verze 15.9.0 nebo novější](/visualstudio/install/install-visual-studio) pomocí úlohy **vývoje .NET Core pro různé platformy** (v části **jiné sady nástrojů** ).

![Snímek obrazovky s instalací sady Visual Studio 2017 se zvolenou úlohou "vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-2017-workloads.jpg)

Po instalaci sady nástrojů pro **vývoj pro různé platformy .NET Core** se v sadě Visual Studio obvykle nainstaluje předchozí verze .NET Core SDK.
Například sada Visual Studio 2017 verze 15,9 po instalaci úlohy používá .NET Core 2,1 SDK ve výchozím nastavení.

Aktualizace sady Visual Studio tak, aby používala sadu .NET Core 2,2 SDK:

 1. Nainstalujte [sadu .NET Core 2,2 SDK](https://dotnet.microsoft.com/download).

 1. Pokud chcete, aby váš projekt používal nejnovější modul runtime .NET Core, přecílíte všechny existující nebo nové projekty .NET Core na .NET Core 2,2 pomocí následujících pokynů:

    * V nabídce **projekt** klikněte na příkaz **vlastnosti**.
    * V nabídce Výběr **cílového rozhraní** nastavte hodnotu na **.NET Core 2,2**.

![Snímek vlastnosti projektu aplikace sady Visual Studio 2017 s vybranou položkou nabídky cílové rozhraní .NET Core 2,2](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Jakmile máte sadu Visual Studio nakonfigurovanou pomocí sady .NET Core 2,2 SDK, můžete provést následující akce:

* Otevřete, sestavte a spusťte existující projekty .NET Core 1. x a 2. x.
* Proveďte změny cílení na projekty .NET Core 1. x a 2. x na .NET Core 2,2, sestavte a spusťte.
* Vytvořte nové projekty .NET Core 2,2.

---
