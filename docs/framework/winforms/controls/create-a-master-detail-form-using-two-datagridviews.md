---
title: 'Postupy: Vytvoření hlavního a podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: ccd9354d623cf1b452bc3890b7fd9a5248cb69c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011525"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Postupy: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView
Následující příklad kódu vytvoří hlavního/podrobného formuláře pomocí dvou <xref:System.Windows.Forms.DataGridView> ovládací prvky vázané na dva <xref:System.Windows.Forms.BindingSource> komponenty. Zdroj dat je <xref:System.Data.DataSet> obsahující `Customers` a `Orders` tabulek z ukázkové databáze Northwind SQL Server spolu s <xref:System.Data.DataRelation> , který se týká obou prostřednictvím `CustomerID` sloupec.  
  
 Jeden <xref:System.Windows.Forms.BindingSource> je vázán na nadřazený prvek `Customers` tabulky v datové sadě. Tato data se zobrazí v hlavním <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Druhý <xref:System.Windows.Forms.BindingSource> je vázán na první datový konektor. <xref:System.Windows.Forms.BindingSource.DataMember%2A> Vlastnost druhého <xref:System.Windows.Forms.BindingSource> nastavena <xref:System.Data.DataRelation> název. To způsobí, že související podrobnosti <xref:System.Windows.Forms.DataGridView> ovládací prvek pro zobrazení řádků z podřízených `Orders` tabulku, která odpovídá aktuální řádek v hlavní databázi <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 Úplné vysvětlení tento příklad kódu naleznete v tématu [názorný postup: Vytvoření hlavního/podrobného formuláře pomocí dvou Windows Forms DataGridView – ovládací prvky](creating-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
 Odkazy na sestavení systému, System.Data, System.Windows.Forms a System.XML.  
  
- Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ukládání citlivých informací, jako jsou hesla, v rámci připojovací řetězec může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Návod: Vytvoření hlavního/podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView](creating-a-master-detail-form-using-two-datagridviews.md)
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
