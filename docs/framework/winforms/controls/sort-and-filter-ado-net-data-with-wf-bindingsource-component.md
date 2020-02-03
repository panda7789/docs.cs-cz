---
title: Řazení a filtrování dat ADO.NET pomocí součásti BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: cf1da3bb94b26449eb72b0e4930b262236487acc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742974"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Postupy: Řazení a filtrování dat ADO.NET pomocí součásti Windows Forms BindingSource
Pomocí vlastností <xref:System.Windows.Forms.BindingSource.Sort%2A> a <xref:System.Windows.Forms.BindingSource.Filter%2A> můžete vystavit možnosti řazení a filtrování <xref:System.Windows.Forms.BindingSource> ovládacího prvku. Jednoduché řazení můžete použít, když je podkladový zdroj dat <xref:System.ComponentModel.IBindingList>a můžete použít filtrování a rozšířené řazení, pokud je zdrojem dat <xref:System.ComponentModel.IBindingListView>. Vlastnost <xref:System.Windows.Forms.BindingSource.Sort%2A> vyžaduje standardní syntaxi ADO.NET: řetězec představující název sloupce dat ve zdroji dat následovaný `ASC` nebo `DESC` k označení, zda má být seznam seřazen ve vzestupném nebo sestupném pořadí. Můžete nastavit pokročilé řazení nebo řazení více sloupců tím, že každý sloupec oddělíte oddělovačem čárky. Vlastnost <xref:System.Windows.Forms.BindingSource.Filter%2A> přijímá řetězcový výraz.  
  
> [!NOTE]
> Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>Filtrování dat pomocí objektu BindingSource  
  
- Vlastnost <xref:System.Windows.Forms.BindingSource.Filter%2A> nastavte na výraz, který chcete.  
  
     V následujícím příkladu kódu je výraz název sloupce následovaný hodnotou, kterou chcete pro sloupec.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Řazení dat pomocí objektu BindingSource  
  
1. Vlastnost <xref:System.Windows.Forms.BindingSource.Sort%2A> nastavte na název sloupce, který požadujete, a za ním `ASC` nebo `DESC` určete vzestupné nebo sestupné pořadí.  
  
2. Oddělte více sloupců čárkou.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu načte data z tabulky Customers ukázkové databáze Northwind do ovládacího prvku <xref:System.Windows.Forms.DataGridView> a filtruje a seřadí zobrazená data.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li spustit tento příklad, vložte kód do formuláře obsahujícího <xref:System.Windows.Forms.BindingSource> s názvem `BindingSource1` a <xref:System.Windows.Forms.DataGridView> s názvem `dataGridView1`. Zpracujte událost <xref:System.Windows.Forms.Form.Load> pro formulář a volejte `InitializeSortedFilteredBindingSource` v metodě obslužné rutiny události Load.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [Postupy: Instalace ukázkových databází](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [Komponenta BindingSource](bindingsource-component.md)
