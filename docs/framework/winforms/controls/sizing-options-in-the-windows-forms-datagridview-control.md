---
title: Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
ms.openlocfilehash: 2f76bbca3d4b6e642c0eec2129c4a2abee752655
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197838"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> řádky, sloupce a záhlaví můžete změnit velikost v důsledku mnoho různých výskytů. V následující tabulce jsou uvedeny těchto událostech.  
  
|Výskyt|Popis|  
|----------------|-----------------|  
|Změna velikosti uživatele|Přetažení nebo poklepání oddělovače řádků, sloupců nebo záhlaví mohou uživatelé provádět úpravy velikosti.|  
|Změna velikosti ovládacího prvku|V režim vyplnění sloupce změnit šířku sloupců při změně šířku ovládacího prvku; například, když je ovládací prvek ukotven k jeho nadřazený formulář a uživatel změní velikost formuláře.|  
|Změnu hodnoty buňky|V režim automatické velikosti podle obsahu změnit velikosti podle nové hodnoty zobrazení.|  
|Volání metody|Změna velikosti programový založené na obsahu umožňuje provádět úpravy příležitostné velikost založené na hodnotách v buňkách v okamžiku volání metody.|  
|Nastavení vlastnosti|Můžete také nastavit konkrétní výšku a šířku hodnoty.|  
  
 Ve výchozím nastavení Změna velikosti uživatele je povoleno, je zakázáno automatické velikosti a hodnotách v buňkách, které jsou větší než jejich sloupce se oříznou.  
  
 Následující tabulka uvádí scénáře, které můžete upravit výchozí chování nebo použít konkrétní nastavení velikosti možností k dosažení určitého účinky.  
  
|Scénář|Implementace|  
|--------------|--------------------|  
|Režim vyplnění sloupce použijte pro zobrazení podobně velikost dat v relativně malý počet sloupců, které zabírají celou šířku ovládacího prvku bez zobrazení vodorovného posuvníku.|Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>.|  
|Režim vyplnění sloupce použijte s zobrazit hodnoty různých velikostí.|Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Inicializovat šířku sloupců relativní nastavením sloupci <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> vlastnosti nebo pomocí volání ovládacího prvku <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metoda po naplnění ovládacího prvku s daty.|  
|Použijte režim vyplnění sloupce s hodnotami různých význam.|Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Nastavte velké <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnoty pro sloupce, které musí vždy zobrazila některá data nebo použít možnost Změna velikosti jiných než vyplnit režim pro konkrétní sloupce.|  
|Chcete-li zabránit zobrazování na pozadí ovládacího prvku použijte režim vyplnění sloupce.|Nastavte <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnost posledního sloupce na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> a použít jiné možnosti nastavení velikosti pro ostatní sloupce. Pokud další sloupce, které používají příliš mnoho místa, nastavte <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> vlastnost posledního sloupce.|  
|Zobrazte sloupec pevnou šířkou, jako je například ikony nebo ID sloupce.|Nastavte <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> k <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> a <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> k <xref:System.Windows.Forms.DataGridViewTriState.False> pro sloupec. Inicializovat jeho šířku tak, že nastavíte <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> vlastnost nebo voláním ovládací prvek <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> metoda po naplnění ovládacího prvku s daty.|  
|Upravte velikost automaticky při každé změně obsahu buňky nedošlo k oříznutí a optimalizovat využití místa.|Nastavte automatické velikosti vlastnost na hodnotu, která představuje režim určení velikosti na základě obsahu. Aby se zabránilo snížení výkonu při práci s velkými objemy dat, použijte nastavení velikosti režimu, který vypočítá pouze zobrazené řádky.|  
|Úprava velikosti podle hodnoty v zobrazené řádky, aby se zabránilo snížení výkonu při práci s více řádků.|Pomocí automatické nebo Programová změna velikosti hodnot výčtu příslušný režim velikosti. Chcete-li upravit velikosti podle hodnoty v nově zobrazených řádků při posouvání, zavolejte metodu změny velikosti v <xref:System.Windows.Forms.DataGridView.Scroll> obslužné rutiny události. Přizpůsobení uživatel dvakrát klikněte na změně velikosti tak, aby pouze hodnoty v zobrazených řádků určují nové velikosti volání změny velikosti metody <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> nebo <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> obslužné rutiny události.|  
|Úprava velikosti podle obsahu buňky pouze v určitých časech, aby se zabránilo snížení výkonu nebo umožňující změnu velikosti uživatele.|Volání metody změny velikosti podle obsahu v obslužné rutině události. Například použít <xref:System.Windows.Forms.DataGridView.DataBindingComplete> událostí k inicializaci velikosti po vytvoření vazby a zpracovat <xref:System.Windows.Forms.DataGridView.CellValidated> nebo <xref:System.Windows.Forms.DataGridView.CellValueChanged> událostí k úpravě velikosti jako kompenzaci za uživatelské úpravy nebo změny ve zdroji vazby dat.|  
|Upravte výšku víceřádkové buňky.|Zajistěte, aby byly vhodné pro zobrazování textu odstavců šířku sloupců a použijte nastavení velikosti automatické nebo programově podle obsahu řádku k úpravě výšky. Také se ujistěte, že se zobrazují buňky s víceřádkové obsah pomocí <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> buňka hodnotu stylu <xref:System.Windows.Forms.DataGridViewTriState.True>.<br /><br /> Obvykle použijete určení velikosti režim automatické sloupce udržovat šířku sloupců nebo je nastavit na konkrétní šířky předtím, než jsou upraveny výšku řádků.|  
  
