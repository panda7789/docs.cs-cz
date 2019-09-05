---
title: Generování SQL ve zprostředkovateli ukázek
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: d0e058cdc4dd3f7a1a04ab6eea5acf4d3deabb89
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248510"
---
# <a name="sql-generation-in-the-sample-provider"></a>Generování SQL ve zprostředkovateli ukázek
[Poskytovatel ukázkového Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ukazuje nové komponenty zprostředkovatelů dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Funguje s databází SQL Server 2005 a je implementována jako obálka pro System. data. SqlClient ADO.NET 2,0 Zprostředkovatel dat.  
  
 Modul pro generování SQL ukázkového poskytovatele (umístěný ve složce generování SQL, s výjimkou souboru DmlSqlGenerator.cs) přebírá vstupní DbQueryCommandTree a vytváří jeden příkaz SQL SELECT.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Tento oddíl obsahuje následující témata:  
  
 [Architektura a návrh](architecture-and-design.md)  
  
 [Návod: Generování SQL](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>Viz také:

- [Generování SQL](sql-generation.md)
