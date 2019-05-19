---
title: 'Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 0e5714663a0873cb275d2909028a7d791be76fcf
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882230"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře
Tabulkové data se často zobrazují ve formátu účetní knihy, kde mají různých barev pozadí střídavých řádků. Tento formát usnadňuje uživatelům řekněte, buněk, které jsou v jednotlivých řádcích, zejména u širokých tabulek, které mají mnoho sloupců.  
  
 S <xref:System.Windows.Forms.DataGridView> ovládacího prvku, můžete zadat informace o dokončení stylu pro střídavé řádky. Vlastnosti stylu jako barva popředí a písma, kromě barvu pozadí, můžete použít k rozlišení střídavé řádky. Další informace najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="define-styles-for-alternating-rows"></a>Definovat styly pro střídavé řádky  
  
1. Vyberte <xref:System.Windows.Forms.DataGridView> ovládací prvek v návrháři.  
  
2.  V **vlastnosti** okna, klikněte na tlačítko se třemi tečkami (![The třemi tečkami (...) v okně Vlastnosti systému Visual Studio](./media/visual-studio-ellipsis-button.png)) vedle položky <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> vlastnost.  
  
3. V **sestavení objektu CellStyle** dialogové okno, definujte styl nastavením vlastností a použít **ve verzi Preview** podokně zkontrolujte zvolené volby. Styly, které zadáte, se používají pro každý druhý řádek zobrazí v ovládacím prvku, počínaje druhý.  
  
4. Chcete-li definovat styly zbývajících řádků, opakujte kroky 2 a 3 pomocí <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> vlastnost.  
  
    > [!NOTE]
    >  Použití stylů zděděno z více vlastností jsou zobrazeny buňky. Další informace o dědičnost stylů, najdete v části [styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Používání Návrháře s ovládacím prvkem Windows Forms DataGridView](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Postupy: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidání ovládacích prvků do formulářů Windows](how-to-add-controls-to-windows-forms.md)
