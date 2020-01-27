---
title: Seskupení ovládacích prvků pomocí ovládacího prvku panel pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 927aeb5b51bc1ac4e22a45e487b49424b4e67b71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745651"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře
Ovládací prvky <xref:System.Windows.Forms.Panel> model Windows Forms slouží k seskupení dalších ovládacích prvků. Existují tři důvody pro seskupení ovládacích prvků. Jedním z nich je vizuální seskupení souvisejících prvků formuláře pro jasné uživatelské rozhraní; Další je programové seskupení přepínačů, například. Poslední je pro přesunutí ovládacích prvků jako jednotky v době návrhu.

## <a name="to-create-a-group-of-controls"></a>Vytvoření skupiny ovládacích prvků

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Panel> z karty **model Windows Forms** panelu nástrojů na formulář.

2. Do panelu přidejte další ovládací prvky, nakreslením každé dovnitř panelu.

     Pokud máte ovládací prvky, které chcete uzavřít na panelu, můžete vybrat všechny ovládací prvky, vyjmout je do schránky, vybrat ovládací prvek <xref:System.Windows.Forms.Panel> a pak je vložit do panelu. Můžete je také přetáhnout na panel.

3. Volitelné Chcete-li přidat ohraničení panelu, nastavte jeho vlastnost <xref:System.Windows.Forms.BorderStyle>. Existují tři možnosti: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>a <xref:System.Windows.Forms.BorderStyle.None>.

## <a name="see-also"></a>Viz také:

- [Ovládací prvek Panel](panel-control-windows-forms.md)
- [Přehled ovládacího prvku Panel](panel-control-overview-windows-forms.md)
- [Postupy: Nastavení pozadí panelu](how-to-set-the-background-of-a-windows-forms-panel.md)
