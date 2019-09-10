---
title: Generování SQL ve zprostředkovateli ukázek
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: a59f1fecf85d63208c3388204c962b5838902ba7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854314"
---
# <a name="sql-generation-in-the-sample-provider"></a>Generování SQL ve zprostředkovateli ukázek
[Poskytovatel ukázkového Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ukazuje nové komponenty zprostředkovatelů dat ADO.NET, které podporují Entity Framework.  Funguje s databází SQL Server 2005 a je implementována jako obálka pro System. data. SqlClient ADO.NET 2,0 Zprostředkovatel dat.  
  
 Modul pro generování SQL ukázkového poskytovatele (umístěný ve složce generování SQL, s výjimkou souboru DmlSqlGenerator.cs) přebírá vstupní DbQueryCommandTree a vytváří jeden příkaz SQL SELECT.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Tento oddíl obsahuje následující témata:  
  
 [Architektura a návrh](architecture-and-design.md)  
  
 [Návod: Generování SQL](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>Viz také:

- [Generování SQL](sql-generation.md)
