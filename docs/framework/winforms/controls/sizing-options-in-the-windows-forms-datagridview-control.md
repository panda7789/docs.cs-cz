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
ms.openlocfilehash: 6e3a7786970ef536da4ef7628cd33ae067ba90be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> velikost v důsledku mnoho různých výskytů můžete změnit řádky, sloupce a hlavičky. V následující tabulce jsou tyto události.  
  
|Výskyt|Popis|  
|----------------|-----------------|  
|Uživatelské změny velikosti|Mohou uživatelé provádět úpravy velikosti přetažením nebo dvakrát kliknete na soubor oddělovače řádků, sloupců nebo hlavičce.|  
|Změna velikosti ovládacího prvku|V režim vyplnění sloupce šířku sloupců změnit, když se změní šířku řízení; například když ovládacího prvku ukotveno jeho nadřazeného formuláře a uživatel změní velikost formuláře.|  
|Změna hodnoty buňky|V režimech na základě obsahu Automatická změna velikosti velikosti změnit podle nové hodnoty zobrazení.|  
|Volání metody|Změna velikosti programový na základě obsahu umožňuje provádět úpravy oportunistické velikost podle hodnot v buňkách při volání metody.|  
|Nastavení vlastnosti|Můžete také nastavit určité výšky a šířky hodnoty.|  
  
 Ve výchozím nastavení Změna velikosti uživatele je povoleno, je zakázán Automatická změna velikosti a jsou oříznut hodnoty buněk, které jsou širší než jejich sloupce.  
  
 Následující tabulka uvádí scénáře, které můžete upravit výchozí chování, nebo chcete použít konkrétní nastavení velikosti možností k dosažení konkrétní účinky.  
  
|Scénář|Implementace|  
|--------------|--------------------|  
|Režim vyplnění sloupce použijte pro zobrazení podobně velikost dat v relativně malý počet sloupců, které zabírají celou šířku ovládacího prvku bez zobrazení vodorovného posuvníku.|Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>.|  
|Použijte režim vyplnění sloupce s zobrazení hodnot různou velikost.|Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Inicializace šířky relativní sloupců nastavením sloupec <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> vlastnosti nebo voláním ovládacího prvku <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metoda po vyplnění ovládacího prvku s daty.|  
|Použijte režim vyplnění sloupce s hodnotami různých význam.|Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Nastavit velké <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnoty pro sloupce, které musí vždy zobrazují některé svých dat nebo použít možnost nastavení velikosti jiné než vyplnění režim pro určité sloupce.|  
|Použijte režim vyplnění sloupce zamezení zobrazení na pozadí ovládacího prvku.|Nastavte <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnost posledního sloupce, který se <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> a použít jiné nastavení velikosti možností pro jiné sloupce. Pokud ostatních sloupců použít příliš mnoho prostoru, nastavte <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> vlastnost posledního sloupce.|  
|Zobrazte sloupec pevnou šířkou, jako je například ikony nebo ID sloupce.|Nastavit <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> k <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> a <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> k <xref:System.Windows.Forms.DataGridViewTriState.False> pro sloupec. Inicializace šířku nastavením <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> vlastnost nebo voláním ovládacího prvku <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> metoda po vyplnění ovládacího prvku s daty.|  
|Upravte velikosti automaticky vždy, když obsah buňky změnit, aby se zabránilo výstřižek a k optimalizaci využití místa.|Nastavte vlastnost Automatická změna velikosti na hodnotu, která představuje režim pro změnu velikosti podle obsahu. Aby se zabránilo snížení výkonu při práci s velkými objemy dat, používejte režim nastavení velikosti, která by vypočítala pouze zobrazených řádků.|  
|Upravte velikosti podle hodnot v zobrazených řádků, aby nedošlo k penalizaci výkon při práci s mnoho řádků.|Použijte hodnoty výčtu odpovídající velikosti režimu s automatickou nebo Programová změna velikosti. Upravit velikosti podle hodnot v nově zobrazených řádků při posouvání, volat metodu změny velikosti <xref:System.Windows.Forms.DataGridView.Scroll> obslužné rutiny události. Chcete-li přizpůsobit poklikejte na soubor uživatele Změna velikosti, aby pouze hodnoty v zobrazených řádků určit nové velikosti volání změny velikosti metody <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> nebo <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> obslužné rutiny události.|  
|Upravte velikosti podle obsahu buňky pouze v určitých časech, aby nedošlo k penalizaci výkonu nebo umožňující změnu velikosti uživatele.|Volání metody změny velikosti podle obsahu v obslužné rutině události. Například použít <xref:System.Windows.Forms.DataGridView.DataBindingComplete> událostí k inicializaci velikosti po vytvoření vazby a zpracovat <xref:System.Windows.Forms.DataGridView.CellValidated> nebo <xref:System.Windows.Forms.DataGridView.CellValueChanged> událostí upravit velikost se pohybuje kompenzovat uživatelské úpravy nebo změny v vázaný datový zdroj.|  
|Přizpůsobit výšku obsah Víceřádkový buňky.|Zkontrolujte, zda jsou vhodné pro zobrazení odstavců textu šířku sloupců a k nastavení výšky použijte nastavení velikosti automatický nebo programové řádku na základě obsahu. Ujistěte se také zobrazení buněk pomocí víceřádkovým obsah pomocí <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> buňky styl hodnotu <xref:System.Windows.Forms.DataGridViewTriState.True>.<br /><br /> Obvykle použijete nastavení velikosti režim automatického sloupce zachovat šířku sloupců nebo je nastavena na konkrétní šířky předtím, než jsou upraveny výšky řádků.|  
  
