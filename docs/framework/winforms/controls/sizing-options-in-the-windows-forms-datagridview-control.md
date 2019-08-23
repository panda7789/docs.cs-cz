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
ms.openlocfilehash: a8e2e05877746dfb043b7e8ac2a6c2b7017883c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960426"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView>řádky, sloupce a záhlaví mohou změnit velikost v důsledku mnoha různých výskytů. Následující tabulka uvádí tyto výskyty.  
  
|Výskyt|Popis|  
|----------------|-----------------|  
|Změna velikosti uživatele|Uživatelé mohou provádět úpravy velikosti přetažením nebo Poklikáním na oddělovače řádků, sloupců nebo záhlaví.|  
|Změnit velikost ovládacího prvku|V režimu vyplnění sloupce se Změna šířky sloupce změní, když se změní šířka ovládacího prvku; například když je ovládací prvek ukotven do svého nadřazeného formuláře a uživatel změní velikost formuláře.|  
|Změna hodnoty buňky|V režimech automatického přizpůsobení velikosti založeném na obsahu se změny velikosti přizpůsobí tak, aby odpovídaly novým hodnotám zobrazení.|  
|Volání metody|Programová změna velikosti na základě obsahu umožňuje provádět úpravy příležitostné velikosti na základě hodnot buněk v době volání metody.|  
|Nastavení vlastnosti|Můžete také nastavit konkrétní hodnoty výšky a šířky.|  
  
 Ve výchozím nastavení je povolená Změna velikosti uživatele, automatické určení velikosti je zakázané a hodnoty buněk, které jsou širší než jejich sloupce, se oříznou.  
  
 V následující tabulce jsou uvedeny scénáře, které můžete použít k úpravě výchozího chování nebo k používání specifických možností změny velikosti, abyste dosáhli konkrétních efektů.  
  
|Scénář|Implementace|  
|--------------|--------------------|  
|Režim výplně sloupce slouží k zobrazení dat podobné velikosti v relativně malém počtu sloupců, které zabírají celou šířku ovládacího prvku bez zobrazení vodorovného posuvníku.|Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>.|  
|Použijte režim vyplnění sloupce s hodnotami zobrazení různých velikostí.|Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Proveďte inicializaci relativních šířek sloupců nastavením vlastností sloupce <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> nebo voláním metody Control <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> po vyplnění ovládacího prvku daty.|  
|Použijte režim vyplnění sloupce s hodnotami proměnlivá důležitost.|Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Nastavte velké <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> hodnoty pro sloupce, které musí vždy zobrazovat některá z nich, nebo pro konkrétní sloupce použít jinou možnost změny velikosti než režim výplně.|  
|Použijte režim vyplnění sloupce, abyste se vyhnuli zobrazení pozadí ovládacího prvku.|Nastavte vlastnost posledního sloupce na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> a použijte další možnosti změny velikosti pro ostatní sloupce. <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> Pokud ostatní sloupce používají příliš mnoho dostupného místa, nastavte <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> vlastnost posledního sloupce.|  
|Zobrazí sloupec s pevnou šířkou, jako je například ikona nebo sloupec ID.|Pro sloupec <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> nastavte <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> na a <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A>. <xref:System.Windows.Forms.DataGridViewTriState.False> Inicializujte šířku <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> nastavením vlastnosti nebo voláním metody Control <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> po vyplnění ovládacího prvku daty.|  
|Automaticky upravit velikosti vždy, když se změní obsah buňky, aby nedocházelo k oříznutí a optimalizoval používání prostoru.|Nastavte vlastnost automatické změny velikosti na hodnotu, která představuje režim změny velikosti podle obsahu. Chcete-li se vyhnout snížení výkonu při práci s velkým objemem dat, použijte režim změny velikosti, který vypočítá pouze zobrazené řádky.|  
|Upravte velikosti tak, aby odpovídaly hodnotám zobrazených řádků, aby nedocházelo k postihům na výkon při práci s mnoha řádky.|Použijte odpovídající hodnoty výčtu v režimu změny velikosti s automatickou nebo programovou změnou velikosti. Chcete-li upravit velikosti tak, aby odpovídaly hodnotám v nově zobrazených řádcích při posouvání, <xref:System.Windows.Forms.DataGridView.Scroll> zavolejte metodu změny velikosti v obslužné rutině události. Pro přizpůsobení uživatele dvakrát klikněte na možnost změny velikosti, takže pouze hodnoty v zobrazených řádcích určují nové velikosti, volání metody změny velikosti v <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> obslužné rutině události nebo. <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick>|  
|Upravte velikosti tak, aby odpovídaly obsahu buňky pouze v určitých časech, aby nedocházelo k postihům výkonu nebo aby bylo možné měnit velikost uživatele.|Zavolejte metodu změny velikosti podle obsahu v obslužné rutině události. Například můžete použít <xref:System.Windows.Forms.DataGridView.DataBindingComplete> událost k inicializaci velikosti po vazbě a <xref:System.Windows.Forms.DataGridView.CellValidated> zpracování události nebo <xref:System.Windows.Forms.DataGridView.CellValueChanged> pro úpravu velikostí, aby bylo možné kompenzovat úpravy uživatelů nebo změny ve vázaném zdroji dat.|  
|Upraví výšku řádků pro obsah víceřádkové buňky.|Ujistěte se, zda jsou šířky sloupců vhodné pro zobrazení odstavců textu a pomocí automatického nebo programové velikosti řádků na základě obsahu upravit výšku. Také zajistěte, aby se buňky s víceřádkovým obsahem <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> zobrazovaly pomocí <xref:System.Windows.Forms.DataGridViewTriState.True>hodnoty stylu buňky.<br /><br /> Obvykle použijete automatický režim pro změnu velikosti sloupce pro zachování šířky sloupců nebo jejich nastavení na konkrétní šířku před tím, než se upraví výšky řádků.|  
  