## <a name="resizing-with-the-mouse"></a>Změna velikosti pomocí myši  
 Ve výchozím nastavení můžou uživatelé měnit velikost řádky, sloupce a záhlaví, které nepoužívají režim automatické velikosti založené na hodnotách v buňkách. Pokud chcete uživatelům zabránit ve změně velikosti pomocí jiné režimy, jako je režim vyplnění sloupce nastavit jeden nebo více z následujících <xref:System.Windows.Forms.DataGridView> vlastnosti:  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Můžete také zabránit uživatelům v Změna velikosti jednotlivých řádků nebo sloupců tak, že nastavíte jejich <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> vlastnosti. Ve výchozím nastavení <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> podle hodnoty vlastnosti <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> hodnota vlastnosti pro sloupce a <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> hodnota vlastnosti pro řádky. Pokud je výslovně nastavit <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> k <xref:System.Windows.Forms.DataGridViewTriState.True> nebo <xref:System.Windows.Forms.DataGridViewTriState.False>, ale přepsání zadaná hodnota je hodnota ovládacího prvku pro řádek nebo sloupec. Nastavte <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> k <xref:System.Windows.Forms.DataGridViewTriState.NotSet> obnovit dědičnosti.  
  
 Protože <xref:System.Windows.Forms.DataGridViewTriState.NotSet> obnoví dědičnost hodnoty <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> nikdy vrátí vlastnosti <xref:System.Windows.Forms.DataGridViewTriState.NotSet> hodnotu, pokud řádek nebo sloupec nebyl přidán do <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pokud je potřeba určit, zda <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> je zděděná hodnota vlastnosti řádku nebo sloupce, zkontrolujte jeho <xref:System.Windows.Forms.DataGridViewElement.State%2A> vlastnost. Pokud <xref:System.Windows.Forms.DataGridViewElement.State%2A> obsahuje hodnotu <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> příznak <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> hodnota vlastnosti není zděděno.  
  
## <a name="automatic-sizing"></a>Automatické nastavení velikosti  
 Existují dva druhy automatické velikosti v <xref:System.Windows.Forms.DataGridView> ovládacího prvku: režim vyplnění sloupce a automatické velikosti podle obsahu.  
  
 Režim vyplnění sloupce způsobí, že viditelných sloupců v ovládacím prvku celou šířku zobrazované oblasti ovládacího prvku. Další informace o tomto režimu najdete v tématu [režim vyplnění sloupce v ovládacím prvku Windows Forms DataGridView](column-fill-mode-in-the-windows-forms-datagridview-control.md).  
  
 Můžete také nakonfigurovat řádky, sloupce a záhlaví má automaticky upravovat jejich velikosti podle jejich obsah buňky. V takovém případě úpravu velikosti vyvolá se při každé změně obsahu buňky.  
  
> [!NOTE]
>  Pokud chcete zachovat hodnoty buněk do vlastní datové mezipaměti pomocí virtuální režim, automatické velikosti nastane, pokud uživatel upraví hodnotu buňky, ale nenastane při změně hodnotu uloženou v mezipaměti mimo <xref:System.Windows.Forms.DataGridView.CellValuePushed> obslužné rutiny události. V takovém případě volat <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> metody pro vynucení aktualizace buňky zobrazíte a použít aktuální režim automatické velikosti ovládacího prvku.  
  
 Pokud je povoleno automatické velikosti podle obsahu pouze jednu dimenzi –, který je pro řádky, ale ne sloupců a sloupců, ale není řádky, – a <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> je také povolena, velikost také dojde k úpravě pokaždé, když se změní dimenzi. Například, pokud řádků, ale ne sloupce jsou nakonfigurované pro automatické velikosti a <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> je povolená, uživatelé můžete přetáhnout oddělovače sloupců změnit šířku sloupce a výšku řádků automaticky upraví tak, že obsah buňky jsou stále plně zobrazeny.  
  
 Pokud nakonfigurujete řádky a sloupce pro automatické velikosti podle obsahu a <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> je povoleno, <xref:System.Windows.Forms.DataGridView> ovládací prvek upraví velikostí pokaždé, když se obsah buňky změnit a používat ideální buňky poměr výšky a šířky při výpočtu nové velikosti.  
  
 Pokud chcete nakonfigurovat režim změny velikosti pro záhlaví řádků a sloupců, které nepřepisují hodnoty ovládacího prvku, nastavte jeden nebo více z následujících <xref:System.Windows.Forms.DataGridView> vlastnosti:  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Chcete-li změnit režim velikosti ovládacího prvku sloupec pro jednotlivé sloupce, nastavte jeho <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnost na hodnotu jinou než <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>. Režim změny velikosti pro sloupec je ve skutečnosti dáno jeho <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> vlastnost. Hodnota této vlastnosti je založena na sloupce <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> hodnota vlastnosti, pokud je tato hodnota <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>v takovém případě ovládacího prvku <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> je zděděná hodnota.  
  
 Použití založené na obsahu automatickou změnu velikosti buďte opatrní při práci s velkými objemy dat. Aby se zabránilo snížení výkonu, použijte automatické velikosti režimy výpočet velikosti pouze podle zobrazených řádků než analýza všechny řádky v ovládacím prvku. Pro maximální výkon je načten použití Programová změna velikosti místo tak, aby velikost můžete měnit v určitých časech, jako například ihned po nová data.  
  
 Režim automatické velikosti podle obsahu nemají vliv na řádky, sloupce nebo hlavičky, které jsou skryté tak, že nastavíte řádku nebo sloupce <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> vlastnosti nebo ovládací prvek <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> nebo <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> vlastností `false`. Například pokud je sloupec skryt po je automaticky velikosti podle hodnoty velké buňky, skrytý sloupec nedojde ke změně jeho velikost je-li odstranit řádek, který obsahuje velké její hodnotu. Automatické velikosti nedojde, pokud se změní viditelnost, takže změna sloupce <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> vlastnost zpět do `true` nebude vynutit přepočítat její velikost na základě své aktuální obsahu.  
  
 Změna velikosti programový založené na obsahu má vliv na řádky, sloupce a záhlaví bez ohledu na jejich viditelnost.  
  
