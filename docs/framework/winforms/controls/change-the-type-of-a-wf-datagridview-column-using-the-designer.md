---
title: 'Postupy: Změna typu sloupce Windows Forms DataGridView pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 12e6e15dd3b4e7941be198a526e8145ceb126e8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544611"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Postupy: Změna typu sloupce Windows Forms DataGridView pomocí návrháře
Někdy budete chtít změnit typ sloupce, který je už přidaná do formulářů Windows <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Můžete například změnit typy některé sloupce, které jsou generovány automaticky, když se navážete na zdroj dat ovládacího prvku. To je užitečné, když má sloupců obsahujících cizí klíče pro řádky v tabulce související tabulce, kterou můžete zobrazit. V takovém případě můžete chtít nahradit textové sloupce pole, které zobrazují tyto cizího klíče se sloupci pole se seznamem, které zobrazují lépe vystihuje hodnoty ze související tabulky.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [jak: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Chcete-li změnit typ sloupce pomocí návrháře  
  
1.  Klikněte na inteligentní označit piktogram (![piktogram inteligentní](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> ovládací prvek a potom vyberte **upravit sloupce**.  
  
2.  Vyberte sloupec **vybrané sloupce** seznamu.  
  
3.  V **vlastnosti sloupce** mřížky, nastavte `ColumnType` vlastnost na nový typ sloupce.  
  
    > [!NOTE]
    >  `ColumnType` Vlastností je vlastnost pouze pro návrh, který určuje třída představující typ sloupce. Není vlastnost aplikace skutečný definována ve třídě sloupce.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Postupy: Vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)
- [Postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
