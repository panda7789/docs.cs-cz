---
title: Generování SQL ve zprostředkovateli ukázek
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: 88223930b65ccec9d030104c62d8b4b2e77ddbe2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079412"
---
# <a name="sql-generation-in-the-sample-provider"></a>Generování SQL ve zprostředkovateli ukázek
[Ukázka zprostředkovatele Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ukazuje nových komponent zprostředkovatele dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Funguje s databází serveru SQL Server 2005 a je implementovaný jako obálka pro zprostředkovatele System.Data.SqlClient ADO.NET 2.0 Data.  
  
 Modul generování SQL zprostředkovateli ukázek (umístěný ve složce generování SQL, s výjimkou souboru DmlSqlGenerator.cs) přijímá vstupní DbQueryCommandTree a vytváří jeden příkaz SQL SELECT.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Tento oddíl obsahuje následující témata:  
  
 [Architektura a návrh](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [Návod: Generování SQL](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>Viz také:

- [Generování SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