## <a name="resizing-with-the-mouse"></a>Změna velikosti pomocí myši  
 Ve výchozím nastavení mohou uživatelé měnit velikost řádků, sloupců a záhlaví, které nepoužívají režim automatického přizpůsobení velikosti v závislosti na hodnotách buněk. Chcete-li uživatelům zabránit v změně velikosti v jiných režimech, jako je například režim vyplnění sloupce, nastavte jednu nebo <xref:System.Windows.Forms.DataGridView> více následujících vlastností:  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Můžete také zabránit uživatelům v změně velikosti jednotlivých řádků nebo sloupců nastavením jejich <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> vlastností. Ve výchozím nastavení <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> je hodnota vlastnosti založena <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> na hodnotě vlastnosti pro sloupce a na <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> hodnotu vlastnosti pro řádky. Pokud je ale explicitně <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> nastavená <xref:System.Windows.Forms.DataGridViewTriState.False> <xref:System.Windows.Forms.DataGridViewTriState.True> hodnota nebo, přepíše se hodnota ovládacího prvku pro daný řádek nebo sloupec. Nastavte na hodnotu <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> proobnovenídědičnosti.<xref:System.Windows.Forms.DataGridViewTriState.NotSet>  
  
 Vzhledem <xref:System.Windows.Forms.DataGridViewTriState.NotSet> k tomu <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> , že obnoví dědění hodnoty, <xref:System.Windows.Forms.DataGridViewTriState.NotSet> vlastnost nikdy nevrátí hodnotu, pokud nebyl řádek <xref:System.Windows.Forms.DataGridView> nebo sloupec přidán do ovládacího prvku. Pokud potřebujete zjistit, jestli <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> je hodnota vlastnosti řádku nebo sloupce zděděná, zkontrolujte její <xref:System.Windows.Forms.DataGridViewElement.State%2A> vlastnost. Pokud hodnota obsahuje příznak, <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> hodnota vlastnosti nebude zděděna. <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> <xref:System.Windows.Forms.DataGridViewElement.State%2A>  
  
