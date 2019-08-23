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
ms.openlocfilehash: f0d4b99f9ee0134fc7334a941dd5ef4fd7ba3df3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930196"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Ovládací prvky s vestavěnou podporou vykreslování vlastníkem
Vlastní kreslení v model Windows Forms, který se také označuje jako vlastní kreslení, je technika pro změnu vzhledu některých ovládacích prvků.  
  
> [!NOTE]
> Slovo "ovládací prvek" v tomto tématu se používá jako třídy, které jsou odvozeny <xref:System.Windows.Forms.Control> z <xref:System.ComponentModel.Component>buď nebo.  
  
 Systém Windows obvykle zpracovává automatické malování pomocí nastavení vlastností, jako je <xref:System.Windows.Forms.Control.BackColor%2A> například k určení vzhledu ovládacího prvku. Při kreslení vlastníka převezmete proces Malování a změníte prvky vzhledu, které nejsou k dispozici pomocí vlastností. Mnoho ovládacích prvků například umožňuje nastavit barvu zobrazeného textu, ale budete omezeni na jednu barvu. Vlastní vykreslování umožňuje provádět akce, jako je například zobrazení části textu černě a částečně.  
  
 V praxi je kreslení vlastníka podobné kreslení grafik na formuláři. Například můžete použít grafické metody v obslužné rutině pro <xref:System.Windows.Forms.Control.Paint> událost formuláře k emulaci `ListBox` ovládacího prvku, ale budete muset napsat vlastní kód pro zpracování interakce všech uživatelů. Při kreslení vlastníka používá ovládací prvek váš kód k nakreslení jeho obsahu, ale jinak uchovává všechny jeho vnitřní funkce. Můžete použít grafické metody pro vykreslení každé položky v ovládacím prvku nebo pro přizpůsobení některých aspektů každé položky, zatímco používáte výchozí vzhled pro jiné aspekty každé položky.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Vlastní kreslení v ovládacích prvcích model Windows Forms  
 Chcete-li provést vykreslování vlastníka v ovládacích prvcích, které ho podporují, obvykle nastavíte jednu vlastnost a zpracujete jednu nebo více událostí.  
  
 Většina ovládacích prvků, které podporují kreslení vlastníka `OwnerDraw` , `DrawMode` mají vlastnost nebo, která označuje, zda ovládací prvek při malování sám vyvolá událost související s kreslením nebo události.  
  
 `OwnerDraw` Ovládací prvky, které nemají vlastnost nebo `DrawMode` , obsahují `DataGridView` ovládací prvek, který poskytuje události `ToolStrip` kreslení, ke kterým dochází automaticky, a ovládací prvek, který je vykreslen pomocí externí třídy vykreslování, která má vlastní. události související s vykreslováním.  
  
 Existuje mnoho různých typů událostí kreslení, ale k typické události kreslení dojde, pokud chcete nakreslit jednu položku v rámci ovládacího prvku. Obslužná rutina události obdrží `EventArgs` objekt, který obsahuje informace o vykreslené položce a o nástrojích, které můžete použít k vykreslení. Například tento objekt obvykle obsahuje číslo indexu položky v rámci své nadřazené kolekce, <xref:System.Drawing.Rectangle> která označuje hranice zobrazení položky <xref:System.Drawing.Graphics> a objekt pro volání metod vybarvení. U některých událostí `EventArgs` objekt poskytuje další informace o položce a metodách, které lze volat k malování některých aspektů položky ve výchozím nastavení, jako je například pozadí nebo obdélník výběru.  
  
 Chcete-li vytvořit opakovaně použitelný ovládací prvek, který obsahuje vlastní nastavení vykreslené uživatelem, vytvořte novou třídu, která je odvozena z třídy ovládacího prvku, která podporuje vykreslování vlastníka. Místo zpracování událostí vykreslování zahrňte do přepsání kód pro vykreslení vlastníka pro příslušnou `On`metodu nebo metody *EventName* v nové třídě. Ujistěte se, že v tomto případě zavoláte metodu nebo metody `On` *EventName* základní třídy, aby uživatelé vašeho ovládacího prvku mohli zpracovávat události vykreslování vlastníka a poskytnout další přizpůsobení.  
  
 Následující model Windows Forms řídí vykreslování vlastníků ve všech verzích .NET Framework:  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <xref:System.Windows.Forms.MenuItem>(používá se <xref:System.Windows.Forms.MainMenu> v <xref:System.Windows.Forms.ContextMenu>a)  
  
