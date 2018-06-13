---
title: Ovládací prvky s vestavěnou podporou vykreslování vlastníkem
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
ms.openlocfilehash: a5cbdc733a2f1cda3e708ceaae8604297f8da58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529244"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Ovládací prvky s vestavěnou podporou vykreslování vlastníkem
Kreslení v systému Windows Forms, který je také označován jako vlastní kreslení, vlastníka je technika pro změnu vzhled určitých ovládacích prvků.  
  
> [!NOTE]
>  Slovo "řízení" v tomto tématu se používá k označení třídy, které jsou odvozeny od buď <xref:System.Windows.Forms.Control> nebo <xref:System.ComponentModel.Component>.  
  
 Obvykle Windows zpracovává Malování automaticky pomocí nastavení vlastností, jako <xref:System.Windows.Forms.Control.BackColor%2A> k určení vzhledu ovládacího prvku. Kreslení vlastníka můžete provést nad tímto procesem Malování Změna vzhledu prvky, které nejsou k dispozici pomocí vlastností. Například mnoho ovládací prvky umožňují nastavit barvu textu, který se zobrazí, ale jste omezeni na jedné barvy. Kreslení vlastníka můžete například zobrazit část textu v černé a část červeně.  
  
 V praxi je podobný jako při kreslení grafiky ve formuláři kreslení vlastníka. Například můžete použít metody grafiky v obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Control.Paint> událostí emulovat `ListBox` řízení, ale muset napsat vlastní kód pro zpracování všechny interakce s uživatelem. S kreslení vlastníka ovládacího prvku používá kódu kreslení její obsah, ale jinak uchovává všechny vlastní možnosti. Grafické metody můžete použít k vykreslení jednotlivých položek v ovládacím prvku nebo chcete-li přizpůsobit některé aspekty každé položky při používat výchozí vzhled pro další aspekty každé položky.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Kreslení vlastníka ve Windows Forms – ovládací prvky  
 K provedení vlastníka kreslení v ovládacích prvcích, které ji podporují, se obvykle nastavit jednu vlastnost a zpracovat jeden nebo více událostí.  
  
 Většina ovládacích prvků kreslení vlastníka tohoto podporu má `OwnerDraw` nebo `DrawMode` vlastnost, která určuje, zda bude ovládací prvek zvýšit jeho kreslení související události nebo událostí v případě, že ho vybarví sám sebe.  
  
 Ovládací prvky, které nemají `OwnerDraw` nebo `DrawMode` vlastnost, zahrnout `DataGridView` řízení, které poskytuje kreslení události, které se automaticky provedou, a `ToolStrip` řízení, které je vykresleno pomocí třídu externí vykreslování, který má svou vlastní Kreslení související události.  
  
 Existuje mnoho různých druhů kreslení události, avšak typické kreslení události dojde k vykreslení jednu položku v ovládacím prvku. Obslužné rutiny události obdrží `EventArgs` objekt, který obsahuje informace o položce přitahuje a nástroje, které můžete použít k vykreslení ho. Například tento objekt obsahuje obvykle číslo indexu položky v rámci jeho kolekce nadřazených <xref:System.Drawing.Rectangle> určující položky zobrazit hranice a <xref:System.Drawing.Graphics> objekt pro volání metod Malování. Pro některé události `EventArgs` objekt poskytuje další informace o položky a metody, které můžete volat k vyplnění některé aspekty položky ve výchozím nastavení, jako je například na pozadí nebo rámečku fokusu.  
  
 Pokud chcete vytvořit opakovaně použitelný ovládací prvek, který obsahuje vlastní nastavení vykreslovaných vlastníkem, vytvořte novou třídu odvozenou z ovládacího prvku třídu, která podporuje kreslení vlastníka. Místo zpracování kreslení událostí, zahrnout kódu vykreslování vlastníkem přepsání pro příslušné `On` *EventName* metodu nebo metody ve třídě nové. Ujistěte se, že zavoláte základní třídy `On` *EventName* metodu nebo metody v tomto případě tak, aby uživatelé ovládacího prvku zpracování vykreslování vlastníkem událostí a poskytnout další přizpůsobení.  
  
 Následující Windows Forms – ovládací prvky kreslení ve všech verzích rozhraní .NET Framework vlastníka podpory:  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <xref:System.Windows.Forms.MenuItem> (používané <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu>)  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 Ovládací prvky podporují pouze v kreslení vlastníka [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Ovládací prvky podporují kreslení vlastníka a jsou v nové [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 Následující části obsahují další podrobnosti pro každou z těchto ovládacích prvků.  
  
### <a name="listbox-and-combobox-controls"></a>ListBox – a ComboBox – ovládací prvky  
 <xref:System.Windows.Forms.ListBox> a <xref:System.Windows.Forms.ComboBox> ovládací prvky umožňují kreslení jednotlivé položky v ovládacím prvku všechno ve velikosti nebo v různou velikost.  
  
> [!NOTE]
>  I když <xref:System.Windows.Forms.CheckedListBox> ovládací prvek je odvozený od <xref:System.Windows.Forms.ListBox> řízení, nepodporuje kreslení vlastníka.  
  
 Kreslení každou položku stejnou velikost, nastavte `DrawMode` vlastnost, která má <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> a zpracovat `DrawItem` událostí.  
  
 Kreslení každou položku pomocí různých velikostí, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> a zpracovat oba `MeasureItem` a `DrawItem` události. `MeasureItem` Událostí umožňuje určit velikost položky před `DrawItem` této položky dojde k události.  
  
 Další informace, včetně příkladů kódu naleznete v následujících tématech:  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [Postupy: Vytvoření textu proměnlivé velikosti v ovládacím prvku ComboBox](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>Součást MenuItem  
 <xref:System.Windows.Forms.MenuItem> Představuje samostatnou položku nabídky v součásti <xref:System.Windows.Forms.MainMenu> nebo <xref:System.Windows.Forms.ContextMenu> součásti.  
  
 Kreslení <xref:System.Windows.Forms.MenuItem>, nastavte jeho `OwnerDraw` vlastnost `true` a zpracovat jeho `DrawItem` událostí. Chcete-li přizpůsobit velikost položky nabídky před `DrawItem` události dojde, zpracování položky `MeasureItem` událostí.  
  
 Další informace, včetně příkladů kódu najdete v těchto tématech:  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl – ovládací prvek  
 <xref:System.Windows.Forms.TabControl> Řízení umožňuje kreslení jednotlivé karty v ovládacím prvku. Kreslení vlastníka ovlivňuje pouze karty; <xref:System.Windows.Forms.TabPage> obsah neovlivní.  
  
 Kreslení každé kartě <xref:System.Windows.Forms.TabControl>, nastavte `DrawMode` vlastnost, která má <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> a zpracovat `DrawItem` událostí. Tato událost nastane jednou pro každé kartě jenom v případě, že je na kartě viditelné v ovládacím prvku.  
  
 Další informace, včetně příkladů kódu najdete v těchto tématech:  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip – komponenta  
 <xref:System.Windows.Forms.ToolTip> Součást umožňuje kreslení celý popisek, jakmile se zobrazí.  
  
 Kreslení <xref:System.Windows.Forms.ToolTip>, nastavte jeho `OwnerDraw` vlastnost `true` a zpracovat jeho `Draw` událostí. Chcete-li přizpůsobit velikost <xref:System.Windows.Forms.ToolTip> před `Draw` události dojde, zpracování `Popup` událostí a sady <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> vlastnost v obslužné rutiny události.  
  
 Další informace, včetně příkladů kódu najdete v těchto tématech:  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView – ovládací prvek  
 <xref:System.Windows.Forms.ListView> Řízení umožňuje kreslení jednotlivé položky, podřízených položek a záhlaví sloupců v ovládacím prvku.  
  
 Chcete-li povolit kreslení v ovládacím prvku vlastníka, nastavte `OwnerDraw` vlastnost `true`.  
  
 Kreslení jednotlivých položek v ovládacím prvku, zpracování `DrawItem` událostí.  
  
 Kreslení každý záhlaví sloupce či podřízenou položku v ovládacím prvku při <xref:System.Windows.Forms.ListView.View%2A> je nastavena na <xref:System.Windows.Forms.View.Details>, zpracování `DrawSubItem` a `DrawColumnHeader` události.  
  
 Další informace, včetně příkladů kódu najdete v těchto tématech:  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView – ovládací prvek  
 <xref:System.Windows.Forms.TreeView> Řízení umožňuje kreslení jednotlivé uzly v ovládacím prvku.  
  
 Kreslení pouze text zobrazovaný v každém uzlu, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> a zpracovat `DrawNode` událost, která má nakreslit text.  
  
 Kreslení všechny elementy každého uzlu, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> a zpracovat `DrawNode` událostí k vykreslení elementů, podle toho, která budete potřebovat, jako například textu, ikony, zaškrtněte políčka, plus a minus a čáry propojující uzly.  
  
 Další informace, včetně příkladů kódu najdete v těchto tématech:  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView – ovládací prvek  
 <xref:System.Windows.Forms.DataGridView> Řízení umožňuje kreslení jednotlivých buněk a řádků v ovládacím prvku.  
  
 Kreslení jednotlivých buněk, zpracování `CellPainting` událostí.  
  
 K vykreslení elementů řádků nebo jednotlivých řádků, zpracovat jeden nebo oba `RowPrePaint` a `RowPostPaint` události. `RowPrePaint` Předtím, než se vykresluje v buňkách v řádku, dojde k události a `RowPostPaint` po buněk se vykresluje dojde k události. Dokáže zpracovat oba události a `CellPainting` událost Malování řádek pozadí, jednotlivých buněk a řádek popředí samostatně, nebo můžete zadat konkrétní přizpůsobení, kde je potřebujete a použít výchozí zobrazení pro další prvky řádek.  
  
 Další informace, včetně příkladů kódu naleznete v následujících tématech:  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip – ovládací prvek  
 <xref:System.Windows.Forms.ToolStrip> a odvozené ovládací prvky umožňují přizpůsobit kteréhokoli aspektu jejich vzhled.  
  
 Poskytnout vlastní vykreslení pro <xref:System.Windows.Forms.ToolStrip> ovládací prvky, nastavení `Renderer` vlastnost <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, nebo <xref:System.Windows.Forms.ToolStripContentPanel> k `ToolStripRenderer` objektu a zpracovat jeden nebo více mnoho kreslení událostí poskytované `ToolStripRenderer` třídy. Alternativně nastavte `Renderer` vlastnost, která má instance vlastní třídy odvozené od `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, nebo <xref:System.Windows.Forms.ToolStripSystemRenderer> implementuje nebo přepsání konkrétní `On` *EventName* metody.  
  
 Další informace, včetně příkladů kódu naleznete v následujících tématech:  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [Postupy: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip ve Windows Forms](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [Postupy: Vlastní vykreslení ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