## <a name="resizing-with-the-mouse"></a>Změna velikosti pomocí myši  
 Ve výchozím nastavení uživatelé mohou změnit řádky, sloupce a hlavičky, které nepoužívají režimu Automatická změna velikosti na základě hodnot v buňkách. Uživatelům zabránit v Změna velikosti s další režimy, jako je například režim vyplnění sloupce, nastavte jeden nebo více z následujících <xref:System.Windows.Forms.DataGridView> vlastnosti:  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Můžete také může zabránit uživatelům v Změna velikosti jednotlivých řádků nebo sloupce nastavením jejich <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> vlastnosti. Ve výchozím nastavení <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> hodnota vlastnosti je založena na <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> hodnota vlastnosti pro sloupce a <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> hodnota vlastnosti pro řádky. Pokud jste nastavili <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> k <xref:System.Windows.Forms.DataGridViewTriState.True> nebo <xref:System.Windows.Forms.DataGridViewTriState.False>, ale zadaná hodnota přepsání ovládací prvek pro hodnotu tohoto sloupce či řádku. Nastavit <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> k <xref:System.Windows.Forms.DataGridViewTriState.NotSet> obnovit dědičnosti.  
  
 Protože <xref:System.Windows.Forms.DataGridViewTriState.NotSet> obnoví dědičnosti hodnotu <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> vlastnost nikdy vrátí <xref:System.Windows.Forms.DataGridViewTriState.NotSet> hodnotu, pokud sloupce či řádku nebyl přidán do <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pokud je potřeba určit, zda <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> je zděděná hodnota vlastnosti sloupce či řádku, zkontrolujte jeho <xref:System.Windows.Forms.DataGridViewElement.State%2A> vlastnost. Pokud <xref:System.Windows.Forms.DataGridViewElement.State%2A> hodnota zahrnuje <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> příznak <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> není zděděná hodnota vlastnosti.  
  
## <a name="automatic-sizing"></a>Automatická změna velikosti  
 Existují dva druhy Automatická změna velikosti v <xref:System.Windows.Forms.DataGridView> ovládacího prvku: režim vyplnění sloupce a na základě obsahu Automatická změna velikosti.  
  
 Režim vyplnění sloupce způsobí, že zobrazených sloupců v ovládacím prvku celou šířku oblasti zobrazení ovládacího prvku. Další informace o tomto režimu najdete v tématu [režim vyplnění sloupce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md).  
  
 Můžete také nakonfigurovat řádky, sloupce a hlavičky automaticky nastavit jejich velikosti podle obsahu jejich buňky. V takovém případě úpravu velikosti dochází při každé změně obsah buňky.  
  
> [!NOTE]
>  Pokud chcete zachovat hodnoty buněk do mezipaměti vlastních dat pomocí virtuální režim, automatická změna velikosti nastane, když uživatel upravuje hodnoty buňky, ale při změnit hodnotu uloženou v mezipaměti mimo nedojde <xref:System.Windows.Forms.DataGridView.CellValuePushed> obslužné rutiny události. V takovém případě volání <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> metoda vynutit aktualizaci buňku zobrazení a použití aktuální režimy Automatická změna velikosti ovládacího prvku.  
  
 Pokud je na základě obsahu Automatická změna velikosti pouze jednu dimenzi – které je u řádků, ale není sloupce, nebo u sloupců, ale není řádků – a <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> je také povoleno, velikost úpravu také dochází při každé změně další dimenze. Například pokud řádky ale není sloupce jsou nakonfigurované pro automatická změna velikosti a <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> je povoleno, uživatelé můžete přetáhnout oddělovače sloupců změnit šířku sloupce a výšky řádků automaticky upraví tak, aby se stále plně zobrazí obsah buňky.  
  
 Pokud nakonfigurujete řádků a sloupců pro založená na obsahu Automatická změna velikosti a <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> je povoleno, <xref:System.Windows.Forms.DataGridView> řízení upraví velikosti vždy, když obsah buňky změnit a použije poměr výšky a šířky ideální buňky při výpočtu nové velikosti.  
  
 Ke konfiguraci režimu nastavení velikosti pro hlavičky a řádky a sloupce, které nepřepisují hodnota ovládacího prvku, nastavte jeden nebo více z následujících <xref:System.Windows.Forms.DataGridView> vlastnosti:  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Chcete-li přepsat režim nastavení velikosti sloupce ovládacího prvku pro jednotlivé sloupce, nastavte jeho <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnost na hodnotu jinou než <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>. Nastavení velikosti režimu pro sloupec je ve skutečnosti dáno jeho <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> vlastnost. Hodnota této vlastnosti je založena na sloupce <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> hodnota vlastnosti není-li tuto hodnotu <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>, v takovém případě ovládacího prvku <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> je zděděná hodnota.  
  
 Použijte na základě obsahu Automatická změna velikosti opatrně při práci s velkými objemy dat. Aby nedošlo k penalizaci výkonu, použijte automatická změna velikosti režimy, které výpočtu velikosti pouze podle zobrazených řádků než analýza každý řádek v ovládacím prvku. Pro maximální výkon je použití Programová změna velikosti místo toho, aby velikost lze změnit v určitých časech, jako například ihned po nová data načtena.  
  
 Na základě obsahu Automatická změna velikosti režimy neovlivní řádků, sloupců nebo hlavičky, které jsou skryté nastavením sloupce či řádku <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> vlastnost nebo ovládací prvek <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> nebo <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> vlastnosti, které chcete `false`. Například pokud je sloupec skryt po je automaticky velikost podle hodnoty velký buňky, skrytý sloupec nedojde ke změně jeho velikost Pokud byl odstraněn řádek obsahující hodnotu velké buňky. Automatická změna velikosti nedojde, když se změní viditelnost, takže změna sloupec <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> vlastnost zpět do `true` nebude vynutit, aby přepočítat jeho velikost na základě jeho aktuální obsahu.  
  
 Změna velikosti programový na základě obsahu ovlivňuje řádky, sloupce a hlavičky bez ohledu na jejich přehled.  
  
