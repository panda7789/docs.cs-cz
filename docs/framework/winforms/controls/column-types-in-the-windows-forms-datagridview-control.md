---
title: "Typy sloupců v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e45ddcec4459e376a5dab4eec36e51cc2e5e49c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Typy sloupců v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Řízení používá několik typů sloupce a zobrazit informace o jeho povolit uživatelům změnit nebo přidat informace.  
  
 Po vytvoření vazby <xref:System.Windows.Forms.DataGridView> řízení a nastavení <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> vlastnost `true`, sloupce jsou automaticky generovány pomocí výchozí typy sloupce, které jsou vhodné pro typy dat obsažené v vázaný datový zdroj.  
  
 Můžete také vytvořit instance jakékoli třídy sloupec sami a přidat je do kolekce vrácené <xref:System.Windows.Forms.DataGridView.Columns%2A> vlastnost. Můžete vytvořit tyto instance pro použití jako nevázaných sloupců, nebo můžete ručně svázat. Ručně vázané sloupce jsou užitečné, například pokud chcete nahradit na automaticky generovaný sloupec jeden typ sloupce jiného typu.  
  
 Následující tabulka popisuje různé třídy sloupce, která je k dispozici pro použití v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Použít s textové hodnoty. Vytvoření automaticky při vytvoření vazby na čísla a řetězce.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|Použít s <xref:System.Boolean> a <xref:System.Windows.Forms.CheckState> hodnoty. Vytvoření automaticky při vytvoření vazby na hodnoty těchto typů.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Slouží k zobrazení bitové kopie. Vytvoření automaticky při vytvoření vazby na pole bajtů <xref:System.Drawing.Image> objekty, nebo <xref:System.Drawing.Icon> objekty.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Slouží k zobrazení tlačítka v buňkách. Automaticky generuje při vytváření vazby. Obvykle se používá jako nevázaných sloupců.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Slouží k zobrazení rozevíracích seznamů v buňkách. Automaticky generuje při vytváření vazby. Obvykle vázané na data ručně.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Slouží k zobrazení odkazy v buňkách. Automaticky generuje při vytváření vazby. Obvykle vázané na data ručně.|  
