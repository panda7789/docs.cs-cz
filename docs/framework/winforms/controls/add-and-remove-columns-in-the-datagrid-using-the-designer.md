---
title: "Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fdb57cf2134ee4f221a26db61cfdcc48dc92548
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Windows Forms <xref:System.Windows.Forms.DataGridView> řízení musí obsahovat sloupce, aby bylo možné zobrazit data. Pokud budete chtít naplnit ovládací prvek ručně, musíte přidat sloupce sami. Alternativně můžete vázat ovládacího prvku na zdroj dat, který generuje a automaticky naplní sloupce. Pokud zdroj dat obsahuje více sloupců, než se má zobrazit, můžete odebrat nežádoucí sloupce.  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-column-using-the-designer"></a>Chcete-li přidat sloupec pomocí návrháře  
  
1.  Klikněte na inteligentní značky glyfy (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> řízení a potom vyberte **přidat sloupec**.  
  
2.  V **přidat sloupec** dialogovém okně vyberte **Vycentrovat sloupec** možnost a vyberte sloupec ze zdroje dat nebo zvolte **nepřipojeného sloupce** možnost a definovat sloupce použití polí zadat.  
  
3.  Klikněte **přidat** tlačítko Přidat sloupec, způsobuje se zobrazí v návrháři, pokud existující sloupce již nevyplní oblasti zobrazení ovládacího prvku.  
  
    > [!NOTE]
    >  Můžete upravit vlastnosti sloupce v **upravit sloupce** dialogové okno, které je dostupné z inteligentní značky ovládacího prvku.  
  
### <a name="to-remove-a-column-using-the-designer"></a>Pokud chcete odebrat sloupec pomocí návrháře  
  
1.  Zvolte **upravit sloupce** z inteligentní značky ovládacího prvku.  
  
2.  Vyberte sloupce z **vybrané sloupce** seznamu.  
  
3.  Klikněte **odebrat** tlačítko odstranění sloupce, způsobuje její zmizí z návrháře.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 [Postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Postupy: Přidávání ovládacích prvků do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
