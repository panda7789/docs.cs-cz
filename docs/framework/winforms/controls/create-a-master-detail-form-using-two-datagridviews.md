---
title: Vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: d317f4e592790c9b48b539b1601814569e14529f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737330"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Postupy: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView
Následující příklad kódu vytvoří hlavní a podrobný formulář pomocí dvou <xref:System.Windows.Forms.DataGridView>ch ovládacích prvků vázaných na dvě komponenty <xref:System.Windows.Forms.BindingSource>. Zdroj dat je <xref:System.Data.DataSet>, který obsahuje tabulky `Customers` a `Orders` ze vzorové databáze Northwind SQL Server společně s <xref:System.Data.DataRelation>, který vztahují dva sloupce `CustomerID`.  
  
 Jedna <xref:System.Windows.Forms.BindingSource> je svázána s nadřazenou `Customers` tabulkou v datové sadě. Tato data se zobrazí v ovládacím prvku hlavní <xref:System.Windows.Forms.DataGridView>. Druhý <xref:System.Windows.Forms.BindingSource> je svázán s prvním datovým konektorem. Vlastnost <xref:System.Windows.Forms.BindingSource.DataMember%2A> druhého <xref:System.Windows.Forms.BindingSource> je nastavena na hodnotu <xref:System.Data.DataRelation> název. To způsobí, že přidružený ovládací prvek <xref:System.Windows.Forms.DataGridView> ovládacího prvku zobrazit řádky podřízené tabulky `Orders`, která odpovídá aktuálnímu řádku v ovládacím prvku hlavní <xref:System.Windows.Forms.DataGridView>.  
  
 Úplný popis tohoto příkladu kódu naleznete v tématu [Návod: Vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků model Windows Forms DataGridView](creating-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
 Odkazy na sestavení System, System. data, System. Windows. Forms a System. XML.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Návod: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView](creating-a-master-detail-form-using-two-datagridviews.md)
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
