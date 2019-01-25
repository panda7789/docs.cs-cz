---
title: Mapování datových typů ODBC
ms.date: 03/30/2017
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
ms.openlocfilehash: f57ba69a03837805f168cf33a9b8060633a6330f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724223"
---
# <a name="odbc-data-type-mappings"></a>Mapování datových typů ODBC
V následující tabulce jsou uvedeny odvozené [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu pro typy dat od zprostředkovatele dat .NET Framework pro ODBC (<xref:System.Data.Odbc>). Zadaný přístupové metody pro <xref:System.Data.Odbc.OdbcDataReader> jsou také uvedeny.  
  
|Typ rozhraní ODBC|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Typ|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zadaný přístupový objekt|  
|---------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|SQL_BIGINT|Int64|GetInt64()|  
|SQL_BINARY|Byte]|GetBytes()|  
|SQL_BIT|Boolean|GetBoolean()|  
|SQL_CHAR|String<br /><br /> Char]|GetString()<br /><br /> GetChars()|  
|SQL_DECIMAL|Desetinné číslo|GetDecimal()|  
|SQL_DOUBLE|Double|GetDouble()|  
|SQL_GUID|Guid|GetGuid()|  
|SQL_INTEGER|Int32|GetInt32()|  
|SQL_LONG_VARCHAR|String<br /><br /> Char]|GetString()<br /><br /> GetChars()|  
|SQL_LONGVARBINARY|Byte]|GetBytes()|  
|SQL_NUMERIC|Desetinné číslo|GetDecimal()|  
|SQL_REAL|Single|GetFloat()|  
|SQL_SMALLINT|Int16|GetInt16()|  
|SQL_TINYINT|Byte|GetByte()|  
|SQL_TYPE_TIMES|DateTime|GetDateTime()|  
|SQL_TYPE_TIMESTAMP|DateTime|GetDateTime()|  
|SQL_VARBINARY|Byte]|GetBytes()|  
|SQL_WCHAR|String<br /><br /> Char]|GetString()<br /><br /> GetChars()|  
|SQL_WLONGVARCHAR|String<br /><br /> Char]|GetString()<br /><br /> GetChars()|  
|SQL_WVARCHAR|String<br /><br /> Char]|GetString()<br /><br /> GetChars()|  
  
## <a name="see-also"></a>Viz také:
- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
