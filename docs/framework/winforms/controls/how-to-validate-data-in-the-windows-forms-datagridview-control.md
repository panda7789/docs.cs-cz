---
title: 'Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 349ea28fe1fd82c1b547018f62273be89ff2db8d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591421"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a>Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView
Následující příklad kódu ukazuje, jak ověřit data zadaná uživatelem do <xref:System.Windows.Forms.DataGridView> ovládacího prvku. V tomto příkladu <xref:System.Windows.Forms.DataGridView> se naplní řádky z `Customers` tabulky ukázkové databáze Northwind. Když uživatel upravuje buňky v `CompanyName` sloupec, jeho hodnota je testována platnost tak, že zkontrolujete, že není prázdná. Pokud obslužná rutina události pro <xref:System.Windows.Forms.DataGridView.CellValidating> události zjistí, že hodnota je prázdný řetězec, <xref:System.Windows.Forms.DataGridView> znemožní uživateli ukončení buňku, dokud nebude zadán neprázdný řetězec.  
  
 Úplné vysvětlení tento příklad kódu naleznete v tématu [názorný postup: Ověřování dat v Windows Forms DataGridView – ovládací prvek](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému, System.Data, System.Windows.Forms a System.XML.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ukládání citlivých informací, jako jsou hesla, v rámci připojovací řetězec může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
- [Návod: Zpracování chyb vzniklých při zadávání dat v ovládacím prvku Windows Forms DataGridView](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
