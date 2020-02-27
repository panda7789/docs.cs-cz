---
title: Provádění běžných úloh pomocí akcí návrháře u ovládacích prvků
ms.date: 02/13/2019
helpviewer_keywords:
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 342741b9ce032b1b8ec50a6c689d9109d12f5b3b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634881"
---
# <a name="walkthrough-perform-common-tasks-using-designer-actions"></a>Návod: provádění běžných úloh pomocí akcí návrháře

Když vytváříte formuláře a ovládací prvky pro model Windows Forms aplikaci, budete opakovaně provádět mnoho úkolů. V následujícím seznamu jsou uvedeny některé běžné úkoly, které se budou provádět v rámci:

- Přidání nebo odebrání karty na <xref:System.Windows.Forms.TabControl>.
- Ukotvení ovládacího prvku k nadřazenému objektu.
- Změna orientace ovládacího prvku <xref:System.Windows.Forms.SplitContainer>.

K urychlení vývoje nabízí mnoho ovládacích prvků i akce návrháře, které jsou kontextové nabídky, které umožňují provádět běžné úkoly, jako jsou například v jednom gestu v době návrhu. Tyto úlohy se nazývají *operace návrháře akcí*.

Akce návrháře zůstávají v Návrháři připojeny k instanci ovládacího prvku a jsou vždy k dispozici.

## <a name="create-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu a nastavení formuláře.

1. V aplikaci Visual Studio vytvořte projekt aplikace založený na systému Windows s názvem **DesignerActionsExample**.

2. Vyberte formulář v **Návrhář formulářů**.

## <a name="use-designer-actions"></a>Použití akcí návrháře

Akce návrháře jsou vždy k dispozici v době návrhu u ovládacích prvků, které je nabízejí.

1. Přetáhněte <xref:System.Windows.Forms.TabControl> ze **sady nástrojů** do formuláře. Všimněte si, že glyf akcí návrháře (![malé černé šipky](./media/designer-actions-glyph.gif)), který se zobrazí na straně <xref:System.Windows.Forms.TabControl>.

2. Klikněte na piktogram akcí návrháře. V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **Přidat kartu** . Všimněte si, že se do <xref:System.Windows.Forms.TabControl>přidá nová stránka karty.

3. Přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> z **panelu nástrojů** do formuláře.

4. Klikněte na piktogram akcí návrháře. V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **Přidat sloupec** . Všimněte si, že je do ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> přidán nový sloupec.

5. Přetáhněte ovládací prvek <xref:System.Windows.Forms.SplitContainer> z **panelu nástrojů** do formuláře.

6. Klikněte na piktogram akcí návrháře. V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **orientace vodorovné příčky** . Všimněte si, že příčka ovládacího prvku <xref:System.Windows.Forms.SplitContainer> je nyní orientována vodorovně.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
