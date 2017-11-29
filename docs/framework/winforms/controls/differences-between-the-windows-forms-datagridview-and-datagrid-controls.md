---
title: "Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 38373b8e3201ea0a6c32d972c7ac9c72888d5eae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid
<xref:System.Windows.Forms.DataGridView> Je nový ovládací prvek, který nahrazuje <xref:System.Windows.Forms.DataGrid> ovládacího prvku. <xref:System.Windows.Forms.DataGridView> Řízení poskytuje mnoho základních a pokročilých funkcí, které chybí v <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Kromě toho architektuře <xref:System.Windows.Forms.DataGridView> ovládací prvek je mnohem jednodušší rozšířit a přizpůsobit než <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
 Následující tabulka popisuje několik primární funkce dostupné v <xref:System.Windows.Forms.DataGridView> ovládací prvek, který chybí <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
|DataGridView – ovládací prvek funkce|Popis|  
|----------------------------------|-----------------|  
|Více typů sloupců|<xref:System.Windows.Forms.DataGridView> Řízení poskytuje další vestavěné typy sloupců než <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Tyto typy sloupců vyhovovaly nejběžnějších scénářů, ale jsou taky usnadňují rozšířit nebo nahradit než typy sloupce v <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Další informace najdete v tématu [typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).|  
|Více způsobů pro zobrazení dat|<xref:System.Windows.Forms.DataGrid> Řízení k zobrazení dat z externího zdroje dat je omezená. <xref:System.Windows.Forms.DataGridView> Řízení, můžete však zobrazení nevázaných dat uložených v ovládacího prvku, data ze zdroje dat vázané nebo vázaných a nevázaných dat společně. Můžete taky implementovat virtuální režim <xref:System.Windows.Forms.DataGridView> řízení a zajistit tak správu vlastní data. Další informace najdete v tématu [režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Více způsoby, jak přizpůsobit zobrazení dat|<xref:System.Windows.Forms.DataGridView> Řízení poskytuje mnoho vlastností a událostí, které vám umožní určit, jak datového naformátován a zobrazit. Například můžete změnit vzhled buněk, řádků a sloupců v závislosti na data, která obsahují, nebo můžete data jednoho datového typu nahradit ekvivalentní datové jiného typu. Další informace najdete v tématu [formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Více možností pro změnu buněk, řádků, sloupců a hlavičky vzhled a chování|<xref:System.Windows.Forms.DataGridView> Řízení umožňuje pracovat s komponentami individuální mřížku mnoha způsoby. Například můžete zmrazení řádků a sloupců, chcete-li zabránit posouvání; Skrýt řádky, sloupce a hlavičky; Změňte způsob, jakým jsou upraveny velikosti řádků, sloupců a záhlaví; změnit způsob, jakým uživatelé věci; a obsahují popisy tlačítek a místní nabídky k jednotlivých buněk, řádků a sloupců.|  
  
 <xref:System.Windows.Forms.DataGrid> Řízení se zachovává kvůli zpětné kompatibilitě a zvláštními potřebami. Téměř všechny účely, měli byste použít <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pouze funkce, která je k dispozici v <xref:System.Windows.Forms.DataGrid> ovládací prvek, který není k dispozici v <xref:System.Windows.Forms.DataGridView> řízení je hierarchické zobrazení informací ze dvou tabulek v jeden ovládací prvek. Je nutné použít dva <xref:System.Windows.Forms.DataGridView> ovládacích prvků pro zobrazení informací ze dvou tabulek, které jsou v relaci a podrobností.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Upgrade na ovládacím prvku DataGridView  
 Pokud máte existující aplikace, které používají <xref:System.Windows.Forms.DataGrid> ovládací prvek v jednoduchém scénáři vázané na data bez přizpůsobení můžete jednoduše nahradit původní ovládacího prvku nový ovládací prvek. Oba ovládací prvky použít standardní Architektura Windows Forms vazby dat, proto <xref:System.Windows.Forms.DataGridView> ovládací prvek bude zobrazení vázaných dat s nepotřebují žádnou další konfiguraci. Můžete chtít zvážit využívat výhod vylepšení datové vazby, ale pomocí vytvoření vazby dat, aby se <xref:System.Windows.Forms.BindingSource> komponenta, která pak můžete vázat na <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Další informace najdete v tématu [BindingSource – komponenta](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 Protože <xref:System.Windows.Forms.DataGridView> ovládací prvek má úplně novou architekturu, neexistuje žádný snadný převod cestu, která vám umožní použít <xref:System.Windows.Forms.DataGrid> přizpůsobení <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Mnoho <xref:System.Windows.Forms.DataGrid> úpravy nejsou potřeba se <xref:System.Windows.Forms.DataGridView> řídit, ale kvůli integrované funkce, které jsou k dispozici v nové ovládací prvek. Pokud jste vytvořili vlastní sloupec typy pro <xref:System.Windows.Forms.DataGrid> ovládací prvek, který chcete použít s <xref:System.Windows.Forms.DataGridView> ovládací prvek, je nutné je znovu pomocí nové architektury provede. Další informace najdete v tématu [přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Windows.Forms.BindingSource>  
 [DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [DataGrid – ovládací prvek](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [BindingSource – komponenta](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 [Formátování dat v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 [Režimy třídění sloupce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Režimy výběru v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
