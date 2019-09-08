---
title: 'Postupy: Připojení objektu DataView k ovládacímu prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 3a3089073cdc5afb4ee51caca9114b401c740b45
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795001"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a>Postupy: Připojení objektu DataView k ovládacímu prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Ovládací prvek poskytuje výkonný a flexibilní způsob zobrazení dat v tabulkovém formátu. Ovládací prvek podporuje model standardní model Windows Forms datové vazby, takže se váže k <xref:System.Data.DataView> celé řadě dalších zdrojů dat. <xref:System.Windows.Forms.DataGridView> Ve většině případů se ale budete Přivážete k <xref:System.Windows.Forms.BindingSource> součásti, která bude spravovat podrobnosti o interakci se zdrojem dat.  
  
 Další informace o <xref:System.Windows.Forms.DataGridView> ovládacím prvku naleznete v tématu [Přehled ovládacího prvku DataGridView](../../winforms/controls/datagridview-control-overview-windows-forms.md).  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a>Připojení ovládacího prvku DataGridView k zobrazení dat  
  
1. Implementujte metodu pro zpracování podrobností o načítání dat z databáze. Následující příklad kódu implementuje `GetData` metodu, která <xref:System.Data.SqlClient.SqlDataAdapter> inicializuje komponentu a <xref:System.Data.DataSet>používá ji k naplnění. Nezapomeňte nastavit `connectionString` proměnnou na hodnotu, která je vhodná pro vaši databázi. Budete potřebovat přístup k serveru s nainstalovanou ukázkovou databází AdventureWorks SQL Server.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. V obslužné rutině <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingSource> `GetData` události ve formuláři svažte ovládací prvek s komponentou a zavolejte metodu pro načtení dat z databáze. <xref:System.Windows.Forms.Form.Load> Vytvoří se z LINQ to DataSetového dotazu přes kontakt <xref:System.Data.DataTable> a pak <xref:System.Windows.Forms.BindingSource> se naváže na komponentu. <xref:System.Data.DataView>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a>Viz také:

- [Datová vazba a LINQ to DataSet](data-binding-and-linq-to-dataset.md)
