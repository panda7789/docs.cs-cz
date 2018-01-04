---
title: "Mapování datového typu rozhraní ODBC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f6f4e63b731f4e8088e86766e258f77cdd0eeff9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="odbc-data-type-mappings"></a>Mapování datového typu rozhraní ODBC
V následující tabulce jsou uvedeny odvozené [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ pro datové typy z zprostředkovatel dat .NET Framework pro ODBC (<xref:System.Data.Odbc>). Typové přístupových metod pro <xref:System.Data.Odbc.OdbcDataReader> jsou také uvedeny.  
  
|Typ rozhraní ODBC|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]Typ|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]typy přistupujícího objektu|  
|---------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|SQL_BIGINT|Int64|GetInt64()|  
|SQL_BINARY|Byte]|GetBytes()|  
|SQL_BIT|Boolean|GetBoolean()|  
|SQL_CHAR|String<br /><br /> Char]|Funkci GetString()<br /><br /> GetChars()|  
|SQL_DECIMAL|Desetinné číslo|GetDecimal()|  
|SQL_DOUBLE|Double|GetDouble()|  
|SQL_GUID|Identifikátor GUID|GetGuid()|  
|SQL_INTEGER|Int32|GetInt32()|  
|SQL_LONG_VARCHAR|String<br /><br /> Char]|Funkci GetString()<br /><br /> GetChars()|  
|SQL_LONGVARBINARY|Byte]|GetBytes()|  
|SQL_NUMERIC|Desetinné číslo|GetDecimal()|  
|SQL_REAL|Single|GetFloat()|  
|SQL_SMALLINT|Int16|GetInt16()|  
|SQL_TINYINT|Byte|GetByte()|  
|SQL_TYPE_TIMES|DateTime|GetDateTime()|  
|SQL_TYPE_TIMESTAMP|DateTime|GetDateTime()|  
|SQL_VARBINARY|Byte]|GetBytes()|  
|SQL_WCHAR|String<br /><br /> Char]|Funkci GetString()<br /><br /> GetChars()|  
|SQL_WLONGVARCHAR|String<br /><br /> Char]|Funkci GetString()<br /><br /> GetChars()|  
|SQL_WVARCHAR|String<br /><br /> Char]|Funkci GetString()<br /><br /> GetChars()|  
  
## <a name="see-also"></a>Viz také  
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
