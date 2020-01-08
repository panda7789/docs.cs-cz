---
title: Co je nového v .NET Core 3.1
description: Přečtěte si o nových funkcích, které najdete v .NET Core 3,1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a9f47c2909375251460b45792822e491d56fb242
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342851"
---
# <a name="whats-new-in-net-core-31"></a>Co je nového v .NET Core 3.1

Tento článek popisuje, co je v .NET Core 3,1 novinkou. Tato verze obsahuje menší vylepšení .NET Core 3,0 a zaměřuje se na malé, ale důležité opravy. Nejdůležitější funkcí pro .NET Core 3,1 je, že se jedná o [dlouhodobou podporu (LTS)](#long-term-support) .

Pokud používáte Visual Studio 2019, musíte aktualizovat na [Visual studio 2019 verze 16,4](https://visualstudio.microsoft.com/downloads/) pro práci s projekty .net Core 3,1. Další informace o tom, co je nového v aplikaci Visual Studio, naleznete v [blogu sady Visual Studio](https://devblogs.microsoft.com/visualstudio/tis-the-season-visual-studio-2019/).

Visual Studio pro Mac také podporuje a zahrnuje .NET Core 3,1 v kanálu Visual Studio pro Mac 8,4 Preview. Aby bylo možné používat .NET Core 3,1, musíte se přihlásit k kanálu verze Preview.

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

## <a name="windows-forms"></a>Windows Forms

*Pouze Windows*

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

*Pouze Windows*

Přidala se podpora pro vytváření C++projektů/CLI (označovaných také jako C++"spravované"). Binární soubory vytvořené z těchto projektů jsou kompatibilní s .NET Core 3,0 a novějšími verzemi.

Pokud chcete přidat podporu C++pro/CLI v aplikaci Visual Studio 2019 16,4, nainstalujte [desktopový C++ vývoj s](https://docs.microsoft.com/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)využitím úlohy. Tato úloha přidá dvě šablony do sady Visual Studio:

- Knihovna tříd CLR (.NET Core)
- Prázdný projekt CLR (.NET Core)

## <a name="next-steps"></a>Další kroky

- [Přečtěte si o nejnovějších změnách mezi .NET Core 3,0 a 3,1.](../compatibility/3.0-3.1.md)
- [Přečtěte si o nejnovějších změnách mezi .NET Framework a .NET Core 3,0 pro aplikace model Windows Forms.](../porting/winforms-breaking-changes.md)
