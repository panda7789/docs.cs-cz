---
title: "Styly buňky v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: edec8a00aff59195c6c80414eb4b950d68e488da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Styly buňky v ovládacím prvku Windows Forms DataGridView
Každá buňka v rámci <xref:System.Windows.Forms.DataGridView> ovládací prvek může mít svůj vlastní styl, jako je například textovém formátu, barva pozadí, barvu popředí a písma. Však obvykle více buněk sdílet vlastnosti konkrétní stylu.  
  
 Skupiny buněk, které sdílejí styly může zahrnovat všechny buňky v rámci konkrétní řádky nebo sloupce, všechny buňky, které obsahují konkrétní hodnoty nebo všechny buňky v ovládacím prvku. Protože tyto skupiny překrývají, jednotlivým buňkám může získat informace o stylu z více než jednom místě. Například můžete každé buňce ve <xref:System.Windows.Forms.DataGridView> ovládací prvek pro použití stejné písmo, ale pouze buněk v měna sloupce pro použití formátu měny a pouze měna buněk s záporná čísla používat barvu red popředí.  
  
## <a name="the-datagridviewcellstyle-class"></a>DataGridViewCellStyle – třída  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Třída obsahuje následující vlastnosti související s vizuální styl:  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>a<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A>a<xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Tato třída také obsahuje následující vlastnosti související s formátování:  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>a<xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A>a<xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Další informace o těchto vlastností a dalších vlastností styl buněk, najdete v článku <xref:System.Windows.Forms.DataGridViewCellStyle> referenční dokumentaci a v tématech uvedených v části Viz také níže.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Používání DataGridViewCellStyle objektů  
 Můžete načíst <xref:System.Windows.Forms.DataGridViewCellStyle> objekty z různých vlastnosti <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>, a <xref:System.Windows.Forms.DataGridViewCell> třídy a jejich odvozené třídy. Pokud jeden z těchto vlastností dosud nebyl nastaven, načítání jeho hodnota se vytvoří nové <xref:System.Windows.Forms.DataGridViewCellStyle> objektu. Můžete také vytvořit instanci vlastního <xref:System.Windows.Forms.DataGridViewCellStyle> objekty a přiřaďte je ke tyto vlastnosti.  
  
 Při sdílení se můžete vyhnout zdvojení informace o stylu <xref:System.Windows.Forms.DataGridViewCellStyle> objekty mezi více <xref:System.Windows.Forms.DataGridView> elementy. Protože stylů nastavit řízení, sloupce a řádkový filtr úrovně dolů prostřednictvím každou úroveň na úroveň buňky, můžete také vyhnout styl duplikace nastavením pouze vlastnosti stylu na každé úrovni, který se liší od výše uvedených úrovně. To je podrobně popsaná v další v následující části styl dědičnosti.  
  
 Následující tabulka uvádí primární vlastnosti, které získání nebo nastavení <xref:System.Windows.Forms.DataGridViewCellStyle> objekty.  
  
