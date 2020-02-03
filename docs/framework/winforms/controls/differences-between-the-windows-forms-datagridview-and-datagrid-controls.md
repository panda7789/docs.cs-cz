---
title: Rozdíly mezi ovládacími prvky DataGridView a DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 3552abe55d8e2c1cb4ae372ca64c7ca21f1fed0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745968"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid
<xref:System.Windows.Forms.DataGridView> ovládací prvek je nový ovládací prvek, který nahrazuje ovládací prvek <xref:System.Windows.Forms.DataGrid>. Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje mnoho základních a rozšířených funkcí, které v ovládacím prvku <xref:System.Windows.Forms.DataGrid> chybí. Kromě toho architektura ovládacího prvku <xref:System.Windows.Forms.DataGridView> výrazně usnadňuje rozšiřování a přizpůsobení než ovládací prvek <xref:System.Windows.Forms.DataGrid>.  
  
 Následující tabulka popisuje několik primárních funkcí, které jsou k dispozici v ovládacím prvku <xref:System.Windows.Forms.DataGridView>, které chybí v ovládacím prvku <xref:System.Windows.Forms.DataGrid>.  
  
|Funkce ovládacího prvku DataGridView|Popis|  
|----------------------------------|-----------------|  
|Více typů sloupců|Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje více předdefinovaných typů sloupců než ovládací prvek <xref:System.Windows.Forms.DataGrid>. Tyto typy sloupců vyhovují potřebám nejběžnějších scénářů, ale je také snazší je roztáhnout nebo nahradit typy sloupců v ovládacím prvku <xref:System.Windows.Forms.DataGrid>. Další informace naleznete v tématu [typy sloupců v ovládacím prvku DataGridView model Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).|  
|Více způsobů zobrazení dat|Ovládací prvek <xref:System.Windows.Forms.DataGrid> je omezený na zobrazení dat z externího zdroje dat. Ovládací prvek <xref:System.Windows.Forms.DataGridView> však může zobrazit nevázaná data uložená v ovládacím prvku, data z vázaného zdroje dat nebo vázaná a nevázaná data dohromady. Můžete také implementovat virtuální režim v ovládacím prvku <xref:System.Windows.Forms.DataGridView> k poskytnutí vlastní správy dat. Další informace najdete v tématu [režimy zobrazení dat v ovládacím prvku DataGridView model Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Více způsobů přizpůsobení zobrazení dat|Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje mnoho vlastností a událostí, které vám umožní určit, jak se mají data formátovat a zobrazovat. Například můžete změnit vzhled buněk, řádků a sloupců v závislosti na datech, která obsahují, nebo můžete nahradit data jednoho datového typu odpovídajícími daty jiného typu. Další informace najdete v tématu [formátování dat v ovládacím prvku DataGridView model Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Více možností pro změnu vzhledu buňky, řádku, sloupce a záhlaví a chování|Ovládací prvek <xref:System.Windows.Forms.DataGridView> umožňuje pracovat s jednotlivými komponentami mřížky mnoha různými způsoby. Můžete například ukotvit řádky a sloupce a zabránit tak jejich posouvání; Skrýt řádky, sloupce a hlavičky; změnit způsob, jakým se upravují velikosti řádků, sloupců a hlaviček; Změna způsobu, jakým uživatelé provedou výběry; a poskytněte popisy tlačítek a místní nabídky pro jednotlivé buňky, řádky a sloupce.|  
  
 <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a speciálním potřebám. Pro téměř všechny účely byste měli použít ovládací prvek <xref:System.Windows.Forms.DataGridView>. Jediná funkce, která je k dispozici v ovládacím prvku <xref:System.Windows.Forms.DataGrid>, který není k dispozici v ovládacím prvku <xref:System.Windows.Forms.DataGridView> je hierarchické zobrazení informací ze dvou souvisejících tabulek v jednom ovládacím prvku. Chcete-li zobrazit informace ze dvou tabulek, které jsou v relaci hlavního/podrobného, je nutné použít dva ovládací prvky <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Upgrade na ovládací prvek DataGridView  
 Pokud máte existující aplikace, které používají ovládací prvek <xref:System.Windows.Forms.DataGrid> v jednoduchém scénáři vázaného na data bez přizpůsobení, můžete nahradit starý ovládací prvek novým ovládacím prvkem. Oba ovládací prvky používají standardní architekturu model Windows Forms datovou vazbu, takže ovládací prvek <xref:System.Windows.Forms.DataGridView> zobrazí vaše vázaná data bez nutnosti další konfigurace. Můžete chtít zvážit využití vylepšení vázání dat, ale vytvořením vazby dat na komponentu <xref:System.Windows.Forms.BindingSource>, kterou pak můžete svázat s ovládacím prvkem <xref:System.Windows.Forms.DataGridView>. Další informace najdete v tématu [Komponenta BindingSource](bindingsource-component.md).  
  
 Vzhledem k tomu, že ovládací prvek <xref:System.Windows.Forms.DataGridView> má zcela novou architekturu, neexistuje žádná jednoduchá cesta pro převod, která vám umožní používat <xref:System.Windows.Forms.DataGrid> přizpůsobení s ovládacím prvkem <xref:System.Windows.Forms.DataGridView>. Mnoho <xref:System.Windows.Forms.DataGrid> přizpůsobení není u ovládacího prvku <xref:System.Windows.Forms.DataGridView> nutné, protože z důvodu integrovaných funkcí, které jsou k dispozici v novém ovládacím prvku. Pokud jste vytvořili vlastní typy sloupců pro ovládací prvek <xref:System.Windows.Forms.DataGrid>, který chcete použít s ovládacím prvkem <xref:System.Windows.Forms.DataGridView>, budete je muset implementovat znovu pomocí nové architektury. Další informace naleznete v tématu [přizpůsobení ovládacího prvku DataGridView model Windows Forms](customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [Ovládací prvek DataGridView](datagridview-control-windows-forms.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Komponenta BindingSource](bindingsource-component.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Formátování dat v ovládacím prvku Windows Forms DataGridView](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Režimy výběru v ovládacím prvku Windows Forms DataGridView](selection-modes-in-the-windows-forms-datagridview-control.md)
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
