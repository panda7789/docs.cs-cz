---
title: 'Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: cadfa715b140c63b216ec0ca2e6d6a6589ae3458
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040391"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře
Ovládací <xref:System.Windows.Forms.Panel> prvky model Windows Forms slouží k seskupení dalších ovládacích prvků. Existují tři důvody pro seskupení ovládacích prvků. Jedním z nich je vizuální seskupení souvisejících prvků formuláře pro jasné uživatelské rozhraní; Další je programové seskupení přepínačů, například. Poslední je pro přesunutí ovládacích prvků jako jednotky v době návrhu.

## <a name="to-create-a-group-of-controls"></a>Vytvoření skupiny ovládacích prvků

1. Přetáhněte ovládací prvek z karty model Windows Forms panelu nástrojů na formulář. <xref:System.Windows.Forms.Panel>

2. Do panelu přidejte další ovládací prvky, nakreslením každé dovnitř panelu.

     Pokud máte ovládací prvky, které chcete uzavřít na panelu, můžete vybrat všechny ovládací prvky, vyjmout je do schránky, vybrat <xref:System.Windows.Forms.Panel> ovládací prvek a pak je vložit do panelu. Můžete je také přetáhnout na panel.

3. Volitelné Chcete-li přidat ohraničení panelu, nastavte jeho <xref:System.Windows.Forms.BorderStyle> vlastnost. Existují tři možnosti: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle> <xref:System.Windows.Forms.BorderStyle.None>a.

## <a name="see-also"></a>Viz také:

- [Ovládací prvek Panel](panel-control-windows-forms.md)
- [Přehled ovládacího prvku Panel](panel-control-overview-windows-forms.md)
- [Postupy: Nastavení pozadí panelu](how-to-set-the-background-of-a-windows-forms-panel.md)
