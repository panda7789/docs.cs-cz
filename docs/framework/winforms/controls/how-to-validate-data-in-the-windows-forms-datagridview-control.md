---
title: Ověřit data v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: 5fd881829f87fa1dec135d936f22996f196b0594
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728306"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a>Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView
Následující příklad kódu ukazuje, jak ověřit data zadaná uživatelem do ovládacího prvku <xref:System.Windows.Forms.DataGridView>. V tomto příkladu je <xref:System.Windows.Forms.DataGridView> vyplněno řádky z tabulky `Customers` ukázkové databáze Northwind. Když uživatel upraví buňku ve sloupci `CompanyName`, je její hodnota testována na platnosti tím, že zkontroluje, že není prázdná. Pokud obslužná rutina události pro událost <xref:System.Windows.Forms.DataGridView.CellValidating> zjistí, že hodnota je prázdný řetězec, <xref:System.Windows.Forms.DataGridView> zabrání uživateli v ukončení buňky, dokud nebude zadán neprázdný řetězec.  
  
 Úplný popis tohoto příkladu kódu naleznete [v tématu Návod: ověřování dat v ovládacím prvku DataGridView model Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. data, System. Windows. Forms a System. XML.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
- [Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