## <a name="programmatic-resizing"></a>Programová změna velikosti  
 Pokud je automatická změna velikosti zakázaná, můžete nastavit prostřednictvím kódu programu přesný šířky nebo výšky řádků, sloupců nebo hlavičky prostřednictvím následujících vlastností:  
  
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
  
 Tyto metody změníte velikost řádky, sloupce, nebo hlavičky jednou spíše než jejich konfigurací pro nepřetržitou změnu velikosti. Chcete-li zobrazit všechny obsah buňky bez výstřižek automaticky vypočteny nové velikosti. Když změníte velikost prostřednictvím kódu programu sloupce, které mají <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> hodnot vlastností <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>, ale počítané šířky na základě obsahu používají úměrně upravit sloupec <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty vlastnosti a jsou šířky sloupec ve skutečnosti potom vypočítává podle tyto nové proporce tak, že všechny sloupce vložit oblasti k dispozici zobrazení ovládacího prvku.  
  
 Programová změna velikosti je užitečné, aby nedošlo k penalizaci výkonu s průběžné změny velikosti. Je také užitečné k zajištění počáteční velikosti pro s možností změny velikosti uživatele řádky, sloupce a hlavičky a pro režim vyplnění sloupce.  
  
 Obvykle budete volat metodu programové změny velikosti v určitých časech v. Například může prostřednictvím kódu programu přizpůsobit všechny sloupce bezprostředně po načtení dat nebo prostřednictvím kódu programu může přizpůsobit specifickým řádkem po hodnotu konkrétní buňky byl změněn.  
  
## <a name="customizing-content-based-sizing-behavior"></a>Nastavení velikosti podle obsahu chování přizpůsobení  
 Můžete upravit nastavení velikosti chování při práci s odvozené <xref:System.Windows.Forms.DataGridView> buněk, řádků a sloupců typy přepsáním <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>, nebo <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> metody nebo voláním chráněných změny velikosti přetížení metody v odvozené <xref:System.Windows.Forms.DataGridView> ovládací prvek. Chráněné změny velikosti přetížení metody jsou navrženy pro práci v párech k dosažení poměr výšky a šířky ideální buňky, zabraňující příliš široké nebo vysoký buněk. Například, pokud zavoláte `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` přetížení z <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> metoda a předejte jí hodnotu `false` pro <xref:System.Boolean> parametr přetížení vypočítá ideální výšku a šířku pro buňky v řádku, ale upraví výšku řádků pouze. Pak musí volat <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metodu pro šířku sloupců pro počítané ideální.  
  
## <a name="content-based-sizing-options"></a>Možnosti nastavení velikosti podle obsahu  
 Výčty používaný pro změnu velikosti vlastnosti a metody mají podobné hodnoty pro nastavení velikosti podle obsahu. S těmito hodnotami můžete omezit buněk, které se použije k výpočtu upřednostňovanou velikost. Pro všechny velikosti výčty hodnot s názvy, které odkazují na zobrazené buňky omezit jejich výpočtů do buněk v zobrazených řádků. S výjimkou řádků je užitečné, aby se zabránilo snížení výkonu, když pracujete s velkého počtu řádků. Můžete taky omezit výpočty pro hodnoty buněk v záhlaví nebo nonheader buněk.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>  
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>  
 [Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 [Režim vyplnění sloupce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