## <a name="programmatic-resizing"></a>Programová změna velikosti  
 Pokud je zakázáno automatické velikosti, můžete prostřednictvím kódu programu nastavit přesné šířku nebo výšku řádků, sloupců nebo záhlaví prostřednictvím následující vlastnosti:  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 Můžete také programově změnit velikost řádky, sloupce a záhlaví podle jejich obsahu pomocí následujících metod:  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 Tyto metody změní velikost řádků, sloupců, nebo záhlaví jednou, spíše než jejich konfiguraci pro průběžné změny velikosti. Chcete-li zobrazit veškerý obsah buňky bez oříznutí automaticky vypočteny nové velikosti. Když změníte velikost programově sloupce, které obsahují <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> hodnoty vlastností <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>, ale počítané šířky založené na obsahu umožňují sloupci proporcionálně upravit <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty vlastností a šířka sloupců ve skutečnosti pak vypočítá podle těchto nových proporce tak, aby všechny sloupce vyplnění oblasti k dispozici zobrazení ovládacího prvku.  
  
 Programová změna velikosti je užitečné, aby se zabránilo snížení výkonu s průběžné změny velikosti. Je také užitečné poskytnout počáteční velikosti umožňující změnu velikosti uživatele řádky, sloupce a záhlaví a režim vyplnění sloupce.  
  
 Bude obvykle volat metody programové změny velikosti v určitých časech. Například může programově změnit velikost všech sloupců bezprostředně po načtení dat nebo vám může prostřednictvím kódu programu změně velikosti konkrétní řádek po hodnoty konkrétní buňky se změnila.  
  
## <a name="customizing-content-based-sizing-behavior"></a>Přizpůsobení chování určení velikosti na základě obsahu  
 Můžete přizpůsobit chování velikosti při práci s odvozené <xref:System.Windows.Forms.DataGridView> buněk, řádků a sloupců typy tak, že přepíšete <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>, nebo <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> metody nebo voláním chráněné změny velikosti přetížení metody v odvozené <xref:System.Windows.Forms.DataGridView> ovládací prvek. Chráněné změny velikosti přetížení metody jsou navrženy pro práci v párech dosáhnout poměr výšky a šířky ideální buněk, jak se vyhnout příliš široké nebo výška buňky. Například, pokud zavoláte `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` přetížení <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> metoda a předejte jí hodnotu `false` pro <xref:System.Boolean> parametr přetížení se vypočítat ideální výšku a šířku pro buňky v řádku, ale upraví výšku řádků pouze. Musíte pak zavolat <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metoda šířku sloupců pro počítané ideální.  
  
## <a name="content-based-sizing-options"></a>Možnosti nastavení velikosti podle obsahu  
 Výčty používané velikosti vlastnosti a metody mají podobné hodnoty pro určení velikosti na základě obsahu. S těmito hodnotami můžete omezit buněk, které se používají k výpočtu velikosti upřednostňované. Pro všechny velikosti výčty hodnot s názvy, které odkazují na zobrazených buněk omezit jejich výpočtů do buněk v zobrazených řádků. Vyloučení řádků je užitečné, aby se zabránilo snížení výkonu při práci s velké množství řádků. Můžete taky omezit výpočty na hodnotách v buňkách v záhlaví nebo nonheader buňky.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Režim vyplnění sloupce v ovládacím prvku Windows Forms DataGridView](column-fill-mode-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