- <xref:System.Windows.Forms.TabControl>  
  
 Následující ovládací prvky podporují kreslení vlastníka pouze v .NET Framework 2,0:  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 Následující ovládací prvky podporují kreslení vlastníka a jsou v .NET Framework 2,0 nové:  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 Následující části obsahují další podrobnosti o každém z těchto ovládacích prvků.  
  
### <a name="listbox-and-combobox-controls"></a>Ovládací prvky ListBox a ComboBox  
 Ovládací prvky <xref:System.Windows.Forms.ComboBox> a umožňují kreslit jednotlivé položky v ovládacím prvku buď v jedné velikosti, nebo v různých velikostech. <xref:System.Windows.Forms.ListBox>  
  
> [!NOTE]
> I když je <xref:System.Windows.Forms.ListBox> ovládací prvek odvozen z ovládacího prvku, nepodporuje vykreslování vlastníka. <xref:System.Windows.Forms.CheckedListBox>  
  
 Chcete-li každou položku nakreslit na stejnou velikost `DrawMode` , nastavte <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> vlastnost na a `DrawItem` zpracujte událost.  
  
 Pro vykreslení každé položky pomocí `DrawMode` jiné velikosti nastavte vlastnost na <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> a zpracujte `MeasureItem` události a `DrawItem` . Událost umožňuje určit velikost položky `DrawItem` před tím, než dojde k události pro tuto položku. `MeasureItem`  
  
 Další informace, včetně příkladů kódu, najdete v následujících tématech:  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [Postupy: Vytvoření textu proměnlivé velikosti v ovládacím prvku ComboBox](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>Komponenta MenuItem  
 Komponenta představuje jednu položku nabídky <xref:System.Windows.Forms.MainMenu> v součásti nebo <xref:System.Windows.Forms.ContextMenu>. <xref:System.Windows.Forms.MenuItem>  
  
 Chcete-li <xref:System.Windows.Forms.MenuItem>nakreslit, `OwnerDraw` nastavte jeho `true` vlastnost na a `DrawItem` zpracujte její událost. Chcete-li přizpůsobit velikost položky nabídky před `DrawItem` výskytem události, zpracujte `MeasureItem` událost položky.  
  
 Další informace, včetně příkladů kódu, najdete v následujících referenčních tématech:  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl – ovládací prvek  
 <xref:System.Windows.Forms.TabControl> Ovládací prvek umožňuje kreslit jednotlivé karty v ovládacím prvku. Vlastní kresba má vliv pouze na karty; <xref:System.Windows.Forms.TabPage> obsah není ovlivněn.  
  
 Chcete-li nakreslit každou <xref:System.Windows.Forms.TabControl>kartu v, `DrawMode` nastavte `DrawItem` vlastnost <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> na a zpracujte událost. Tato událost nastane jednou pro každou kartu pouze v případě, že je karta viditelná v ovládacím prvku.  
  
 Další informace, včetně příkladů kódu, najdete v následujících referenčních tématech:  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip – komponenta  
 <xref:System.Windows.Forms.ToolTip> Komponenta umožňuje při zobrazení zobrazit celý popis tlačítka.  
  
 Chcete-li <xref:System.Windows.Forms.ToolTip>nakreslit, `OwnerDraw` nastavte jeho `true` vlastnost na a `Draw` zpracujte její událost. Chcete-li přizpůsobit <xref:System.Windows.Forms.ToolTip> velikost, `Draw` než dojde k `Popup` události, zpracujte událost a nastavte <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> vlastnost v obslužné rutině události.  
  
 Další informace, včetně příkladů kódu, najdete v následujících referenčních tématech:  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView – ovládací prvek  
 <xref:System.Windows.Forms.ListView> Ovládací prvek umožňuje v ovládacím prvku nakreslit jednotlivé položky, podpoložky a záhlaví sloupců.  
  
 Chcete-li povolit vykreslování vlastníka v ovládacím prvku, `OwnerDraw` nastavte vlastnost `true`na hodnotu.  
  
 Chcete-li nakreslit každou položku v ovládacím prvku `DrawItem` , zpracujte událost.  
  
 Chcete-li v ovládacím prvku nakreslit jednotlivá záhlaví podpoložky nebo <xref:System.Windows.Forms.ListView.View%2A> sloupce, když je <xref:System.Windows.Forms.View.Details>vlastnost nastavena na `DrawSubItem` , `DrawColumnHeader` zpracujte události a.  
  
 Další informace, včetně příkladů kódu, najdete v následujících referenčních tématech:  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView – ovládací prvek  
 <xref:System.Windows.Forms.TreeView> Ovládací prvek umožňuje kreslit jednotlivé uzly v ovládacím prvku.  
  
 Chcete-li nakreslit pouze text zobrazený v každém uzlu `DrawMode` , nastavte <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> vlastnost na a `DrawNode` zpracujte událost pro vykreslení textu.  
  
 Chcete-li nakreslit všechny prvky každého uzlu, `DrawMode` nastavte vlastnost <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> na a zpracujte `DrawNode` událost pro vykreslení všech potřebných prvků, jako jsou text, ikony, zaškrtávací políčka, znaménka plus a mínus a čáry připojující uzly.  
  
 Další informace, včetně příkladů kódu, najdete v následujících referenčních tématech:  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView – ovládací prvek  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek umožňuje kreslit jednotlivé buňky a řádky v ovládacím prvku.  
  
 Chcete-li nakreslit jednotlivé buňky `CellPainting` , zpracujte událost.  
  
 Chcete-li nakreslit jednotlivé řádky nebo prvky řádků, zpracujte jednu nebo obě `RowPrePaint` události `RowPostPaint` a. K události dojde před vykreslením buněk v řádku `RowPostPaint` a událost nastane po vykreslení buněk. `RowPrePaint` Můžete zpracovávat obě události a `CellPainting` událost pro malování pozadí řádku, jednotlivé buňky a popředí řádku samostatně nebo můžete zadat konkrétní vlastní nastavení, kde je potřebujete, a použít výchozí zobrazení pro jiné prvky řádku.  
  
 Další informace, včetně příkladů kódu, najdete v následujících tématech:  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku DataGridView model Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku DataGridView model Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip – ovládací prvek  
 <xref:System.Windows.Forms.ToolStrip>a odvozené ovládací prvky umožňují přizpůsobit libovolný aspekt jejich vzhledu.  
  
 Chcete-li poskytnout vlastní <xref:System.Windows.Forms.ToolStrip> vykreslování pro ovládací prvky `Renderer` , nastavte <xref:System.Windows.Forms.ToolStripPanel>vlastnost <xref:System.Windows.Forms.ToolStrip> `ToolStripRenderer` objektu <xref:System.Windows.Forms.ToolStripManager>,, nebo <xref:System.Windows.Forms.ToolStripContentPanel> na objekt a zpracujte jednu nebo více mnoha událostí kreslení poskytovaných `ToolStripRenderer` třída. Případně můžete `Renderer` nastavit vlastnost na instanci vaší vlastní třídy odvozené z `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>nebo <xref:System.Windows.Forms.ToolStripSystemRenderer> , která implementuje nebo Přepisuje konkrétní `On`metody *EventName* .  
  
 Další informace, včetně příkladů kódu, najdete v následujících tématech:  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [Postupy: Vytvoření a nastavení vlastního zobrazovací jednotky pro ovládací prvek ToolStrip v model Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [Postupy: Vlastní vykreslení ovládacího prvku ToolStrip](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
