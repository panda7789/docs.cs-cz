---
title: Mapování datových typů Oracle
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: be478741069e9edd406d73c0b75d5960b9909896
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783420"
---
# <a name="oracle-data-type-mappings"></a>Mapování datových typů Oracle
V následující tabulce jsou uvedeny datové typy Oracle a jejich mapování na <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Datový typ Oracle|.NET Framework datový typ vrácený funkcí OracleDataReader. GetValue|OracleClient datový typ vrácený funkcí OracleDataReader. GetOracleValue|Poznámky|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte []**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte []**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**DATOVÝ TYP CLOB**|**Řetězec**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATUM**|**Hodnotu**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**PLOVÁK**|**Notaci**|<xref:System.Data.OracleClient.OracleNumber>|Tento datový typ je alias pro datový typ **Number** a je navržen tak, <xref:System.Data.OracleClient.OracleDataReader> aby vrátil hodnotu **System. Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo hodnoty s plovoucí desetinnou čárkou. Použití datového typu .NET Framework může způsobit přetečení.|  
|**ČÍSLA**|**Notaci**|<xref:System.Data.OracleClient.OracleNumber>|Tento datový typ je aliasem pro datový typ **Number (38)** a je navržen tak, <xref:System.Data.OracleClient.OracleDataReader> aby vrátí hodnotu **System. Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> namísto celočíselné hodnoty. Použití datového typu .NET Framework může způsobit přetečení.|  
|**INTERVAL OD ROKU DO MĚSÍCE**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**DRUHÝ DEN INTERVALU**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**DLOUHOU**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**DLOUHO NEZPRACOVANÉ**|**Byte []**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Řetězec**|<xref:System.Data.OracleClient.OracleLob>||  
|**AUTOMATICKÉ**|**Notaci**|<xref:System.Data.OracleClient.OracleNumber>|Použití datového typu .NET Framework může způsobit přetečení.|  
|**NVARCHAR2**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**ZÍSKÁNÍ**|**Byte []**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REFERENČNÍ KURZOR**|||Datový typ **odkazu Oracle REF CURSOR** není <xref:System.Data.OracleClient.OracleDataReader> objektem podporován.|  
|**ROWID**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**ČASOVÉ RAZÍTKO**|**Hodnotu**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ČASOVÉ RAZÍTKO S MÍSTNÍM ČASOVÝM PÁSMEM**|**Hodnotu**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ČASOVÉ RAZÍTKO S ČASOVÝM PÁSMEM**|**Hodnotu**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**CELÉ ČÍSLO BEZ ZNAMÉNKA**|**Číslo**|<xref:System.Data.OracleClient.OracleNumber>|Tento datový typ je aliasem pro datový typ **Number (38)** a je navržen tak, <xref:System.Data.OracleClient.OracleDataReader> aby vrátí hodnotu **System. Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo unsigned integer hodnoty. Použití datového typu .NET Framework může způsobit přetečení.|  
|**VARCHAR2**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
  
 V následující tabulce jsou uvedeny datové typy Oracle a datové typy .NET Framework (**System. data. DbType** a <xref:System.Data.OracleClient.OracleType>), které se použijí při vytváření vazby jako parametry.  
  
|Datový typ Oracle|Výčet DbType pro svázání jako parametr|OracleType výčet pro svázání jako parametr|Poznámky|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle umožňuje vytvořit vazbu jako **BFILE** jako parametr **BFILE** . Rozhraní .NET Zprostředkovatel dat pro Oracle je nevytváří automaticky, pokud se pokusíte vytvořit**BFILE** hodnotu, jako je **Byte []** nebo <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Objekt blob**|Oracle umožňuje vytvořit vazbu **objektu BLOB** pouze jako parametr **objektu BLOB** . Rozhraní .NET Zprostředkovatel dat pro Oracle je nevytváří automaticky, pokud se pokusíte vytvořit vazby jiné hodnoty než**objektu BLOB** , například **Byte []** nebo <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**DATOVÝ TYP CLOB**||**Clob**|Oracle umožňuje vytvořit vazbu jako **datový typ CLOB** jako parametr **datový typ CLOB** . Rozhraní .NET Zprostředkovatel dat pro Oracle je nevytváří automaticky, pokud se pokusíte vytvořit vazby**Nedatový typ clobelné** hodnoty, jako je **System. String** nebo <xref:System.Data.OracleClient.OracleString>.|  
|**DATUM**|**Hodnotu**|**Hodnotu**||  
|**PLOVÁK**|**Single, Double, Decimal**|**Float, Double, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Určuje hodnotu **System. data. DbType** a <xref:System.Data.OracleClient.OracleType>.|  
|**ČÍSLA**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Určuje hodnotu **System. data. DbType** a <xref:System.Data.OracleClient.OracleType>.|  
|**INTERVAL OD ROKU DO MĚSÍCE**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType>Nástroj je k dispozici pouze v případě, že používáte klientský i serverový software Oracle 9i.|  
|**DRUHÝ DEN INTERVALU**|**objekt**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType>Nástroj je k dispozici pouze v případě, že používáte klientský i serverový software Oracle 9i.|  
|**DLOUHOU**|**AnsiString**|**LongVarChar**||  
|**DLOUHO NEZPRACOVANÉ**|**Binární**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle umožňuje vytvořit vazbu jako **NCLOB** jako parametr **NCLOB** . Rozhraní .NET Zprostředkovatel dat pro Oracle je nevytváří automaticky, pokud se pokusíte vytvořit vazby**NeNCLOBelné** hodnoty, jako je **System. String** nebo <xref:System.Data.OracleClient.OracleString>.|  
|**AUTOMATICKÉ**|**VarNumeric**|**Číslo**||  
|**NVARCHAR2**|**Řetězec**|**NVarChar**||  
|**ZÍSKÁNÍ**|**Binární**|**Získání**||  
|**REFERENČNÍ KURZOR**||**Kurzor**|Další informace najdete v tématu [referenčních kurzorů Oracle](oracle-ref-cursors.md).|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**ČASOVÉ RAZÍTKO**|**Hodnotu**|**Časové razítko**|<xref:System.Data.OracleClient.OracleType>Nástroj je k dispozici pouze v případě, že používáte klientský i serverový software Oracle 9i.|  
|**ČASOVÉ RAZÍTKO S MÍSTNÍM ČASOVÝM PÁSMEM**|**Hodnotu**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType>Nástroj je k dispozici pouze v případě, že používáte klientský i serverový software Oracle 9i.|  
|**ČASOVÉ RAZÍTKO S ČASOVÝM PÁSMEM**|**Hodnotu**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType>Nástroj je k dispozici pouze v případě, že používáte klientský i serverový software Oracle 9i.|  
|**CELÉ ČÍSLO BEZ ZNAMÉNKA**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, UInt32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Určuje hodnotu **System. data. DbType** a <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **Hodnoty vstup**, **Output**a **ReturnValue** **ParameterDirection** používané <xref:System.Data.OracleClient.OracleParameter.Value%2A> vlastností objektujsou.NETFrameworkdatovýchtypů,pokudvstupníhodnotanenídatovýtypOracle(pro<xref:System.Data.OracleClient.OracleParameter> <xref:System.Data.OracleClient.OracleNumber> například nebo<xref:System.Data.OracleClient.OracleString>). To se nevztahuje na datové typy **REF CURSOR**, **BFILE**a **LOB** .  
  
## <a name="see-also"></a>Viz také:

- [Oracle a ADO.NET](oracle-and-adonet.md)
- [Přehled ADO.NET](ado-net-overview.md)
