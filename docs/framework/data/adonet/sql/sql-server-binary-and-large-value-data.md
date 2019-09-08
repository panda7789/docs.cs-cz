---
title: Binární a vysoké hodnoty na SQL Serveru
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4d941ad6b7865112b45fd8c20ad89e9236e17b9d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791684"
---
# <a name="sql-server-binary-and-large-value-data"></a>Binární a vysoké hodnoty na SQL Serveru
SQL Server poskytuje `max` specifikátor, který rozšiřuje kapacitu `varchar`úložiště, `nvarchar`a `varbinary` datové typy. `varchar(max)`, `nvarchar(max)` a`varbinary(max)` jsou souhrnně označovány jako *datové typy velkých hodnot*. Datové typy s velkými hodnotami můžete použít k ukládání až 2 ^ 31-1 bajtů dat.  
  
 SQL Server 2008 zavádí atribut FILESTREAM, který není datovým typem, ale spíše atribut, který může být definován ve sloupci a umožňuje uložení velkých hodnot do systému souborů místo do databáze.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Úprava vysokých (maximálních) hodnot v ADO.NET](modifying-large-value-max-data.md)  
 Popisuje, jak pracovat s datovými typy s velkými hodnotami.  
  
 [Data FILESTREAM](filestream-data.md)  
 Popisuje, jak pracovat s daty ve velkých hodnotách, které jsou uloženy v SQL Server 2008 s atributem FILESTREAM.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy SQL Serveru a ADO.NET](sql-server-data-types.md)
- [Operace dat na SQL Serveru v ADO.NET](sql-server-data-operations.md)
- [Načítání a úpravy dat v ADO.NET](../retrieving-and-modifying-data.md)
- [Přehled ADO.NET](../ado-net-overview.md)
