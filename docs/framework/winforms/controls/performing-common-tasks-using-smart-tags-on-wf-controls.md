---
title: 'Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 1cc854d735ba88a301d6e2f6a83fe5c8bf881380
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211420"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms

Jak vytvořit formuláře a ovládací prvky pro aplikace Windows Forms, existují mnoho úloh, které budete opakovaně provádět. Toto jsou některé běžně prováděné úlohy, které se zobrazí:

- Přidání nebo odebrání kartu na <xref:System.Windows.Forms.TabControl>.

- Ukotvení ovládacího prvku k nadřazené úloze.

- Změna orientace <xref:System.Windows.Forms.SplitContainer> ovládacího prvku.

Mnoho ovládacích prvků pro rychlejší vývoj, nabízí inteligentní značky, které jsou kontextové nabídky, které umožňují provádět běžné úkoly, jako jsou tyto jedním gestem v době návrhu. Tyto úlohy se nazývají *smart-tag příkazy*.

Inteligentní značky zůstanou připojené k instanci ovládacího prvku po dobu jeho platnosti v návrháři a jsou vždy k dispozici.

Úlohy v tomto návodu zahrnují:

- Vytvoření projektu Windows Forms

- Pomocí inteligentních značek

- Povolení a zakázání inteligentní značky

Až budete hotovi, budete mít znalosti o úloze, kterou tyto funkce důležité rozložení.

## <a name="create-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu a nastavení formuláře.

1. V sadě Visual Studio vytvořte projekt aplikace pro systém Windows s názvem "SmartTagsExample" (**souboru** > **nový** > **projektu**  >  **Visual C#**  nebo **jazyka Visual Basic** > **klasický desktopový** > **Windows Forms Aplikace**).

2. Vyberte formulář v nástrojích pro **Návrháře formulářů Windows**.

## <a name="use-smart-tags"></a>Použití inteligentních značek

Inteligentní značky jsou vždy k dispozici na ovládací prvky, které nabízejí je v době návrhu.

1. Přetáhněte <xref:System.Windows.Forms.TabControl> z **nástrojů** do formuláře. Všimněte si smart piktogram (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), který se zobrazí na straně aplikace <xref:System.Windows.Forms.TabControl>.

2. Klikněte na tlačítko smart piktogram. V místní nabídce, která se zobrazí vedle šifra, vyberte **přidat kartu** položky. Podívejte se, že je do nové stránky karty <xref:System.Windows.Forms.TabControl>.

3. Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.

4. Klikněte na tlačítko smart piktogram. V místní nabídce, která se zobrazí vedle šifra, vyberte **přidat sloupec** položky. Podívejte se, že nový sloupec se přidá do <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.

5. Přetáhněte <xref:System.Windows.Forms.SplitContainer> ovládacího prvku **nástrojů** do formuláře.

6. Klikněte na tlačítko smart piktogram. V místní nabídce, která se zobrazí vedle šifra, vyberte **orientace vodorovné příčky** položky. Zda se zobrazila zpráva <xref:System.Windows.Forms.SplitContainer> ovládacího prvku rozdělovač je nyní orientovaný vodorovně.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- [Návod: Přidání inteligentních značek ke komponentě ve Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))