## <a name="automatic-sizing"></a>Automatické určení velikosti  
 Existují dva typy automatického přizpůsobení velikosti v <xref:System.Windows.Forms.DataGridView> ovládacím prvku: režim výplně sloupce a Automatická změna velikosti na základě obsahu.  
  
 Režim výplně sloupce způsobí, že viditelné sloupce v ovládacím prvku budou plnit šířku oblasti zobrazení ovládacího prvku. Další informace o tomto režimu naleznete v tématu [režim vyplnění sloupce v ovládacím prvku DataGridView model Windows Forms](column-fill-mode-in-the-windows-forms-datagridview-control.md).  
  
 Můžete také nakonfigurovat řádky, sloupce a záhlaví a automaticky tak upravit jejich velikosti tak, aby odpovídaly obsahu buněk. V takovém případě se k úpravě velikosti dojde vždy, když se změní obsah buňky.  
  
> [!NOTE]
> Pokud udržujete hodnoty buněk ve vlastní mezipaměti dat pomocí virtuálního režimu, automatické určení velikosti dojde, když uživatel upraví hodnotu buňky, ale nestane se při změně hodnoty uložené v mezipaměti mimo <xref:System.Windows.Forms.DataGridView.CellValuePushed> obslužnou rutinu události. V tomto případě voláním <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> metody vynuťte, aby ovládací prvek aktualizoval zobrazení buňky a použili aktuální automatické režimy velikosti.  
  
 Pokud je Automatická velikost na základě obsahu povolena pouze pro jednu dimenzi – to znamená pro řádky, nikoli pro sloupce nebo pro sloupce, ale ne pro řádky – <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> a je také povoleno, k úpravě velikosti dojde také při každé změně dimenze. Například pokud jsou řádky, ale ne sloupce nakonfigurované pro automatické změny velikosti <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> a jsou povolené, můžou uživatelé přetahovat oddělovače sloupců, aby se změnila šířka sloupce a výšky řádků se automaticky upraví tak, aby se obsah buněk pořád plně zobrazoval.  
  
 Pokud nakonfigurujete řádky a sloupce pro automatické přizpůsobení velikosti založené na obsahu <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> a je povolený <xref:System.Windows.Forms.DataGridView> , bude ovládací prvek měnit velikosti vždy, když se změní obsah buňky, a při výpočtu nových velikostí použije ideální poměr výšky buňky na šířku.  
  
 Chcete-li konfigurovat režim změny velikosti pro záhlaví a řádky a pro sloupce, které nepřepisují hodnotu ovládacího prvku, nastavte jednu nebo více <xref:System.Windows.Forms.DataGridView> následujících vlastností:  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Chcete-li přepsat režim změny velikosti sloupce ovládacího prvku pro jednotlivý sloupec, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> nastavte jeho vlastnost na jinou hodnotu <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>než. Režim změny velikosti pro sloupec je ve skutečnosti určen <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> vlastností. Hodnota této vlastnosti je založena na hodnotě <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnosti sloupce, pokud se nejedná <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>o hodnotu, v takovém případě je děděna <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> hodnota ovládacího prvku.  
  
 Používejte automatickou změnu velikosti založenou na obsahu s opatrností při práci s velkým objemem dat. Aby nedošlo k analýze každého řádku ovládacího prvku, použijte režimy automatického navýšení velikosti, které vypočítávají velikosti pouze na zobrazených řádcích, aby nedocházelo k postihům výkonu. Pro maximální výkon použijte programové změny velikosti, abyste mohli měnit velikost v určitých časech, například hned po načtení nových dat.  
  
 Režimy automatického přizpůsobení velikosti na základě obsahu neovlivňují řádky, sloupce nebo hlavičky, které jste skryli nastavením <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> vlastnosti řádku nebo sloupce nebo ovládacího prvku <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> nebo <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> vlastností na `false`. Pokud je sloupec například skrytý po jeho automatickém rozměru tak, aby odpovídal velké hodnotě buňky, skrytý sloupec nebude měnit jeho velikost, pokud je odstraněn řádek obsahující hodnotu velké buňky. Automatická změna velikosti se neprojeví, když se změní viditelnost, <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> takže změna vlastnosti `true` sloupce zpět na na základě aktuálního obsahu nezpůsobí přepočítání velikosti.  
  
 Programové změny velikosti na základě obsahu ovlivňují řádky, sloupce a záhlaví bez ohledu na jejich viditelnost.  
  
