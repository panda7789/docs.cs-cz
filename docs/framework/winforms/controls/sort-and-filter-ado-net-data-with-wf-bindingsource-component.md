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
ms.openlocfilehash: 3b58c4f3a53156ab01fb0c0c46b9a9b8d3fea84b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538062"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Postupy: Řazení a filtrování dat ADO.NET pomocí součásti Windows Forms BindingSource
Můžete vystavit řazení a filtrování funkce <xref:System.Windows.Forms.BindingSource> ovládat prostřednictvím <xref:System.Windows.Forms.BindingSource.Sort%2A> a <xref:System.Windows.Forms.BindingSource.Filter%2A> vlastnosti. Jednoduché řazení, pokud je základní zdroj dat můžete použít <xref:System.ComponentModel.IBindingList>, a můžete použít filtrování a rozšířené řazení, pokud je zdroj dat <xref:System.ComponentModel.IBindingListView>. <xref:System.Windows.Forms.BindingSource.Sort%2A> Vlastnost vyžaduje standardní [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] syntaxe: následuje řetězec představující název sloupce dat ve zdroji dat `ASC` nebo `DESC` indikující, zda v seznamu musí být seřazeny ve vzestupném nebo sestupném pořadí. Můžete nastavit pokročilé řazení nebo více sloupci řazení oddělením každý sloupec s oddělovačem čárkami. <xref:System.Windows.Forms.BindingSource.Filter%2A> Vlastnost trvá řetězcového výrazu.  
  
> [!NOTE]
>  Ukládání citlivé informace, jako jsou hesla, v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>K filtrování dat pomocí BindingSource  
  
-   Nastavte <xref:System.Windows.Forms.BindingSource.Filter%2A> vlastnost, která má výraz, který chcete.  
  
     V následujícím příkladu kódu je výraz název sloupce, za nímž následuje hodnotu, která chcete použít pro sloupec.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Řazení dat pomocí BindingSource  
  
1.  Nastavte <xref:System.Windows.Forms.BindingSource.Sort%2A> vlastnost na název sloupce, který chcete, za nímž následuje `ASC` nebo `DESC` k označení vzestupném nebo sestupném pořadí.  
  
2.  Více sloupců oddělte čárkou.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu načte data z tabulky Zákazníci ukázková databáze Northwind do <xref:System.Windows.Forms.DataGridView> řídit a filtry a seřadí zobrazená data.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pro spuštění tohoto příkladu, vložte kód do formuláře, který obsahuje <xref:System.Windows.Forms.BindingSource> s názvem `BindingSource1` a <xref:System.Windows.Forms.DataGridView> s názvem `dataGridView1`. Zpracování <xref:System.Windows.Forms.Form.Load> události pro formulář a volání `InitializeSortedFilteredBindingSource` v obslužná rutina události zatížení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [Postupy: Instalace ukázkových databází](http://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [Komponenta BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)
