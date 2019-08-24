---
title: 'Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 34c14c0afd9632b06947fd72e46ddbda070cfb0f
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015767"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>Návod: Provádění běžných úloh pomocí inteligentních značek

Když vytváříte formuláře a ovládací prvky pro vaši model Windows Forms aplikaci, budete opakovaně provádět spoustu úloh. Toto jsou některé běžně prováděné úkoly, které se vám budou nacházet:

- Přidání nebo odebrání karty na <xref:System.Windows.Forms.TabControl>.

- Ukotvení ovládacího prvku k nadřazenému objektu.

- Změna orientace <xref:System.Windows.Forms.SplitContainer> ovládacího prvku.

K urychlení vývoje nabízí mnoho ovládacích prvků inteligentní značky, které jsou kontextové nabídky, které umožňují provádět běžné úkoly, jako jsou v jednom gestu v době návrhu. Tyto úlohy se nazývají *operace inteligentních značek*.

Inteligentní značky zůstávají připojeny k instanci ovládacího prvku pro svou životnost v návrháři a jsou vždy k dispozici.

## <a name="create-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu a nastavení formuláře.

1. V aplikaci Visual Studio vytvořte projekt aplikace založený na systému Windows s názvem **SmartTagsExample**.

2. Vyberte formulář v **Návrhář formulářů**.

## <a name="use-smart-tags"></a>Použití inteligentních značek

Inteligentní značky jsou vždy k dispozici v době návrhu u ovládacích prvků, které je nabízejí.

1. Přetáhněte z panelu nástrojů do formuláře. <xref:System.Windows.Forms.TabControl> Poznamenejte si glyf inteligentních značek![(glyf](./media/vs-winformsmttagglyph.gif)inteligentních značek), který se zobrazí <xref:System.Windows.Forms.TabControl>na straně.

2. Klikněte na glyf inteligentních značek. V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **Přidat kartu** . Všimněte si, že je do okna <xref:System.Windows.Forms.TabControl>přidána nová stránka karty.

3. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TableLayoutPanel>

4. Klikněte na glyf inteligentních značek. V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **Přidat sloupec** . Všimněte si, že je do <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku přidán nový sloupec.

5. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.SplitContainer>

6. Klikněte na glyf inteligentních značek. V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **orientace vodorovné příčky** . Všimněte si <xref:System.Windows.Forms.SplitContainer> , že příčka ovládacího prvku je nyní orientována vodorovně.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
