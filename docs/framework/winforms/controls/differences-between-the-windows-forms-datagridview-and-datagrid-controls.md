---
title: Rozdíly mezi ovládacími prvky DataGridView a DataGrid
description: Přečtěte si o různých rozdílech mezi funkcemi model Windows Forms DataGridView a DataGrid a také s rozdíly v jejich architektuře.
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 1438182d764097ae4f8fd7df046ad72c9213da19
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174585"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid
<xref:System.Windows.Forms.DataGridView>Ovládací prvek je nový ovládací prvek, který nahradí <xref:System.Windows.Forms.DataGrid> ovládací prvek. <xref:System.Windows.Forms.DataGridView>Ovládací prvek poskytuje řadu základních a rozšířených funkcí, které v <xref:System.Windows.Forms.DataGrid> ovládacím prvku chybí. Kromě toho architektura <xref:System.Windows.Forms.DataGridView> ovládacího prvku výrazně usnadňuje rozšiřování a přizpůsobení než <xref:System.Windows.Forms.DataGrid> ovládací prvek.  
  
 Následující tabulka popisuje několik primárních funkcí, které jsou k dispozici v <xref:System.Windows.Forms.DataGridView> ovládacím prvku, které v <xref:System.Windows.Forms.DataGrid> ovládacím prvku chybí.  
  
|Funkce ovládacího prvku DataGridView|Popis|  
|----------------------------------|-----------------|  
|Více typů sloupců|<xref:System.Windows.Forms.DataGridView>Ovládací prvek poskytuje více předdefinovaných typů sloupců než <xref:System.Windows.Forms.DataGrid> ovládací prvek. Tyto typy sloupců vyhovují potřebám nejběžnějších scénářů, ale je také snazší je roztáhnout nebo nahradit typy sloupců v <xref:System.Windows.Forms.DataGrid> ovládacím prvku. Další informace naleznete v tématu [typy sloupců v ovládacím prvku DataGridView model Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).|  
|Více způsobů zobrazení dat|<xref:System.Windows.Forms.DataGrid>Ovládací prvek je omezen na zobrazení dat z externího zdroje dat. <xref:System.Windows.Forms.DataGridView>Ovládací prvek však může zobrazit nevázaná data uložená v ovládacím prvku, data z vázaného zdroje dat nebo vázaná a nevázaná data dohromady. Můžete také implementovat virtuální režim v <xref:System.Windows.Forms.DataGridView> ovládacím prvku pro zajištění vlastní správy dat. Další informace najdete v tématu [režimy zobrazení dat v ovládacím prvku DataGridView model Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Více způsobů přizpůsobení zobrazení dat|<xref:System.Windows.Forms.DataGridView>Ovládací prvek poskytuje mnoho vlastností a událostí, které vám umožní určit, jak se mají data formátovat a zobrazovat. Například můžete změnit vzhled buněk, řádků a sloupců v závislosti na datech, která obsahují, nebo můžete nahradit data jednoho datového typu odpovídajícími daty jiného typu. Další informace najdete v tématu [formátování dat v ovládacím prvku DataGridView model Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Více možností pro změnu vzhledu buňky, řádku, sloupce a záhlaví a chování|<xref:System.Windows.Forms.DataGridView>Ovládací prvek umožňuje pracovat s jednotlivými komponentami mřížky mnoha různými způsoby. Můžete například ukotvit řádky a sloupce a zabránit tak jejich posouvání; Skrýt řádky, sloupce a hlavičky; změnit způsob, jakým se upravují velikosti řádků, sloupců a hlaviček; Změna způsobu, jakým uživatelé provedou výběry; a poskytněte popisy tlačítek a místní nabídky pro jednotlivé buňky, řádky a sloupce.|  
  
 <xref:System.Windows.Forms.DataGrid>Ovládací prvek se zachovává kvůli zpětné kompatibilitě a speciálním potřebám. Pro téměř všechny účely byste měli použít <xref:System.Windows.Forms.DataGridView> ovládací prvek. Jediná funkce, která je k dispozici v <xref:System.Windows.Forms.DataGrid> ovládacím prvku, který není v ovládacím prvku k dispozici, <xref:System.Windows.Forms.DataGridView> je hierarchické zobrazení informací ze dvou souvisejících tabulek v jednom ovládacím prvku. <xref:System.Windows.Forms.DataGridView>Chcete-li zobrazit informace ze dvou tabulek, které jsou v relaci hlavního/podrobného, je nutné použít dva ovládací prvky.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Upgrade na ovládací prvek DataGridView  
 Pokud máte existující aplikace, které <xref:System.Windows.Forms.DataGrid> ovládací prvek používají v jednoduchém scénáři vázaného na data bez přizpůsobení, můžete nahradit starý ovládací prvek novým ovládacím prvkem. Oba ovládací prvky používají standardní model Windows Forms architektury datových vazeb, takže <xref:System.Windows.Forms.DataGridView> ovládací prvek zobrazí vaše vázaná data bez nutnosti další konfigurace. Možná budete chtít zvážit využití vylepšení vázání dat, ale vytvořením vazby dat na <xref:System.Windows.Forms.BindingSource> komponentu, kterou můžete svázat s <xref:System.Windows.Forms.DataGridView> ovládacím prvkem. Další informace najdete v tématu [Komponenta BindingSource](bindingsource-component.md).  
  
 Vzhledem k tomu <xref:System.Windows.Forms.DataGridView> , že ovládací prvek má zcela novou architekturu, neexistuje žádná jednoduchá cesta pro převod, která vám umožní použít <xref:System.Windows.Forms.DataGrid> přizpůsobení s <xref:System.Windows.Forms.DataGridView> ovládacím prvkem. Mnoho <xref:System.Windows.Forms.DataGrid> přizpůsobení není v <xref:System.Windows.Forms.DataGridView> ovládacím prvku k dispozici, ale z důvodu integrovaných funkcí dostupných v novém ovládacím prvku. Pokud jste vytvořili vlastní typy sloupců pro <xref:System.Windows.Forms.DataGrid> ovládací prvek, který chcete použít s <xref:System.Windows.Forms.DataGridView> ovládacím prvkem, budete ho muset znovu implementovat pomocí nové architektury. Další informace naleznete v tématu [přizpůsobení ovládacího prvku DataGridView model Windows Forms](customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView – ovládací prvek](datagridview-control-windows-forms.md)
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