|Typ vašeho vlastního sloupce|Můžete vytvořit vlastní třídu sloupec dědění <xref:System.Windows.Forms.DataGridViewColumn> třídu nebo všechny jejich odvozené třídy, které poskytují vlastní vzhled, chování nebo hostované ovládací prvky. Další informace najdete v tématu [postupy: přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView pomocí rozšíření jejich chování a vzhledu](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Tyto typy sloupců jsou popsány podrobněji v následujících částech.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn> Je typ sloupce pro obecné účely pro použití s textové hodnoty jako čísla a řetězce. V režimu úprav <xref:System.Windows.Forms.TextBox> ovládací prvek je zobrazen v aktivní buňce povolení uživatelům změnit hodnotu buňky.  
  
 Hodnoty buněk je automaticky převeden na řetězce pro zobrazení. Hodnoty zadané nebo upraven uživatelem se automaticky Parsuje vytvořit hodnotu buňky odpovídající datového typu. Můžete přizpůsobit tyto převody zpracování <xref:System.Windows.Forms.DataGridView.CellFormatting> a <xref:System.Windows.Forms.DataGridView.CellParsing> události <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 Hodnota buňky datový typ sloupce je zadán v <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> vlastnost sloupce.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> Se používá s <xref:System.Boolean> a <xref:System.Windows.Forms.CheckState> hodnoty. <xref:System.Boolean>hodnoty se zobrazí jako stavu dvou nebo tří stavů zaškrtávacích políček, v závislosti na hodnotě <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> vlastnost. Sloupec je vázána k <xref:System.Windows.Forms.CheckState> hodnoty, <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> hodnota vlastnosti je `true` ve výchozím nastavení.  
  
 Obvykle hodnot v buňkách políčko jsou určené pro úložiště, jako další data, nebo provádění hromadné operace. Pokud chcete reagovat okamžitě, když uživatelé kliknou na buňku zaškrtávací políčko, může zpracovat <xref:System.Windows.Forms.DataGridView.CellClick> událostí, ale tato událost nastane dříve, než se aktualizuje hodnotu buňky. Pokud potřebujete v době, klepněte na tlačítko Nová hodnota, jednou z možností je pro výpočet, očekávané hodnoty, které je bude na základě aktuální hodnoty. Další možností je Potvrdit změnu okamžitě a zpracovat <xref:System.Windows.Forms.DataGridView.CellValueChanged> událost, která má odpovědět na ni. Potvrzení změn při kliknutí na buňky, je nutné zpracovat <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged> událostí. V obslužné rutině, pokud aktuální buňky buňku zaškrtávací políčko, zavolejte <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> metoda a předejte jí <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit> hodnotu.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn> Slouží k zobrazení obrázků. Sloupce obrázku můžou vyplní automaticky ze zdroje dat, ručně vyplněný pro nevázaných sloupců nebo dynamicky vložené do obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellFormatting> událostí.  
  
 Automatické naplnění sloupec bitové kopie ze zdroje dat pracuje s pole bajtů v různých formátech bitové kopie, včetně všech formátů podporovaných <xref:System.Drawing.Image> třídy a OLE obrázek formát používaný Microsoft® Access a ukázková databáze Northwind.  
  
 Ručně vyplnění sloupce obrázku je užitečné, když chcete poskytovat funkce <xref:System.Windows.Forms.DataGridViewButtonColumn>, ale s přizpůsobený vzhled. Může zpracovat <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> událost a reakce na kliknutí v rámci buňky bitové kopie.  
  
 Naplnění buněk sloupce obrázku v obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellFormatting> událostí je užitečné, když chcete poskytnout bitové kopie pro počítané hodnoty nebo ve formátech bitové kopie. Například může mít "Rizika" sloupec s řetězcové hodnoty jako `"high"`, `"middle"`, a `"low"` , kterou chcete zobrazit jako ikony. Alternativně můžete mít na sloupec "Image", obsahující umístění bitové kopie, které musí být načteny místo binární obsah bitové kopie.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 Pomocí <xref:System.Windows.Forms.DataGridViewButtonColumn>, můžete zobrazit sloupec buněk, které obsahují tlačítka. To je užitečné, když chcete poskytují snadný způsob pro vaše uživatele k provádění akcí na konkrétní záznamy, jako je například umístění pořadí nebo zobrazení podřízené záznamy v samostatném okně.  
  
 Tlačítko sloupce nejsou automaticky vytvoří, když datové vazby <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Použití tlačítko sloupců, musíte je ručně vytvořit a přidat je do kolekce vrácené <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType> vlastnost.  
  
 Může odpovídat na kliknutí uživatele v buňkách tlačítko tak, že zpracování <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> událostí.  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 Pomocí <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, můžete zobrazit sloupec buněk, které obsahují seznamy rozevíracího seznamu. To je užitečné pro zadávání dat v polích, která může obsahovat pouze konkrétní hodnoty, například sloupci kategorie produktů tabulky v ukázkové databázi Northwind.  
  
 Můžete naplnění rozevíracího seznamu použít pro všechny buňky stejným způsobem, jako by naplnění <xref:System.Windows.Forms.ComboBox> rozevíracího seznamu, buď ručně prostřednictvím kolekce vrácené <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> vlastnost, nebo vazby ke zdroji dat prostřednictvím <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>, a <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> vlastnosti. Další informace najdete v tématu [ComboBox – ovládací prvek](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md).  
  
 Hodnoty skutečné buněk můžete vázat na zdroj dat používaný <xref:System.Windows.Forms.DataGridView> ovládací prvek pro nastavení <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> vlastnost <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
 Pole se seznamem pole sloupců nejsou automaticky vytvoří, když datové vazby <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Použití sloupců pole se seznamem, musíte je ručně vytvořit a přidat je do kolekce vrácené <xref:System.Windows.Forms.DataGridView.Columns%2A> vlastnost.  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 Pomocí <xref:System.Windows.Forms.DataGridViewLinkColumn>, můžete zobrazit sloupce buněk, které obsahují hypertextové odkazy. To je užitečné pro adresu URL hodnoty ve zdroji dat, nebo jako alternativu k sloupci tlačítko pro zvláštní chování, například otevřete okno s podřízené záznamy.  
  
 Odkaz sloupce nejsou automaticky vytvoří, když datové vazby <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Použití sloupců odkaz, musíte je vytvořit ručně a přidat je do kolekce vrácené <xref:System.Windows.Forms.DataGridView.Columns%2A> vlastnost.  
  
 Může odpovídat na uživatele kliknutí na odkazy tak, že zpracování <xref:System.Windows.Forms.DataGridView.CellContentClick> událostí. Tato událost se liší od <xref:System.Windows.Forms.DataGridView.CellClick> a <xref:System.Windows.Forms.DataGridView.CellMouseClick> události, ke kterým dochází, když uživatel klikne kdekoli v buňce.  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn> Třída poskytuje několik vlastností úpravy vzhledu odkazů před, během a po jejich klikli.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewImageColumn>  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>  
 [DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Postupy: zobrazení obrázků v buňkách Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 [Postupy: práce se sloupci obrázků v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
