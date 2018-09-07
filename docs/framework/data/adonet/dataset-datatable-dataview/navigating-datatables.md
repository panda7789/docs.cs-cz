---
title: Navigace v datových tabulkách
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: f00e2171c1adf4ff99a669085131ebc8d38f7006
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44063050"
---
# <a name="navigating-datatables"></a>Navigace v datových tabulkách
<xref:System.Data.DataTableReader> Získá obsah jednoho nebo více <xref:System.Data.DataTable> objekty ve formě jednoho nebo více sad výsledků dotazu jen pro čtení, pouze vpřed.  
  
 A <xref:System.Data.DataTableReader> může obsahovat více sad výsledků dotazu, pokud je vytvořena pomocí <xref:System.Data.DataSet.CreateDataReader%2A> metody. Po více než jednu sadu výsledků, <xref:System.Data.DataTableReader.NextResult%2A> metoda Posune kurzor na další sadu výsledků. Jedná se o proces pouze vpřed. Není možné vrátit na předchozí sadu výsledků dotazu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `TestConstructor` metoda vytvoří dva <xref:System.Data.DataTable> instancí. Pro ukázání tento konstruktor pro <xref:System.Data.DataTableReader> třídy, vzorovým kódem se vytvoří nový **třída DataTableReader** na základě pole, která obsahuje dvě **DataTables**a provádí jednoduché operace Tisk obsahu z prvního několik sloupců do okna konzoly.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Čtečky datových tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
