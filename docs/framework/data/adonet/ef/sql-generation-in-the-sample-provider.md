---
title: Generování SQL ve zprostředkovateli ukázek
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: b2397570bb5f312aa6a3955a76234bde508fcc6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505497"
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
