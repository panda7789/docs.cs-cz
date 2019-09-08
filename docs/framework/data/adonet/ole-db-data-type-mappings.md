---
title: Mapování datových typů OLE DB
ms.date: 03/30/2017
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
ms.openlocfilehash: 969433b2582771a0ed57217180c2795f9359956f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783493"
---
# <a name="ole-db-data-type-mappings"></a>Mapování datových typů OLE DB
Následující tabulka ukazuje odvozený .NET Framework typ pro datové typy z .NET Framework Zprostředkovatel dat pro ADO a OLE DB (<xref:System.Data.OleDb>). V seznamu <xref:System.Data.OleDb.OleDbDataReader> jsou uvedeny i přístupové metody typu pro.  
  
|Typ ADO|Typ OLE DB|Typ rozhraní .NET Framework|Přístupový objekt typu .NET Framework|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte[]|GetBytes ()|  
|adBoolean|DBTYPE_BOOL|Boolean|GetBoolean()|  
|adBSTR|DBTYPE_BSTR|String|GetString ()|  
|adChapter|DBTYPE_HCHAPTER|Podporováno prostřednictvím `DataReader`. Viz [načítání dat pomocí objektu DataReader](retrieving-data-using-a-datareader.md).|GetValue ()|  
|adChar|DBTYPE_STR|String|GetString ()|  
|adCurrency|DBTYPE_CY|Desetinné číslo|GetDecimal ()|  
|adDate|DBTYPE_DATE|DateTime|GetDateTime()|  
|adDBDate|DBTYPE_DBDATE|DateTime|GetDateTime()|  
|adDBTime|DBTYPE_DBTIME|DateTime|GetDateTime()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|DateTime|GetDateTime()|  
|adDecimal|DBTYPE_DECIMAL|Desetinné číslo|GetDecimal ()|  
|adDouble|DBTYPE_R8|Double|GetDouble()|  
|adError|DBTYPE_ERROR|ExternalException –|GetValue ()|  
|adFileTime|DBTYPE_FILETIME|DateTime|GetDateTime()|  
|adGUID|DBTYPE_GUID|Guid|GetGuid()|  
|adIDispatch|DBTYPE_IDISPATCH *|Objekt|GetValue ()|  
|adInteger|DBTYPE_I4|Int32|GetInt32()|  
|adIUnknown|DBTYPE_IUNKNOWN *|Objekt|GetValue ()|  
|adNumeric|DBTYPE_NUMERIC|Desetinné číslo|GetDecimal ()|  
|adPropVariant|DBTYPE_PROPVARIANT|Objekt|GetValue ()|  
|adSingle|DBTYPE_R4|Single|GetFloat()|  
|adSmallInt|DBTYPE_I2|Int16|GetInt16()|  
|adTinyInt|DBTYPE_I1|Byte|GetByte()|  
|adUnsignedBigInt|DBTYPE_UI8|UInt64|GetValue ()|  
|adUnsignedInt|DBTYPE_UI4|UInt32|GetValue ()|  
|adUnsignedSmallInt|DBTYPE_UI2|UInt16|GetValue ()|  
|adUnsignedTinyInt|DBTYPE_UI1|Byte|GetByte()|  
|adVariant|DBTYPE_VARIANT|Objekt|GetValue ()|  
|adWChar|DBTYPE_WSTR|String|GetString ()|  
|adUserDefined|DBTYPE_UDT|nepodporováno||  
|adVarNumeric|DBTYPE_VARNUMERIC|nepodporováno||  
  
 \*Pro OLE DB typy `DBTYPE_IUNKNOWN` a `DBTYPE_IDISPATCH`odkaz na objekt je zařazovací reprezentace ukazatele.  
  
## <a name="see-also"></a>Viz také:

- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
- [Přehled ADO.NET](ado-net-overview.md)
