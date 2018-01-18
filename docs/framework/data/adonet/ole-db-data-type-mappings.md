---
title: "Mapování datového typu OLE DB"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 407f194a8530f9b9e4241a6bdb4d26a4b891aa46
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="ole-db-data-type-mappings"></a>Mapování datového typu OLE DB
V následující tabulce jsou uvedeny odvozené [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ pro datové typy z zprostředkovatel dat .NET Framework pro ADO a OLE DB (<xref:System.Data.OleDb>). Typové přístupových metod pro <xref:System.Data.OleDb.OleDbDataReader> jsou také uvedeny.  
  
|Typ ADO|Typ OLE DB|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]Typ|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]typy přistupujícího objektu|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte[]|GetBytes()|  
|adBoolean|DBTYPE_BOOL|Boolean|GetBoolean()|  
|adBSTR|DBTYPE_BSTR|String|GetString()|  
|adChapter|DBTYPE_HCHAPTER|Podporované prostřednictvím `DataReader`. V tématu [načítání dat pomocí DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).|GetValue()|  
|adChar|DBTYPE_STR|String|GetString()|  
|adCurrency|DBTYPE_CY|Desetinné číslo|GetDecimal()|  
|adDate|DBTYPE_DATE|DateTime|GetDateTime()|  
|adDBDate|DBTYPE_DBDATE|DateTime|GetDateTime()|  
|adDBTime|DBTYPE_DBTIME|DateTime|GetDateTime()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|DateTime|GetDateTime()|  
|adDecimal|DBTYPE_DECIMAL|Desetinné číslo|GetDecimal()|  
|adDouble|DBTYPE_R8|Double|GetDouble()|  
|adError|DBTYPE_ERROR|ExternalException –|GetValue()|  
|adFileTime|DBTYPE_FILETIME|DateTime|GetDateTime()|  
|adGUID|DBTYPE_GUID|Identifikátor GUID|GetGuid()|  
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
  
 \*Pro typy OLE DB `DBTYPE_IUNKNOWN` a `DBTYPE_IDISPATCH`, odkaz na objekt je zařazené reprezentace ukazatele.  
  
## <a name="see-also"></a>Viz také  
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
