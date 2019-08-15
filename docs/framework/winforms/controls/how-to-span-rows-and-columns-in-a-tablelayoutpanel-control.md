---
title: 'Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: a215b2b4e05bab5c81d2779d4b67d5b9d57b6ba5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039690"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel
Ovládací prvky v <xref:System.Windows.Forms.TableLayoutPanel> ovládacím prvku mohou být rozloženy sousedícími řádky a sloupci.

## <a name="to-span-columns-and-rows"></a>Postup při rozpětí sloupců a řádků

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TableLayoutPanel>

2. Přetáhněte ovládací prvek ze **sady nástrojů** na <xref:System.Windows.Forms.TableLayoutPanel> levou horní buňku ovládacího prvku. <xref:System.Windows.Forms.Button>

3. Nastavte vlastnost **jeho ColumnSpan**ovládacího prvku na hodnotu 2 <xref:System.Windows.Forms.Button> . Všimněte si, <xref:System.Windows.Forms.Button> že ovládací prvek pokrývá první a druhý sloupec.

4. Nastavte vlastnost **RowSpan**ovládacího prvku na hodnotu 2 <xref:System.Windows.Forms.Button> . Všimněte si, <xref:System.Windows.Forms.Button> že ovládací prvek pokrývá první a druhý řádek.

5. Nastavte vlastnost **jeho ColumnSpan**ovládacího prvku na hodnotu 1 <xref:System.Windows.Forms.Button> . Všimněte si, <xref:System.Windows.Forms.Button> že se ovládací prvek přesune do prvního sloupce a zasahuje do prvního a druhého řádku.

## <a name="see-also"></a>Viz také:

- [Ovládací prvek TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