|Vlastnost|Třídy|Popis|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>a jsou odvozené třídy|Získá nebo nastaví výchozí styly využívané prostředím všechny buňky v celý ovládací prvek (včetně buněk záhlaví), ve sloupci nebo v řádku.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozích stylů buňky používané všechny řádky v ovládacím prvku. Nezahrnuje hlavičky buněk.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozích stylů buňky používané střídavých řádků v ovládacím prvku. Použít k vytvoření účetní knihy vliv.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozích stylů buňky používané ovládacího prvku záhlaví řádků. Pokud jsou povolené vizuální styly přepsány aktuální motiv.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozích stylů buňky používané ovládacího prvku záhlaví sloupců. Pokud jsou povolené vizuální styly přepsány aktuální motiv.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell>a odvozených tříd|Získá nebo nastaví styly definované na úrovni buněk. Tyto styly přednost před akcemi zděděn z vyšší úrovně.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>a jsou odvozené třídy|Získá všechny styly aktuálně u buněk, řádků nebo sloupec, včetně styly zděděn z vyšší úrovně.|  
  
 Jak je uvedeno nahoře, zjišťování hodnoty vlastnosti stylu automaticky vytvoří nový <xref:System.Windows.Forms.DataGridViewCellStyle> objektu, pokud vlastnost nebyla nastavena dříve. Abyste se vyhnuli zbytečně vytváření těchto objektů, tříd řádků a sloupců mají <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> vlastnost, která můžete zkontrolovat, určete zda <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> vlastnost byla nastavena. Podobně třídy buňky mají <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> vlastnost, která určuje, zda <xref:System.Windows.Forms.DataGridViewCell.Style%2A> vlastnost byla nastavena.  
  
 Všechny vlastnosti stylu má odpovídající *PropertyName* `Changed` událostí na <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pro řádek, sloupce a vlastnosti buněk, název události začíná "`Row`","`Column`", nebo "`Cell`" (například <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Každá z těchto událostí nastane, když je odpovídající vlastnost stylu nastavena na jiný <xref:System.Windows.Forms.DataGridViewCellStyle> objektu. Tyto události se nevyskytují při načítání <xref:System.Windows.Forms.DataGridViewCellStyle> objekt z vlastnosti stylu a upravte jeho hodnoty vlastností. Reagovat na změny v samotných objektech styl buněk, zpracování <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> událostí.  
  
## <a name="style-inheritance"></a>Styl dědičnosti  
 Každý <xref:System.Windows.Forms.DataGridViewCell> získá její vzhled z jeho <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> vlastnost. <xref:System.Windows.Forms.DataGridViewCellStyle> Objekt tato vlastnost vrátí dědí své hodnoty z hierarchie vlastnosti typu <xref:System.Windows.Forms.DataGridViewCellStyle>. Tyto vlastnosti jsou uvedeny níže v pořadí, ve kterém <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> pro není v záhlaví buňky získá jeho hodnoty.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(jenom pro buněk v řádky s lichou čísla indexů)  
  
4.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pro buňky záhlaví řádků a sloupců <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> vlastnost nebude naplněn sadou hodnot z následujícího seznamu vlastností zdroje v uvedeném pořadí.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>nebo<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Následující diagram znázorňuje tento proces.  
  
 ![Vlastnosti typu DataGridViewCellStyle](../../../../docs/framework/winforms/controls/media/datagridviewcells1.gif "DataGridViewCells1")  
  
 Můžete taky přejít styly zdědí konkrétní řádků a sloupců. Sloupec <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> vlastnost dědí své hodnoty z následující vlastnosti.  
  
1.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Řádek <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> vlastnost dědí své hodnoty z následující vlastnosti.  
  
1.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(jenom pro buněk v řádky s lichou čísla indexů)  
  
3.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pro každou vlastnost v <xref:System.Windows.Forms.DataGridViewCellStyle> objekt vrácený `InheritedStyle` vlastnost, hodnota vlastnosti se získávají z první styl buněk v příslušném seznamu, který má odpovídající vlastnost nastavená na hodnotu jiné než <xref:System.Windows.Forms.DataGridViewCellStyle> třídy výchozí hodnoty.  
  
 Následující tabulka popisuje, jak <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> hodnotu vlastnosti u buněk příklad je zděděn z jeho obsahující sloupec.  
  
|Vlastnost typu`DataGridViewCellStyle`|Příklad `ForeColor` hodnota načtené objektu|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 V takovém případě <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> hodnota z buňky řádku je první skutečné hodnoty v seznamu. To se stane <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> hodnotu vlastnosti buňky <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>.  
  
 Následující diagram ilustruje, jak budou různí <xref:System.Windows.Forms.DataGridViewCellStyle> vlastnosti může dědit vlastnosti jejich hodnoty z různých místech.  
  
 ![DataGridView – vlastnost & č. 45; hodnota dědičnosti](../../../../docs/framework/winforms/controls/media/datagridviewcells2.gif "DataGridViewCells2")  
  
 Využití výhod styl dědičnosti, můžete poskytnout příslušné styly pro celý ovládací prvek bez nutnosti zadávat stejné informace na více místech.  
  
 I když buňky hlavičky styl dědičnosti účastnit, jak je popsáno, objekty vrácené <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> vlastnosti <xref:System.Windows.Forms.DataGridView> ovládací prvek mít hodnoty počáteční vlastností, které přepsat hodnoty vlastností pro objekt vrácený rutinou <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> vlastnost. Pokud chcete vlastnosti nastavit pro objekt vrácený <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> vlastnost použít záhlaví řádků a sloupců, musíte nastavit odpovídající vlastnosti objektů vrácené <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> uvedené vlastnosti na výchozí hodnoty pro <xref:System.Windows.Forms.DataGridViewCellStyle> třídy.  
  
> [!NOTE]
>  Pokud jsou povolené vizuální styly, záhlaví řádků a sloupců (s výjimkou <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) jsou automaticky ve podle aktuálního motivu, přepsání žádné styly definované pomocí těchto vlastností.  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>, A <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> typy také inicializovat některé hodnoty pro objekt vrácený rutinou sloupec <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> vlastnost. Další informace najdete v tématu referenční dokumentaci pro tyto typy.  
  
## <a name="setting-styles-dynamically"></a>Nastavení stylů dynamicky  
 Chcete-li přizpůsobit stylů buňky s konkrétní hodnoty, implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událostí. Obslužné rutiny pro tuto událost přijímat argument <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> typu. Tento objekt obsahuje vlastnosti, které vám umožňují určit hodnotu buňka společně s jeho umístění <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Tento objekt obsahuje také <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> vlastnost, která je inicializována tak, aby hodnota <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> vlastnost buňky, který je formátován. Můžete upravit vlastnosti styl buněk k zadání informací o stylu odpovídající hodnotu buňky a umístění.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.RowPrePaint> a <xref:System.Windows.Forms.DataGridView.RowPostPaint> události také přijímat <xref:System.Windows.Forms.DataGridViewCellStyle> data události objektu, ale v jejich případě je kopii řádku <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> vlastnost pro účely jen pro čtení a změny se neovlivní ovládacího prvku.  
  
 Můžete také dynamicky upravit styly jednotlivých buněk v reakci na události, jako <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridView.CellMouseLeave> události. Například v obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellMouseEnter> události, může uložit aktuální hodnota barvu pozadí buněk (načíst prostřednictvím buňky <xref:System.Windows.Forms.DataGridViewCell.Style%2A> vlastnost), nastavte ji na novou barvu, která bude zvýrazněte buňky, když je ponechán ukazatel myši nad ním. V obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellMouseLeave> událostí, barva pozadí pak můžete obnovit na původní hodnotu.  
  
> [!NOTE]
>  Ukládání do mezipaměti hodnotami uloženými v buňky <xref:System.Windows.Forms.DataGridViewCell.Style%2A> vlastnost je důležité, bez ohledu na to, jestli je nastavená hodnota určitého stylu. Pokud nahradíte dočasně nastavení stylu, obnovení do původního stavu "není nastavena" zajistí, že buňky přejde zpět na styl nastavení, která dědí z vyšší úrovně. Pokud potřebujete zjistit skutečný styl platí pro buňku bez ohledu na to, jestli je zděděn styl, použijte na buňku <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>  
 [Základní formátování a styly v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Postupy: nastavení výchozích stylů buňky pro Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 [Formátování dat v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)
