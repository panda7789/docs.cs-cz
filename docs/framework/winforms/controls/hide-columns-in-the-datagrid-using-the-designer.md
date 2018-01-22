---
title: "Postupy: Skrývání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f09bcdd3db201aa270ff7b124c8b142ecd588746
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Skrývání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Někdy budete chtít zobrazit jenom některé sloupce, které jsou k dispozici v systému Windows Forms <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Například můžete chtít zobrazit zaměstnanec mzda sloupec uživatelů s přihlašovacími údaji správy při skrytí od jiných uživatelů. Alternativně můžete vytvořit vazbu ovládacího prvku na zdroj dat, který obsahuje mnoho sloupců, jenom některé z nich chcete zobrazit. V takovém případě bude obvykle odeberte sloupce, které vás zajímá není v zobrazení, nikoli jejich skrytí. Další informace najdete v tématu [postupy: Přidání a odebrání sloupců v Windows Forms DataGridView – ovládací prvek pomocí návrháře](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-hide-a-column-using-the-designer"></a>Skrytí sloupce pomocí návrháře  
  
1.  Klikněte na inteligentní značky glyfy (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> řízení a potom vyberte **upravit sloupce**.  
  
2.  Vyberte sloupce z **vybrané sloupce** seznamu.  
  
3.  V **vlastnosti sloupce** mřížky, nastavte <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> vlastnost `false`.  
  
    > [!NOTE]
    >  Můžete také skrýt sloupce při přidávání zrušením **viditelný** zaškrtávací políčko **přidat sloupec** dialogové okno.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Postupy: Přidávání ovládacích prvků do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
