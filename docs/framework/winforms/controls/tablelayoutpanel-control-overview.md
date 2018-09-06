---
title: TableLayoutPanel – přehled ovládacího prvku
ms.date: 03/30/2017
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
ms.openlocfilehash: be7ef4055d809349fe97a3d48e29158c5449576b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855800"
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel – přehled ovládacího prvku
<xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek uspořádá její obsah do mřížky. Protože je prováděna rozložení i v době návrhu a běhu, můžete změnit dynamicky se změnami prostředí aplikace. To umožňuje ovládací prvky v panelu proporcionálně velikost, tak můžou reagovat na změny, jako je například změna velikosti nadřazeného ovládacího prvku nebo text délka mění kvůli lokalizace.  
  
 Libovolný ovládací prvek Windows Forms může být podřízený <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek, včetně dalších instancí <xref:System.Windows.Forms.TableLayoutPanel>. To umožňuje vytvořit sofistikované rozložení, které přizpůsoboval změnám v době běhu.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Ovládacího prvku můžete rozšířit tak, aby vyhovovaly nových ovládacích prvků, když se přidají, závisí na hodnotě <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, a <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> vlastnosti. Nastavení buď <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> nebo <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> vlastnost na hodnotu 0 určuje, že <xref:System.Windows.Forms.TableLayoutPanel> bude nevázaných ve směru odpovídající.  
  
 Můžete také řídit směr rozbalení (horizontal nebo vertical) po <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek je plná podřízených ovládacích prvků. Ve výchozím nastavení <xref:System.Windows.Forms.TableLayoutPanel> rozbalí přidáním řádků ovládacího prvku.  
  
 Pokud chcete řádky a sloupce, které se chovají odlišně od výchozí chování, můžete řídit vlastnosti řádků a sloupců pomocí <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> a <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> vlastnosti. Můžete nastavit vlastnosti řádky nebo sloupce samostatně.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Ovládacího prvku přidá následující vlastnosti do jeho podřízených ovládacích prvků: `Cell`, `Column`, `Row`, `ColumnSpan`, a `RowSpan`.  
  
 Můžete sloučit buňky v <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku tak, že nastavíte `ColumnSpan` nebo `RowSpan` vlastnosti na podřízený ovládací prvek.  
  
1.  [Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Postupy: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [Doporučené postupy pro ovládací prvek TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
