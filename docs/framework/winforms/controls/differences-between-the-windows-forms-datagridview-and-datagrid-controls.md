---
title: Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 6802ef375d8d15826725e68f5065317192523178
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095669"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid
<xref:System.Windows.Forms.DataGridView> Je nový ovládací prvek, který nahrazuje <xref:System.Windows.Forms.DataGrid> ovládacího prvku. <xref:System.Windows.Forms.DataGridView> Řízení poskytuje mnoho základních a pokročilých funkcí, které nebyly nalezeny v <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Kromě toho architektuře <xref:System.Windows.Forms.DataGridView> ovládací prvek je mnohem jednodušší rozšířit a přizpůsobit než <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
 Následující tabulka popisuje některé z primární funkce dostupné v <xref:System.Windows.Forms.DataGridView> ovládací prvek, který chybí <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
|Funkce ovládacího prvku DataGridView|Popis|  
|----------------------------------|-----------------|  
|Více typů sloupců|<xref:System.Windows.Forms.DataGridView> Řízení poskytuje další vestavěné typy sloupců, než <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Tyto typy sloupců vyhovovaly nejběžnějších scénářů, ale je také snazší rozšířit nebo nahradit než typy sloupců v <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Další informace najdete v tématu [typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md).|  
|Několik způsobů, jak zobrazit data|<xref:System.Windows.Forms.DataGrid> Ovládací prvek je omezený na zobrazení dat z externího zdroje dat. <xref:System.Windows.Forms.DataGridView> Ovládacího prvku, ale můžete zobrazit nevázaných dat uložených v ovládacího prvku, data ze zdroje vázaných dat nebo vázané a nevázaných dat společně. Můžete implementovat virtuální režim <xref:System.Windows.Forms.DataGridView> ovládacího prvku a zajistit tak správu vlastní data. Další informace najdete v tématu [režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Několik způsobů, jak přizpůsobit zobrazení dat|<xref:System.Windows.Forms.DataGridView> Ovládací prvek obsahuje mnoho vlastností a událostí, které vám umožní určit, jak je ve formátu data a je zobrazena. Například můžete změnit vzhled buněk, řádků a sloupců v závislosti na tom, které obsahují data nebo data jednoho datového typu můžete nahradit ekvivalentní datové jiného typu. Další informace najdete v tématu [formátování dat v ovládacím prvku Windows Forms DataGridView](data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Více možností pro změnu buňky, řádek, sloupce a záhlaví vzhled a chování|<xref:System.Windows.Forms.DataGridView> Ovládací prvek umožňuje pracovat s komponentami jednotlivé tabulky v několika různými způsoby. Například můžete ukotvit řádků a sloupců a zabrání tak jejich posouvání; Skrýt řádky, sloupce a záhlaví; Změňte způsob, jakým jsou upraveny velikosti řádků, sloupců a záhlaví; změnit způsob, jakým uživatelé dle; a obsahují popisy a místní nabídky k jednotlivých buněk, řádků a sloupců.|  
  
 <xref:System.Windows.Forms.DataGrid> Ovládací prvek se zachovává kvůli zpětné kompatibilitě a pro speciální požadavky. Pro téměř všechny účely byste měli použít <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pouze funkce, která je k dispozici v <xref:System.Windows.Forms.DataGrid> ovládací prvek, který není k dispozici v <xref:System.Windows.Forms.DataGridView> hierarchické zobrazení informací ze dvou souvisejících tabulek v jeden ovládací prvek je ovládací prvek. Je nutné použít dvě <xref:System.Windows.Forms.DataGridView> ovládacích prvků pro zobrazení informací ze dvou tabulek, které jsou v relaci hlavního záznamu/podrobností.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Upgrade na ovládacím prvku DataGridView  
 Pokud máte existující aplikace, které používají <xref:System.Windows.Forms.DataGrid> ovládacího prvku v jednoduchém scénáři vázané na data bez přizpůsobení můžete jednoduše nahradit původní ovládací prvek nový ovládací prvek. Oba ovládací prvky použít standardní architekturu datové vazby Windows Forms, takže <xref:System.Windows.Forms.DataGridView> ovládací prvek zobrazí vázaných dat s nepotřebují žádnou další konfiguraci. Můžete chtít zvážit využití výhod vylepšení datové vazby, ale pomocí vazby dat <xref:System.Windows.Forms.BindingSource> součásti, která pak můžete vázat na <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Další informace najdete v tématu [komponenty BindingSource](bindingsource-component.md).  
  
 Protože <xref:System.Windows.Forms.DataGridView> ovládací prvek má úplně nové architektury, neexistuje jednoduchý převod cesta, která vám umožní použít <xref:System.Windows.Forms.DataGrid> přizpůsobení <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Mnoho <xref:System.Windows.Forms.DataGrid> přizpůsobení nejsou potřeba se <xref:System.Windows.Forms.DataGridView> řídit, ale kvůli integrované funkce dostupné v nový ovládací prvek. Pokud jste si vytvořili vlastní sloupec typy pro <xref:System.Windows.Forms.DataGrid> ovládací prvek, který chcete použít s <xref:System.Windows.Forms.DataGridView> ovládacího prvku, je nutné je znovu pomocí nové architektury implementovat. Další informace najdete v tématu [přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView – ovládací prvek](datagridview-control-windows-forms.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [BindingSource – komponenta](bindingsource-component.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Formátování dat v ovládacím prvku Windows Forms DataGridView](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Režimy třídění sloupce v ovládacím prvku Windows Forms DataGridView](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Režimy výběru v ovládacím prvku Windows Forms DataGridView](selection-modes-in-the-windows-forms-datagridview-control.md)
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
