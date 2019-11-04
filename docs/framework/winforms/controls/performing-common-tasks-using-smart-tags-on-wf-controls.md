---
title: 'Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07fb43a711ae8b1e2e375b17b136c07f35b1cf39
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459571"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>Návod: provádění běžných úloh pomocí inteligentních značek

Když vytváříte formuláře a ovládací prvky pro vaši model Windows Forms aplikaci, budete opakovaně provádět spoustu úloh. Toto jsou některé běžně prováděné úkoly, které se vám budou nacházet:

- Přidání nebo odebrání karty na <xref:System.Windows.Forms.TabControl>.

- Ukotvení ovládacího prvku k nadřazenému objektu.

- Změna orientace ovládacího prvku <xref:System.Windows.Forms.SplitContainer>.

K urychlení vývoje nabízí mnoho ovládacích prvků inteligentní značky, které jsou kontextové nabídky, které umožňují provádět běžné úkoly, jako jsou v jednom gestu v době návrhu. Tyto úlohy se nazývají *operace inteligentních značek*.

Inteligentní značky zůstávají připojeny k instanci ovládacího prvku pro svou životnost v návrháři a jsou vždy k dispozici.

## <a name="create-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu a nastavení formuláře.

1. V aplikaci Visual Studio vytvořte projekt aplikace založený na systému Windows s názvem **SmartTagsExample**.

2. Vyberte formulář v **Návrhář formulářů**.

## <a name="use-smart-tags"></a>Použití inteligentních značek

Inteligentní značky jsou vždy k dispozici v době návrhu u ovládacích prvků, které je nabízejí.

1. Přetáhněte <xref:System.Windows.Forms.TabControl> ze **sady nástrojů** do formuláře. Poznamenejte si glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif)), který se zobrazí na straně <xref:System.Windows.Forms.TabControl>.

2. Klikněte na glyf inteligentních značek. V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **Přidat kartu** . Všimněte si, že se do <xref:System.Windows.Forms.TabControl>přidá nová stránka karty.

3. Přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> z **panelu nástrojů** do formuláře.

4. Klikněte na glyf inteligentních značek. V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **Přidat sloupec** . Všimněte si, že je do ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> přidán nový sloupec.

5. Přetáhněte ovládací prvek <xref:System.Windows.Forms.SplitContainer> z **panelu nástrojů** do formuláře.

6. Klikněte na glyf inteligentních značek. V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **orientace vodorovné příčky** . Všimněte si, že příčka ovládacího prvku <xref:System.Windows.Forms.SplitContainer> je nyní orientována vodorovně.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
