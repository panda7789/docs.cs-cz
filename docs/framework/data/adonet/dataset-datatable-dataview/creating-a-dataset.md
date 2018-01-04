---
title: "Vytvoření datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8ae997822d71a0a0a4276b8b32b963149a8ed67a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
