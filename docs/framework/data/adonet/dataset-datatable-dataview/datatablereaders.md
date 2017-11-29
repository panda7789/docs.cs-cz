---
title: DataTableReaders
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ed9094a036262bac2e101e7b4268aac2e66a0d10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="datatablereaders"></a>DataTableReaders
<xref:System.Data.DataTableReader> Uvede obsah <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> ve formě jednoho nebo více jen pro čtení, dopředné výsledek nastaví.  
  
 Při vytváření **třída DataTableReader** z **DataTable**, výsledná **třída DataTableReader** objekt obsahuje jedna sada výsledků s stejná data jako  **DataTable** ze které byla vytvořena, s výjimkou všechny řádky, které byly označeny jako odstraněný. Se sloupce zobrazí ve stejném pořadí jako původní **DataTable**.  
  
 A **třída DataTableReader** může obsahovat více sad výsledků dotazu, pokud byla vytvořena pomocí volání <xref:System.Data.DataSet.CreateDataReader%2A>. Výsledky jsou ve stejném pořadí jako **DataTables** v **datovou sadu** objektu <xref:System.Data.DataSet.Tables%2A> kolekce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytváření DataReader –](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 Popisuje, jak vytvořit **třída DataTableReader** objektu.  
  
 [Navigace DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 Popisuje použití **čtení** metoda Chcete-li procházet obsah **třída DataTableReader**.  
  
## <a name="see-also"></a>Viz také  
 [Načítání a upravovat Data v technologii ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
