---
title: Mapování datových typů OLE DB
ms.date: 03/30/2017
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
ms.openlocfilehash: a5c4b7264b9f8abb842fff3295d53ed8ab626671
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584522"
---
# <a name="ole-db-data-type-mappings"></a>Mapování datových typů OLE DB
V následující tabulce jsou uvedeny odvozený typ rozhraní .NET Framework pro datové typy z zprostředkovatele dat .NET Framework pro ADO a technologie OLE DB (<xref:System.Data.OleDb>). Zadaný přístupové metody pro <xref:System.Data.OleDb.OleDbDataReader> jsou také uvedeny.  
  
|Typ rozhraní ADO|Typ OLE DB|Typ rozhraní .NET Framework|Zadaný přístupový objekt rozhraní .NET framework|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte[]|GetBytes()|  
|adBoolean|DBTYPE_BOOL|Boolean|GetBoolean()|  
|adBSTR|DBTYPE_BSTR|String|GetString()|  
|adChapter|DBTYPE_HCHAPTER|Podporují `DataReader`. Zobrazit [načítání dat pomocí čtečky dat](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).|GetValue()|  
|adChar|TYPEM DBTYPE_STR|String|GetString()|  
|adCurrency|DBTYPE_CY|Desetinné číslo|GetDecimal()|  
|adDate|TYPU DBTYPE_DATE|DateTime|GetDateTime()|  
|adDBDate|DBTYPE_DBDATE|DateTime|GetDateTime()|  
|adDBTime|DBTYPE_DBTIME|DateTime|GetDateTime()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|DateTime|GetDateTime()|  
|adDecimal|DBTYPE_DECIMAL|Desetinné číslo|GetDecimal()|  
|adDouble|DBTYPE_R8|Double|GetDouble()|  
|adError|DBTYPE_ERROR|ExternalException|GetValue()|  
|adFileTime|TYP DBTYPE_FILETIME|DateTime|GetDateTime()|  
|adGUID|DBTYPE_GUID|Guid|GetGuid()|  
|adIDispatch|DBTYPE_IDISPATCH *|Objekt|GetValue()|  
|adInteger|DBTYPE_I4|Int32|GetInt32()|  
|adIUnknown|DBTYPE_IUNKNOWN *|Objekt|GetValue()|  
|adNumeric|DBTYPE_NUMERIC|Desetinné číslo|GetDecimal()|  
|adPropVariant|DBTYPE_PROPVARIANT|Objekt|GetValue()|  
|adSingle|DBTYPE_R4|Single|GetFloat()|  
|adSmallInt|DBTYPE_I2|Int16|GetInt16()|  
|adTinyInt|DBTYPE_I1|Byte|GetByte()|  
|adUnsignedBigInt|DBTYPE_UI8|UInt64|GetValue()|  
|adUnsignedInt|DBTYPE_UI4|UInt32|GetValue()|  
|adUnsignedSmallInt|DBTYPE_UI2|UInt16|GetValue()|  
|adUnsignedTinyInt|DBTYPE_UI1|Byte|GetByte()|  
|adVariant|DBTYPE_VARIANT|Objekt|GetValue()|  
|adWChar|DBTYPE_WSTR|String|GetString()|  
|adUserDefined|DBTYPE_UDT|Nepodporuje se||  
|adVarNumeric|DBTYPE_VARNUMERIC|Nepodporuje se||  
  
 \* U typů OLE DB `DBTYPE_IUNKNOWN` a `DBTYPE_IDISPATCH`, zařazené reprezentaci ukazatele je odkaz na objekt.  
  
## <a name="see-also"></a>Viz také:

- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
