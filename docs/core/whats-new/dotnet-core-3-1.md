---
title: Co je nového v .NET Core 3.1
description: Přečtěte si o nových funkcích, které najdete v .NET Core 3,1.
dev_langs:
- csharp
author: adegeo
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 2373b21e92c6ca68aac33684a9bd0912a2e642b3
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324272"
---
# <a name="whats-new-in-net-core-31"></a>Co je nového v .NET Core 3.1

Tento článek popisuje, co je v .NET Core 3,1 novinkou. Tato verze obsahuje menší vylepšení .NET Core 3,0 a zaměřuje se na malé, ale důležité opravy. Nejdůležitější funkcí pro .NET Core 3,1 je, že se jedná o [dlouhodobou podporu (LTS)](#long-term-support) .

Pokud používáte Visual Studio 2019, musíte aktualizovat na [Visual studio 2019 verze 16,4 nebo novější](https://visualstudio.microsoft.com/downloads/) , abyste mohli pracovat s projekty .net Core 3,1. Informace o tom, co je nového ve verzi Visual Studio verze 16,4, najdete v článku [novinky v aplikaci Visual studio 2019 verze 16,4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).

Visual Studio pro Mac také podporuje a zahrnuje .NET Core 3,1 v Visual Studio pro Mac 8,4.

Další informace o této verzi najdete v tématu [oznámení .NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

- [Stáhněte si a začněte s .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1) na Windows, MacOS nebo Linux.

## <a name="long-term-support"></a>Dlouhodobá podpora

.NET Core 3,1 je LTS verze s podporou Microsoftu pro následující tři roky. Důrazně doporučujeme přesunout své aplikace do .NET Core 3,1. Aktuální životní cyklus dalších hlavních vydání je následující:

| Vydaná verze | Poznámka |
| ------- | ---- |
| .NET Core 3.0 | Konec životnosti 3. března 2020.     |
| .NET Core 2.2 | Konec životnosti 23. prosince 2019. |
| .NET Core 2.1 | Konec životnosti 21. srpna 2021.    |

Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="macos-apphost-and-notarization"></a>macOS appHost a notarization

*jenom macOS*

Od notarized .NET Core SDK 3,1 pro macOS je nastavení appHost ve výchozím nastavení zakázané. Další informace najdete v tématu [MacOS Catalina notarization a dopad na stažení a projekty .NET Core](../install/macos-notarization-issues.md).

Když je povolené nastavení appHost, .NET Core při sestavování nebo publikování generuje nativní spustitelný soubor strojového souboru. Vaše aplikace běží v kontextu appHost při spuštění ze zdrojového kódu pomocí `dotnet run` příkazu nebo spuštěním spustitelného souboru stroj-O přímo.

Bez appHost je jediným způsobem, jak může uživatel spustit aplikaci [závislou na modulu runtime](../deploying/index.md#publish-runtime-dependent) , použití `dotnet <filename.dll>` příkazu. AppHost se vždy vytvoří při publikování [vlastní](../deploying/index.md#publish-self-contained)aplikace.

Můžete buď nakonfigurovat appHost na úrovni projektu, nebo přepnout appHost pro konkrétní `dotnet` příkaz s `-p:UseAppHost` parametrem:

- Soubor projektu

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Parametr příkazového řádku

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

Další informace o tomto `UseAppHost` nastavení najdete v tématu [vlastnosti MSBuild pro Microsoft. NET. SDK](../project-sdk/msbuild-props.md#useapphost).

## <a name="windows-forms"></a>Windows Forms

*Jen ve Windows*

> [!WARNING]
> V model Windows Forms došlo k zásadním změnám.

Starší ovládací prvky byly zahrnuty do model Windows Forms, které byly v sadě nástrojů návrháře sady Visual Studio v některých časových intervalech nedostupné. Ty se nahradily novými ovládacími prvky zpátky v .NET Framework 2,0. Ty se odebraly ze sady Desktop SDK pro .NET Core 3,1.

| Odebraný ovládací prvek | Doporučená náhrada | Odebraná přidružená rozhraní API |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | DataGridCell<br/>Hodnota DataGridRow<br/>DataGridTableCollection<br/>DataGridColumnCollection<br/>Styl DataGridTableStyle<br/>Styl DataGridColumnStyle<br/>DataGridLineStyle<br/>DataGridParentRowsLabel<br/>DataGridParentRowsLabelStyle<br/>Funkce DataGridBoolColumn<br/>DataGridTextBox<br/>Kolekce GridColumnStylesCollection<br/>GridTableStylesCollection<br/>HitTestType |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | ToolBarAppearance |
| ToolBarButton   | <xref:System.Windows.Forms.ToolStripButton>   | ToolBarButtonClickEventArgs<br/>ToolBarButtonClickEventHandler<br/>ToolBarButtonStyle<br/>ToolBarTextAlign |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | MenuItemcollection |
| MainMenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

Doporučujeme aktualizovat aplikace na .NET Core 3,1 a přejít na ovládací prvky pro nahrazení. Nahrazení ovládacích prvků je jednoduchý proces, v podstatě "najít a nahradit" na typ.

## <a name="ccli"></a>C++/CLI

*Jen ve Windows*

Přidala se podpora pro vytváření projektů C++/CLI (označovaných také jako "spravované C++"). Binární soubory vytvořené z těchto projektů jsou kompatibilní s .NET Core 3,0 a novějšími verzemi.

Pokud chcete přidat podporu pro C++/CLI v aplikaci Visual Studio 2019 verze 16,4, nainstalujte [desktopový vývoj s využitím úlohy C++](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads). Tato úloha přidá dvě šablony do sady Visual Studio:

- Knihovna tříd CLR (.NET Core)
- Prázdný projekt CLR (.NET Core)

## <a name="next-steps"></a>Další kroky

- [Přečtěte si o nejnovějších změnách mezi .NET Core 3,0 a 3,1.](../compatibility/3.0-3.1.md)
- [Přečtěte si o nejnovějších změnách v .NET Core 3,1 pro aplikace model Windows Forms.](../compatibility/winforms.md#net-core-31)
