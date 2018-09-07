---
title: 'Postupy: Řazení a filtrování dat ADO.NET pomocí součásti Windows Forms BindingSource'
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
ms.openlocfilehash: 932d30d356225d88d7ef149561cc4c5cc8ac4dd0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44067935"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Postupy: Řazení a filtrování dat ADO.NET pomocí součásti Windows Forms BindingSource
Můžete zveřejnit řazení a filtrování schopnost <xref:System.Windows.Forms.BindingSource> řídit prostřednictvím <xref:System.Windows.Forms.BindingSource.Sort%2A> a <xref:System.Windows.Forms.BindingSource.Filter%2A> vlastnosti. Můžete provést jednoduché řazení podkladovým zdrojem dat je <xref:System.ComponentModel.IBindingList>, a můžete použít filtrování a rozšířené řazení, pokud je zdroj dat <xref:System.ComponentModel.IBindingListView>. <xref:System.Windows.Forms.BindingSource.Sort%2A> Vlastnost vyžaduje standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] syntaxe: řetězec představující název sloupce dat ve zdroji dat, za nímž následuje `ASC` nebo `DESC` označující, zda mají být řazeny seznam ve vzestupném nebo sestupném pořadí. Můžete nastavit rozšířené řazení nebo řazení více sloupců tak, že oddělíte každý sloupec s oddělovačem čárkou. <xref:System.Windows.Forms.BindingSource.Filter%2A> Vlastnost přebírá řetězcového výrazu.  
  
> [!NOTE]
>  Ukládání citlivých informací, jako jsou hesla, v rámci připojovací řetězec může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>K filtrování dat pomocí objektu BindingSource  
  
-   Nastavte <xref:System.Windows.Forms.BindingSource.Filter%2A> vlastnost pro výraz, který chcete.  
  
     Výraz v následujícím příkladu kódu je název sloupce zadáte hodnotu, která chcete použít pro sloupec.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Řazení dat pomocí BindingSource  
  
1.  Nastavte <xref:System.Windows.Forms.BindingSource.Sort%2A> nastavte na název sloupce, který chcete, za nímž následuje `ASC` nebo `DESC` označíte, vzestupném nebo sestupném pořadí.  
  
2.  Oddělte čárkou více sloupců.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu načte data z tabulky Customers v ukázkové databázi Northwind <xref:System.Windows.Forms.DataGridView> ovládací prvek a filtry a seřadí zobrazená data.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li spustit tento příklad, vložte kód do formuláře, který obsahuje <xref:System.Windows.Forms.BindingSource> s názvem `BindingSource1` a <xref:System.Windows.Forms.DataGridView> s názvem `dataGridView1`. Zpracování <xref:System.Windows.Forms.Form.Load> událost pro formulář opravdu zavřít a volání `InitializeSortedFilteredBindingSource` v metodě obslužné rutiny události load.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [Postupy: Instalace ukázkových databází](https://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [Komponenta BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)