## <a name="programmatic-resizing"></a>Programové změny velikosti  
 Pokud je automatické určení velikosti zakázané, můžete programově nastavit přesnou šířku nebo výšku řádků, sloupců nebo hlaviček pomocí následujících vlastností:  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 Můžete také programově změnit velikost řádků, sloupců a hlaviček tak, aby odpovídaly jejich obsahu, a to pomocí následujících metod:  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 Tyto metody změní velikost řádků, sloupců nebo hlaviček místo toho, aby je nakonfigurovali pro průběžnou změnu velikosti. Nové velikosti se automaticky vypočtou, aby se zobrazily všechny obsahy buněk bez omezení. Při programové změně velikosti sloupců, které <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> mají <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>hodnoty vlastností, se ale pro proporcionální úpravy hodnot vlastností sloupce <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> používají počítané šířky na základě obsahu a ve skutečnosti se jedná o šířky sloupců. následně se vypočítají podle těchto nových proporcí, aby všechny sloupce vyplnily dostupnou zobrazovanou oblast ovládacího prvku.  
  
 Programové změny velikosti se hodí k tomu, abyste se vyhnuli postihům výkonu s průběžnou změnou velikosti. Také je užitečné zadat počáteční velikost řádků, sloupců a hlaviček pro změnu uživatele a pro režim vyplnění sloupce.  
  
 Obvykle budete volat metody programové změny velikosti v určitých časech. Například můžete programově změnit velikost všech sloupců hned po načtení dat, nebo můžete programově změnit velikost konkrétního řádku po úpravě konkrétní hodnoty buňky.  
  
## <a name="customizing-content-based-sizing-behavior"></a>Přizpůsobení chování při změně velikosti podle obsahu  
 Můžete přizpůsobit chování velikosti při práci s odvozenými <xref:System.Windows.Forms.DataGridView> typy buňky, řádku a sloupce <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>přepsáním <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> metod, <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>, nebo voláním přetížení metody Protected Změna velikosti v odvozeném <xref:System.Windows.Forms.DataGridView> nad. Přetížení metody chráněné změny velikosti jsou navržena tak, aby fungovala v páru, aby bylo možné dosáhnout ideálního poměru výšky buňky na šířku a vyhnout se tak širokému nebo vysokému počtu buněk. Například pokud voláte `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` přetížení <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> metody a `false` předáte hodnotu <xref:System.Boolean> parametru, přetížení vypočítá ideální výšku a šířku pro buňky na řádku, ale upraví výšku řádků. pouze. Pak je nutné zavolat <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metodu pro úpravu šířky sloupců na vypočtené ideální.  
  
## <a name="content-based-sizing-options"></a>Možnosti změny velikosti podle obsahu  
 Výčty používané vlastnostmi a metodami změny velikosti mají podobné hodnoty pro určení velikosti podle obsahu. Pomocí těchto hodnot můžete omezit, které buňky se mají použít k výpočtu upřednostňovaných velikostí. U výčtů pro všechny změny velikosti se hodnoty s názvy, které odkazují na zobrazené buňky, omezují jejich výpočty na buňky v zobrazených řádcích. Vyloučení řádků je užitečné k tomu, abyste se vyhnuli snížení výkonu při práci s velkým množstvím řádků. Výpočty můžete také omezit na hodnoty buněk v záhlaví nebo nezáhlaví buňky.  
  
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
- [Postupy: Nastavení režimů změny velikosti ovládacího prvku DataGridView model Windows Forms](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
