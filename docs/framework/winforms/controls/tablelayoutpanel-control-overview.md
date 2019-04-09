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
ms.openlocfilehash: 57a57b9f888f2fc46eddba5b97b9e833a7e9f028
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134014"
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
  
3.  [Postupy: Úpravy sloupců a řádků v ovládacím prvku TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [Návod: Uspořádání ovládacích prvků ve Windows Forms s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutSettings>
- [Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [Postupy: Vytvoření formuláře Windows Forms s možností změny velikosti pro zadávání dat](how-to-create-a-resizable-windows-form-for-data-entry.md)
- [Doporučené postupy pro ovládací prvek TableLayoutPanel](best-practices-for-the-tablelayoutpanel-control.md)
