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
ms.openlocfilehash: 1807170b2f5df2333ec3b271a11f9b929c1e7993
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087180"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Ovládací prvky s vestavěnou podporou vykreslování vlastníkem
Vykreslení ve Windows Forms, který je také označován jako vlastní kreslení, vlastníka je postup pro změnu vizuálního vzhledu některé ovládací prvky.  
  
> [!NOTE]
>  Slovo "control" v tomto tématu se používá k označení tříd, které jsou odvozeny z buď <xref:System.Windows.Forms.Control> nebo <xref:System.ComponentModel.Component>.  
  
 Obvykle Windows zpracovává Malování automaticky pomocí nastavení vlastností, jako <xref:System.Windows.Forms.Control.BackColor%2A> k určení vzhledu ovládacího prvku. Pomocí vykreslení vlastníka můžete převzít kontrolu nad procesu Malování Změna vzhledu prvky, které nejsou k dispozici s použitím vlastností. Například mnoho ovládacích prvků můžete tak nastavit barvu textu, který se zobrazí, ale pro vás platí omezení na jednu barvu. Kreslení vlastníka můžete třeba zobrazit část textu v černé a část červeně.  
  
 V praxi se podobá vykreslování grafiky ve formuláři vykreslení vlastníka. Například můžete použít grafické metody v obslužné rutině pro daný formulář <xref:System.Windows.Forms.Control.Paint> událostí k emulaci `ListBox` ovládacího prvku, ale byste museli napsat vlastní kód pro zpracování všechny interakce s uživatelem. Pomocí vykreslení vlastníka ovládací prvek nakreslit jeho obsah pomocí kódu, ale jinak uchovává všechny vnitřní funkce. Metody grafiky můžete použít k vykreslení každou položku v ovládacím prvku nebo přizpůsobit některé aspekty každou položku, když použijete výchozí vzhled jiných aspektů každé položky.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Kreslení vlastníka ve Windows Forms ovládací prvky  
 K provedení vlastníka kreslení v ovládacích prvcích, které ho podporují, bude obvykle jednu vlastnost a zpracovat jeden nebo více událostí.  
  
 Většina ovládací prvky mají tento vlastník podporu kreslení `OwnerDraw` nebo `DrawMode` vlastnost, která označuje, zda ovládací prvek vyvolá jeho události související s kreslení nebo události, kdy ho jsou vykreslovány samotný.  
  
 Ovládací prvky, které nemají `OwnerDraw` nebo `DrawMode` zahrnují vlastnosti `DataGridView` ovládací prvek, který poskytuje výkresu události, které se automaticky provedou, a `ToolStrip` ovládací prvek, který je vykreslen třídu externí vykreslování, který má vlastní Kreslení související události.  
  
 Existuje mnoho různých druhů kreslení události, ale typické výkresu události dojde k vykreslení jednu položku v ovládacím prvku. Obslužná rutina události obdrží `EventArgs` objekt, který obsahuje informace o položkách, které je cílem vykreslování a nástrojích, které můžete použít k vykreslení ho. Například tento objekt obvykle obsahuje položky číslo indexu v rámci kolekce jeho nadřazených prvků <xref:System.Drawing.Rectangle> , který určuje položky zobrazit hranice a <xref:System.Drawing.Graphics> objekt pro volání metod Malování. Pro některé události `EventArgs` objekt poskytuje další informace o položky a metody, které můžete volat za účelem vykreslení některé aspekty položky ve výchozím nastavení, jako je například na pozadí nebo rámečku fokusu.  
  
 Vytvoření opakovaně použitelné ovládací prvek, který obsahuje vaše vlastní nastavení vykreslovaných vlastníkem, vytvořte novou třídu, která je odvozena z třídy ovládacího prvku, který podporuje vykreslení vlastníka. Namísto zpracování událostí výkresu, zahrnout kód vykreslování vlastníkem přepsání pro odpovídající `On` *EventName* metodu nebo metody v této nové třídě. Ujistěte se, že můžete volat základní třídy `On` *EventName* metodu nebo metody v tomto případě tak, aby uživatelé ovládacího prvku může zpracovávat události vykreslování vlastníkem a poskytují líp přizpůsobte.  
  
 Následující Windows Forms – ovládací prvky podporu vlastníka kreslení ve všech verzích rozhraní .NET Framework:  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <xref:System.Windows.Forms.MenuItem> (používají <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu>)  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 Vlastník kreslení pouze v podporují následující ovládací prvky [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Následující ovládací prvky podporují kreslení vlastníka a jsou novinkou [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 Následující části obsahují další podrobnosti pro každou z těchto ovládacích prvků.  
  
### <a name="listbox-and-combobox-controls"></a>ListBox – a ovládací prvky pole se seznamem  
 <xref:System.Windows.Forms.ListBox> a <xref:System.Windows.Forms.ComboBox> ovládací prvky umožňují nakreslete jednotlivých položek v ovládacím prvku vše na velikosti, nebo v různých velikostí.  
  
> [!NOTE]
>  I když <xref:System.Windows.Forms.CheckedListBox> ovládací prvek je odvozený z <xref:System.Windows.Forms.ListBox> ovládacího prvku, a proto není podporována vykreslení vlastníka.  
  
 Chcete-li nakreslit každou položku se stejnou velikostí, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> a zpracovat `DrawItem` událostí.  
  
 Chcete-li nakreslit každou položku pomocí různých velikostí, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> a zpracovat oba `MeasureItem` a `DrawItem` události. `MeasureItem` Událostí umožňuje určit velikost položky před `DrawItem` dojde k události pro danou položku.  
  
 Další informace, včetně příkladů kódu naleznete v následujících tématech:  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [Postupy: Vytvoření textu proměnlivé velikosti v ovládacím prvku ComboBox](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>Komponenta položku nabídky  
 <xref:System.Windows.Forms.MenuItem> Představuje samostatnou položku nabídky v součásti <xref:System.Windows.Forms.MainMenu> nebo <xref:System.Windows.Forms.ContextMenu> komponenty.  
  
 Chcete-li nakreslit <xref:System.Windows.Forms.MenuItem>, nastavte jeho `OwnerDraw` vlastnost `true` a zpracovat jeho `DrawItem` událostí. Chcete-li přizpůsobit velikost položky nabídky před `DrawItem` dojde k události, zpracování položky `MeasureItem` událostí.  
  
 Další informace, včetně příkladů kódu naleznete v následujících tématech:  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl – ovládací prvek  
 <xref:System.Windows.Forms.TabControl> Ovládací prvek umožňuje nakreslit jednotlivé karty v ovládacím prvku. Kreslení vlastníka má vliv pouze na karty; <xref:System.Windows.Forms.TabPage> obsah to nebude mít vliv.  
  
 Chcete-li nakreslit každá karta <xref:System.Windows.Forms.TabControl>, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> a zpracování `DrawItem` událostí. Tato událost akce proběhne jednou pro každou kartu pouze v případě, že na kartě zobrazený v ovládacím prvku.  
  
 Další informace, včetně příkladů kódu naleznete v následujících tématech:  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip – komponenta  
 <xref:System.Windows.Forms.ToolTip> Komponenty umožňuje nakreslit celý popis, jakmile se zobrazí.  
  
 Chcete-li nakreslit <xref:System.Windows.Forms.ToolTip>, nastavte jeho `OwnerDraw` vlastnost `true` a zpracovat jeho `Draw` událostí. Přizpůsobit velikost <xref:System.Windows.Forms.ToolTip> před `Draw` dojde k události, zpracování `Popup` událostí a nastavte <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> vlastnost v obslužné rutině události.  
  
 Další informace, včetně příkladů kódu naleznete v následujících tématech:  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView – ovládací prvek  
 <xref:System.Windows.Forms.ListView> Ovládací prvek umožňuje nakreslit jednotlivých položek, podřízené položky a záhlaví sloupců v ovládacím prvku.  
  
 Pokud chcete povolit vlastníka výkres v ovládacím prvku, nastavte `OwnerDraw` vlastnost `true`.  
  
 Chcete-li nakreslit každou položku v ovládacím prvku, zpracovat `DrawItem` událostí.  
  
 Chcete-li nakreslit záhlaví každého sloupce nebo podřízenou položku v ovládacím prvku při <xref:System.Windows.Forms.ListView.View%2A> je nastavena na <xref:System.Windows.Forms.View.Details>, zpracovat `DrawSubItem` a `DrawColumnHeader` události.  
  
 Další informace, včetně příkladů kódu naleznete v následujících tématech:  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView – ovládací prvek  
 <xref:System.Windows.Forms.TreeView> Ovládací prvek umožňuje nakreslit jednotlivé uzly v ovládacím prvku.  
  
 Chcete-li nakreslit pouze text zobrazený v každém uzlu, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> a zpracovat `DrawNode` události vykreslování textu.  
  
 Chcete-li nakreslit všechny prvky každého uzlu, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> a zpracovat `DrawNode` událost k vykreslení elementů, podle toho, která budete potřebovat, jako například text, ikony, zaškrtněte políčka, plus a minus a čáry spojující uzly.  
  
 Další informace, včetně příkladů kódu naleznete v následujících tématech:  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView – ovládací prvek  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek umožňuje nakreslit jednotlivé buňky a řádků v ovládacím prvku.  
  
 Chcete-li nakreslit jednotlivé buňky, zpracovat `CellPainting` událostí.  
  
 Chcete-li nakreslit jednotlivé řádky nebo řádků, zpracovat jeden nebo oba `RowPrePaint` a `RowPostPaint` události. `RowPrePaint` Předtím, než jsou překreslit buňky v řádku, dojde k události a `RowPostPaint` po buňky jsou překreslit dojde k události. Dokáže zpracovat oba události a `CellPainting` událost k vykreslení pozadí řádku, jednotlivé buňky a řádek popředí samostatně, nebo můžete zadat konkrétní přizpůsobení, kde je potřebujete a použijte výchozí zobrazení pro další prvky řádku.  
  
 Další informace, včetně příkladů kódu naleznete v následujících tématech:  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip – ovládací prvek  
 <xref:System.Windows.Forms.ToolStrip> a odvozené ovládací prvky umožňují přizpůsobit jiného aspektu jejich výskytu.  
  
 Poskytnout vlastní vykreslování pro <xref:System.Windows.Forms.ToolStrip> ovládací prvky, nastavit `Renderer` vlastnost <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, nebo <xref:System.Windows.Forms.ToolStripContentPanel> k `ToolStripRenderer` objektu a zpracovat jeden nebo více mnoho událostí výkresu poskytované `ToolStripRenderer` třídy. Můžete také nastavit `Renderer` vlastnost instance vlastní třídy odvozené z `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, nebo <xref:System.Windows.Forms.ToolStripSystemRenderer> , který implementuje nebo přepíše konkrétní `On` *EventName* metody.  
  
 Další informace, včetně příkladů kódu naleznete v následujících tématech:  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [Postupy: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip ve Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [Postupy: Vlastní vykreslení ovládacího prvku ToolStrip](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
