---
title: 'Postupy: Řazení a filtrování dat ADO.NET pomocí komponenty Windows Forms BindingSource'
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
ms.openlocfilehash: ae331ca9e3fd2aed654659e11434454874eff8fa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960410"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Postupy: Řazení a filtrování dat ADO.NET pomocí komponenty Windows Forms BindingSource
Schopnost <xref:System.Windows.Forms.BindingSource> řazení a filtrování ovládacího prvku můžete vystavit <xref:System.Windows.Forms.BindingSource.Sort%2A> prostřednictvím vlastností a <xref:System.Windows.Forms.BindingSource.Filter%2A> . Když je <xref:System.ComponentModel.IBindingList>podkladový zdroj dat, můžete použít jednoduché řazení <xref:System.ComponentModel.IBindingListView>. Pokud je zdrojem dat, můžete použít filtrování a rozšířené řazení. Vlastnost vyžaduje standardní syntaxi ADO.NET: řetězec představující název sloupce dat ve zdroji dat `ASC` následovaný nebo `DESC` , který označuje, jestli se má seznam seřadit ve vzestupném nebo sestupném pořadí. <xref:System.Windows.Forms.BindingSource.Sort%2A> Můžete nastavit pokročilé řazení nebo řazení více sloupců tím, že každý sloupec oddělíte oddělovačem čárky. <xref:System.Windows.Forms.BindingSource.Filter%2A> Vlastnost přebírá řetězcový výraz.  
  
> [!NOTE]
> Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>Filtrování dat pomocí objektu BindingSource  
  
- <xref:System.Windows.Forms.BindingSource.Filter%2A> Nastavte vlastnost na výraz, který chcete.  
  
     V následujícím příkladu kódu je výraz název sloupce následovaný hodnotou, kterou chcete pro sloupec.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Řazení dat pomocí objektu BindingSource  
  
1. Nastavte vlastnost na název sloupce, který požadujete, a `ASC` za něj `DESC` určete vzestupné nebo sestupné pořadí. <xref:System.Windows.Forms.BindingSource.Sort%2A>  
  
2. Oddělte více sloupců čárkou.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu načte data z tabulky Customers ukázkové databáze Northwind do <xref:System.Windows.Forms.DataGridView> ovládacího prvku a filtruje a seřadí zobrazená data.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li spustit tento příklad, vložte kód <xref:System.Windows.Forms.BindingSource> do formuláře obsahujícího pojmenované `BindingSource1` a <xref:System.Windows.Forms.DataGridView> pojmenované `dataGridView1`. Zpracujte událost pro formulář a zavolejte `InitializeSortedFilteredBindingSource` metodu obslužné rutiny události načtení. <xref:System.Windows.Forms.Form.Load>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [Postupy: Instalace ukázkových databází](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [Komponenta BindingSource](bindingsource-component.md)
