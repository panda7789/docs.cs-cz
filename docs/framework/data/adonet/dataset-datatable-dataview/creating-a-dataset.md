---
title: Vytvoření datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 3c48b430b1a087a79db37398b2c68014b8077c55
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755962"
---
# <a name="creating-a-dataset"></a>Vytvoření datové sady
Vytvoření instance <xref:System.Data.DataSet> voláním <xref:System.Data.DataSet> konstruktor. Volitelně můžete zadáte název argument. Pokud nezadáte název <xref:System.Data.DataSet>, název nastavena na "NewDataSet".  
  
 Můžete také vytvořit novou <xref:System.Data.DataSet> na základě existujícího <xref:System.Data.DataSet>. Nové <xref:System.Data.DataSet> lze přesnou kopii existující <xref:System.Data.DataSet>; klon <xref:System.Data.DataSet> který zkopíruje relační struktury nebo schématu, ale který neobsahuje žádná data z existující <xref:System.Data.DataSet>; nebo podmnožinu <xref:System.Data.DataSet>, obsahující pouze změněné řádky z existující <xref:System.Data.DataSet> pomocí <xref:System.Data.DataSet.GetChanges%2A> metoda. Další informace najdete v tématu [kopírování obsahu datovou sadu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).  
  
 Následující příklad kódu ukazuje, jak vytvořit instanci <xref:System.Data.DataSet>.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Viz také  
 [Naplnění datové sady z adaptéru dat](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
