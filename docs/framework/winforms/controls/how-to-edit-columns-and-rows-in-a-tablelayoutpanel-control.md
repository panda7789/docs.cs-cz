---
title: "Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf54a02a409bead598a4e98315d5709e55677f3b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel
Můžete použít editor kolekce z <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku, s názvem **styly řádku a sloupce** dialogové okno, chcete-li upravit řádků a sloupců pro vaše ovládací prvky.  
  
> [!NOTE]
>  Pokud chcete ovládacího prvku na více řádcích nebo sloupců, nastavte `RowSpan` a `ColumnSpan` vlastnosti na ovládací prvek. Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Pokud chcete zarovnání ovládacího prvku v buňce nebo pokud chcete roztáhnout buňce ovládacího prvku, pomocí ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost. Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-edit-rows-and-columns"></a>Chcete-li upravit řádků a sloupců  
  
1.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> řídit z **sada nástrojů** do formuláře.  
  
2.  Klikněte na tlačítko <xref:System.Windows.Forms.TableLayoutPanel> glyfy inteligentní značky ovládacího prvku (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a vyberte **úpravy řádků a sloupců** otevřete  **Styly řádku a sloupce** dialogové okno. Vám může také klikněte pravým tlačítkem na <xref:System.Windows.Forms.TableLayoutPanel> řízení a vyberte **úpravy řádků a sloupců** z místní nabídky.  
  
3.  Chcete-li přidat nebo odebrat sloupce, vyberte **sloupce** z **typ člena** rozevíracího seznamu.  
  
4.  Chcete-li přidat nebo odebrat řádky, vyberte **řádky** z **typ člena** rozevíracího seznamu.  
  
5.  Klikněte na tlačítko **přidat** tlačítko Přidat sloupce či řádku na konec **člen** seznamu.  
  
6.  Klikněte **vložit** tlačítko Přidat řádku nebo sloupce před aktuálně vybrané položky v seznamu.  
  
7.  Pokud přidáváte sloupce či řádku, vyberte **typ velikosti** pro nový řádek nebo sloupec. Další informace naleznete v tématu <xref:System.Windows.Forms.SizeType>.  
  
8.  Chcete-li odebrat sloupce či řádku, klikněte na tlačítko **odebrat** tlačítko Odstranit aktuálně vybrané položky v **člen** seznamu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.SizeType>  
 [Ovládací prvek TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
