---
title: "Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bdd208d589c6b38088074f6d94045651df7049e8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře
Tabulková data se zobrazí často ve formátu účetní knihy, kde mají střídavých řádků různých barev pozadí. Tento formát usnadňuje uživatelům říct buněk, které jsou v jednotlivých řádcích, zejména s wide tabulky, které mají mnoho sloupců.  
  
 Pomocí <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete zadat informace o dokončení stylu střídavých řádků. Styl charakteristiky, jako jsou například barvu popředí a písma, kromě barvu pozadí slouží k odlišení střídavých řádků. Další informace najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="define-styles-for-alternating-rows"></a>Definování stylů střídavých řádků  
  
1.  Vyberte <xref:System.Windows.Forms.DataGridView> ovládacího prvku v návrháři.  
  
2.  V **vlastnosti** okně klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> vlastnost.  
  
3.  V **objektu CellStyle** dialogové okno, zadejte styl nastavením vlastností a použít **Preview** podokně k potvrzení voleb. Styly, které zadáte, se používají pro každý druhý řádek, který se zobrazí v ovládacím prvku, počínaje na druhou.  
  
4.  Chcete-li definovat styly pro zbývající řádky, opakujte kroky 2 a 3 pomocí <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> vlastnost.  
  
    > [!NOTE]
    >  Zobrazení buněk pomocí styly zděděno z více vlastností. Další informace o dědičnosti styl najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Používání Návrháře s ovládacím prvkem Windows Forms DataGridView](../../../../docs/framework/winforms/controls/using-the-designer-with-the-windows-forms-datagridview-control.md)  
 [Postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Postupy: Přidávání ovládacích prvků do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
