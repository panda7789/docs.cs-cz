---
title: "Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2a203aa20865a4180b4eb9a7b192fc3c9b73a2f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView pomocí Návrháře
Můžete použít návrháře pro připojení <xref:System.Windows.Forms.DataGridView> ovládacího prvku do zdroje dat několik různé typy, včetně databází, obchodní objekty nebo webové služby. Při vytvoření vazby ovládacího prvku ke zdroji dat pomocí návrháře, je ovládací prvek vázán automaticky k <xref:System.Windows.Forms.BindingSource> komponenty, která představuje příslušný zdroj dat. Kromě toho sloupce jsou automaticky generovány v ovládacím prvku tak, aby odpovídaly zadaný zdroj dat informace o schématu.  
  
 Po vygenerování sloupců, můžete upravit, aby vyhovovala vašim potřebám. Například můžete odebrat nebo skrýt sloupce vás zajímá není v zobrazení, můžete pořadí sloupců nebo můžete upravit typy sloupců. Další informace o úpravách sloupců najdete v tématech uvedených v části Viz také.  
  
 Můžete také navázat více <xref:System.Windows.Forms.DataGridView> ovládací prvky pro tabulky v relaci k vytvoření relací a podrobností. V této konfiguraci jeden ovládací prvek zobrazí nadřazenou tabulkou a další ovládací prvek pouze řádky z podřízené tabulky, které se vztahují k aktuální řádek v nadřazené tabulce. Další informace najdete v tématu [postupy: zobrazení souvisejících dat ve formulářové aplikaci Windows](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek nebo dvou ovládacích prvků pro relaci a podrobností. Informace o spuštění tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-the-control-to-a-data-source"></a>K vytvoření vazby ovládacího prvku ke zdroji dat  
  
1.  Klikněte na inteligentní značky glyfy (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
2.  Klikněte na šipku rozevíracího seznamu pro **zvolit zdroj dat** možnost.  
  
3.  Pokud váš projekt již nemá zdroj dat, klikněte na tlačítko **přidat zdroj dat projektu** a postupujte podle kroků uvedených v průvodci.  
  
     Další informace najdete v tématu [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). Váš nový zdroj dat se objeví v **zvolit zdroj dat** okno rozevíracího seznamu. Pokud váš nový zdroj dat obsahuje pouze jednoho člena, jako je například jeden databázové tabulky, vytvoří automaticky vazbu ovládacího prvku tohoto člena. V opačném případě pokračujte k dalšímu kroku.  
  
4.  Rozbalte **jiných zdrojů dat** a **zdroje dat projektu** uzly, pokud nejsou rozbalená a potom vyberte zdroj dat pro vazbu ovládacího prvku do.  
  
5.  Pokud zdroj dat obsahuje více než jednoho člena, jako třeba když jste vytvořili <xref:System.Data.DataSet?displayProperty=nameWithType> obsahující více tabulek, rozbalení zdroje dat a pak vyberte konkrétní člena pro vazbu.  
  
6.  K vytvoření vztahu seznam podrobnosti v **zvolit zdroj dat** rozevíracího okna pro druhý <xref:System.Windows.Forms.DataGridView> řídit, rozbalte <xref:System.Windows.Forms.BindingSource> vytvoří pro nadřazenou tabulku a pak vybrat související podřízenou tabulku ze seznamu Zobrazit.  
  
    > [!NOTE]
    >  Pokud váš projekt již má zdroj dat, můžete také použít **zdroje dat** okno Vytvoření dat formuláře. Další informace najdete v tématu [okno zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 [Postupy: připojování k datům v databázi](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556)  
 [Postupy: přidávání a odebírání sloupců v systému Windows Forms DataGridView – ovládací prvek pomocí návrháře](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Postupy: Změna pořadí sloupců v prvku Windows Forms DataGridView pomocí návrháře](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 [Postupy: Změna typu sloupce Windows Forms DataGridView pomocí návrháře](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 [Postupy: zablokování sloupců v systému Windows Forms DataGridView – ovládací prvek pomocí návrháře](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 [Postupy: skrytí sloupců v systému Windows Forms DataGridView – ovládací prvek pomocí návrháře](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 [Postupy: přepnutí sloupců jen pro čtení v systému Windows Forms DataGridView – ovládací prvek pomocí návrháře](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 [Postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Okno zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)  
 [Postupy: zobrazení souvisejících dat v systému Windows Forms aplikace](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)
