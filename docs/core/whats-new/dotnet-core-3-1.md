---
title: Co je nového v .NET Core 3.1
description: Další informace o nových funkcích v rozhraní .NET Core 3.1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 323a2390f079c17b81db01e4e3787916251943bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156553"
---
# <a name="whats-new-in-net-core-31"></a>Co je nového v .NET Core 3.1

Tento článek popisuje, co je nového v rozhraní .NET Core 3.1. Tato verze obsahuje menší vylepšení .NET Core 3.0, se zaměřením na malé, ale důležité opravy. Nejdůležitější funkcí o .NET Core 3.1 je, že se jedná o [vydání dlouhodobé podpory (LTS).](#long-term-support)

Pokud používáte Visual Studio 2019, musíte aktualizovat na [Visual Studio 2019 verze 16.4](https://visualstudio.microsoft.com/downloads/) pro práci s projekty .NET Core 3.1. Další informace o tom, co je nového v Sadě Visual Studio, najdete [v tématu Co je nového ve Visual Studiu 2019 verze 16.4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).

Visual Studio pro Mac také podporuje a obsahuje .NET Core 3.1 v Visual Studiu pro Mac 8.4.

Další informace o vydání naleznete v [oznámení .NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

- [Stáhněte si a s rozhraním .NET Core 3.1 můžete začít](https://dotnet.microsoft.com/download/dotnet-core/3.1) ve Windows, macOS nebo Linuxu.

## <a name="long-term-support"></a>Dlouhodobá podpora

.NET Core 3.1 je verze LTS s podporou společnosti Microsoft pro příští tři roky. Důrazně doporučujeme přesunout aplikace do .NET Core 3.1. Aktuální životní cyklus ostatních hlavních verzí je následující:

| Vydat | Poznámka |
| ------- | ---- |
| .NET Core 3.0 | Konec životnosti 3. března 2020.     |
| .NET Core 2.2 | Konec životnosti dne 23.12.2019. |
| .NET Core 2.1 | Konec životnosti 21. srpna 2021.    |

Další informace naleznete v [zásadách podpory jádra .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="macos-apphost-and-notarization"></a>aplikace macOSHost a notářská izace

*pouze macOS*

Počínaje notářsky oznamovaným rozhraním .NET Core SDK 3.1 pro macOS je nastavení appHost ve výchozím nastavení zakázáno. Další informace najdete v [tématu macOS Catalina Notarization a dopad na stahování a projekty .NET Core](../install/macos-notarization-issues.md).

Když je povoleno nastavení appHost, .NET Core generuje nativní Mach-O spustitelný soubor při vytváření nebo publikování. Vaše aplikace běží v kontextu appHost při spuštění ze `dotnet run` zdrojového kódu pomocí příkazu nebo spuštěním spustitelného souboru Mach-O přímo.

Bez appHost, jediný způsob, jak uživatel může spustit aplikaci `dotnet <filename.dll>` [závislou na běhu](../deploying/index.md#publish-runtime-dependent) je pomocí příkazu. AppHost se vždy vytvoří, když publikujete aplikaci [samostatnou](../deploying/index.md#publish-self-contained).

Můžete buď nakonfigurovat appHost na úrovni projektu, nebo přepnout `dotnet` appHost `-p:UseAppHost` pro konkrétní příkaz s parametrem:

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

Další informace o `UseAppHost` nastavení naleznete v [tématu Vlastnosti MSBuild pro sadu Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

## <a name="windows-forms"></a>Windows Forms

*Jen ve Windows*

> [!WARNING]
> Ve Formulářích Windows dojde k průlomové změny.

Starší ovládací prvky byly zahrnuty ve formulářích systému Windows, které byly po určitou dobu v panelu nástrojů aplikace Visual Studio Designer nedostupné. Tyto byly nahrazeny nové ovládací prvky zpět v rozhraní .NET Framework 2.0. Tyto byly odebrány z sady Desktop SDK pro rozhraní .NET Core 3.1.

| Odebraný ovládací prvek | Doporučená výměna | Přidružená api byla odebrána. |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | Datagridcell<br/>Datagridrow<br/>Sběr datagridtable<br/>Datagridcolumncollection<br/>Datagridtablestyle<br/>Datagridcolumnstyle<br/>Styl DataGridLine<br/>Popisek DataGridParentRowsLabel<br/>DataGridParentRowsLabelStyleStyle<br/>Datagridboolcolumn<br/>Datagridtextbox<br/>Gridcolumnstylescollection<br/>Gridtablestylescollection<br/>Typ přístupového typu |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | Vzhled panelu nástrojů |
| Toolbarbutton   | <xref:System.Windows.Forms.ToolStripButton>   | ToolBarButtonClickEventArgs<br/>Obslužné volání toolBarButtonClickEvent<br/>ToolBarButtonStyle<br/>Zarovnání panelu nástrojů |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | Kolekce položek MenuCollection |
| Mainmenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

Doporučujeme aktualizovat aplikace na .NET Core 3.1 a přejít na náhradní ovládací prvky. Nahrazení ovládacích prvků je jednoduchý proces, v podstatě "najít a nahradit" na typu.

## <a name="ccli"></a>C++/CLI

*Jen ve Windows*

Byla přidána podpora pro vytváření projektů C++/CLI (označované také jako "spravované C++". Binární soubory vytvořené z těchto projektů jsou kompatibilní s rozhraním .NET Core 3.0 a novějšími verzemi.

Chcete-li přidat podporu pro C++/CLI ve Visual Studiu 2019 verze 16.4, nainstalujte [vývoj plochy s úlohami C++](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads). Tato úloha přidá do sady Visual Studio dvě šablony:

- Knihovna tříd CLR (jádro.NET)
- Prázdný projekt CLR (jádro.NET)

## <a name="next-steps"></a>Další kroky

- [Zkontrolujte nejnovější změny mezi .NET Core 3.0 a 3.1.](../compatibility/3.0-3.1.md)
- [Projděte si nejnovější změny v rozhraní .NET Core 3.1 pro aplikace pro Windows Forms.](../compatibility/winforms.md#net-core-31)
