---
title: "TableLayoutPanel – přehled ovládacího prvku"
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
- TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 614887524a49e1163b3049111895166995fdace4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel – přehled ovládacího prvku
<xref:System.Windows.Forms.TableLayoutPanel> Řízení uspořádá jeho obsah v mřížce. Protože je prováděna rozložení i v době návrhu a běh, ho můžete změnit dynamicky jako změny prostředí aplikace. To umožňuje ovládacích prvků v panelu se úměrně změnit velikost, tak může reagovat na změny, jako je například změna velikosti nadřazeného ovládacího prvku nebo text délka změna z důvodu lokalizace.  
  
 Libovolný ovládací prvek Windows Forms může být podřízená <xref:System.Windows.Forms.TableLayoutPanel> řízení, včetně ostatní instance <xref:System.Windows.Forms.TableLayoutPanel>. Umožňuje vytvořit sofistikované rozložení, které se změny v době běhu přizpůsobit.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Řízení můžete rozšířit, aby odpovídala nové ovládací prvky, když budou přidány, v závislosti na hodnotě <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, a <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> vlastnosti. Nastavení buď <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> nebo <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> vlastnost na hodnotu 0 určuje, že <xref:System.Windows.Forms.TableLayoutPanel> bude nevázaných v odpovídající směru.  
  
 Můžete taky řídit směr rozšíření (vodorovné nebo svislé), po <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek je plná podřízených ovládacích prvků. Ve výchozím nastavení <xref:System.Windows.Forms.TableLayoutPanel> řízení rozšíří dolů přidáním řádků.  
  
 Pokud chcete řádky a sloupce, které se chovají jinak než výchozí chování, můžete řídit vlastnosti řádků a sloupců pomocí <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> a <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> vlastnosti. Vlastnosti řádky nebo sloupce můžete nastavit samostatně.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Řízení přidá následující vlastnosti do jeho podřízených ovládacích prvků: `Cell`, `Column`, `Row`, `ColumnSpan`, a `RowSpan`.  
  
 Sloučením buněk v <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek pro nastavení `ColumnSpan` nebo `RowSpan` vlastností podřízeného prvku.  
  
1.  [Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
3.  [Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
4.  [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Postupy: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [Doporučené postupy pro ovládací prvek TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
