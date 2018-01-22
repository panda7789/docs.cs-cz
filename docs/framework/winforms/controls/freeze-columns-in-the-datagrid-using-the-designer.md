---
title: "Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře"
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
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33606cc30ccc1d63e780d07bcb1757d62b7ebea2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Když uživatelé zobrazit data zobrazená v systému Windows Forms <xref:System.Windows.Forms.DataGridView> ovládací prvek, někdy potřebují k odkazování na jeden sloupec nebo sadu sloupců často. Například když zobrazíte informace o zákazníkovi, který obsahuje mnoho sloupců tabulky, je vhodné pro zobrazit jméno zákazníka za všech okolností při povolování ostatních sloupců posun mimo oblast viditelné.  
  
 K dosažení toto chování, můžete zmrazení sloupců v ovládacím prvku. Po ukotvení sloupec se všechny sloupce na levé straně, (nebo záhlavím vpravo ve skriptech jazyk zprava doleva) jsou také pozastaveny. Ukotvené sloupce, takže zůstávají na svém místě, při lze posunout všech ostatních sloupců. Pokud je povoleno změny pořadí sloupců, ukotvené sloupce jsou považovány za skupinu liší od neukotvené sloupce. Uživatelé mohou změnit umístění sloupce buď skupiny, ale sloupec nemůže přesunout z jedné skupiny na druhý.  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-freeze-a-column-using-the-designer"></a>Chcete-li ukotvit sloupec pomocí návrháře  
  
1.  Klikněte na inteligentní značky glyfy (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> řízení a potom vyberte **upravit sloupce**.  
  
2.  Vyberte sloupce z **vybrané sloupce** seznamu.  
  
3.  V **vlastnosti sloupce** mřížky, nastavte <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> vlastnost `true`.  
  
    > [!NOTE]
    >  Můžete také ukotvit sloupec při přidávání výběrem **zmrazené** pole **přidat sloupec** dialogové okno.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 [Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 [Postupy: zobrazení textu zprava doleva ve Windows Forms pro globalizaci](http://msdn.microsoft.com/library/f0663385-2354-4c65-8676-706422283b14)  
 [Postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Postupy: Přidávání ovládacích prvků do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
