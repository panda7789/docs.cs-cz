---
title: Mappings1 typ dat Oracle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 746013a11d10162a78116ff41d0b09d942f7651b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-data-type-mappings"></a>Mapování datového typu Oracle
Následující tabulka uvádí typy dat Oracle a jejich mapování <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Oracle datový typ|Datový typ rozhraní .NET framework vrácený OracleDataReader.GetValue|OracleClient datový typ vrácený OracleDataReader.GetOracleValue|Poznámky|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**OBJEKT BLOB**|**Byte]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR –**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**DATOVÝ TYP CLOB**|**Řetězec**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATUM**|**Data a času**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**PLOVOUCÍ DESETINNÁ ČÁRKA**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Tento datový typ je alias **číslo** datového typu a je navržený tak, tak, aby <xref:System.Data.OracleClient.OracleDataReader> vrátí **System.Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo hodnotu s plovoucí desetinnou čárkou. Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**CELÉ ČÍSLO**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Tento datový typ je alias **NUMBER(38)** datového typu a je navržený tak, tak, aby <xref:System.Data.OracleClient.OracleDataReader> vrátí **System.Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo celočíselnou hodnotu. Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**INTERVAL ROK, MĚSÍC**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**DENNÍ INTERVAL SEKUNDY.**|**Časový interval**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**DLOUHÁ**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**DLOUHO NEZPRACOVANÁ**|**Byte]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Řetězec**|<xref:System.Data.OracleClient.OracleLob>||  
|**ČÍSLO**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**NVARCHAR2**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**NEZPRACOVANÁ**|**Byte]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF KURZORU**|||Oracle **REF kurzor** datový typ není podporován <xref:System.Data.OracleClient.OracleDataReader> objektu.|  
|**ID ŘÁDKU**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**ČASOVÉ RAZÍTKO**|**Data a času**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ČASOVÉ RAZÍTKO S MÍSTNÍM ČASOVÉM PÁSMU**|**Data a času**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ČASOVÉ RAZÍTKO S ČASOVÝM PÁSMEM**|**Data a času**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**CELÉ ČÍSLO BEZ ZNAMÉNKA**|**Číslo**|<xref:System.Data.OracleClient.OracleNumber>|Tento datový typ je alias **NUMBER(38)** datového typu a je navržený tak, tak, aby <xref:System.Data.OracleClient.OracleDataReader> vrátí **System.Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo hodnoty celé číslo bez znaménka. Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**VARCHAR2**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
  
 Následující tabulka uvádí typy dat Oracle a datové typy rozhraní .NET Framework (**System.Data.DbType** a <xref:System.Data.OracleClient.OracleType>) chcete použít při vazbě je jako parametry.  
  
|Oracle datový typ|Hodnota DbType výčtu pro vazbu jako parametr|Výčet OracleType pro vazbu jako parametr|Poznámky|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle umožňuje pouze vazby **BFILE** jako **BFILE** parametr. Zprostředkovatel dat .NET pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**BFILE** hodnotu, jako například **byte []** nebo <xref:System.Data.OracleClient.OracleBinary>.|  
|**OBJEKT BLOB**||**Objekt BLOB**|Oracle umožňuje pouze vazby **BLOB** jako **BLOB** parametr. Zprostředkovatel dat .NET pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**BLOB** hodnotu, jako například **byte []** nebo <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR –**|**AnsiStringFixedLength**|**Char –**||  
|**DATOVÝ TYP CLOB**||**Datový typ CLOB**|Oracle umožňuje pouze vazby **datový typ CLOB** jako **datový typ CLOB** parametr. Zprostředkovatel dat .NET pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**datový typ CLOB** hodnotu, jako například **System.String** nebo <xref:System.Data.OracleClient.OracleString>.|  
|**DATUM**|**Data a času**|**Data a času**||  
|**PLOVOUCÍ DESETINNÁ ČÁRKA**|**Jednoduché, Double, Decimal**|**Float, dvakrát, počet**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Určuje, **System.Data.DBType** a <xref:System.Data.OracleClient.OracleType>.|  
|**CELÉ ČÍSLO**|**SByte –, Int16, Int32, Int64, Decimal**|**SByte –, Int16, Int32, počet**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Určuje, **System.Data.DBType** a <xref:System.Data.OracleClient.OracleType>.|  
|**INTERVAL ROK, MĚSÍC**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType>je k dispozici pouze v případě použití softwaru i Oracle 9i klienta a serveru.|  
|**DENNÍ INTERVAL SEKUNDY.**|**Objekt**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType>je k dispozici pouze v případě použití softwaru i Oracle 9i klienta a serveru.|  
|**DLOUHÁ**|**AnsiString**|**LongVarChar**||  
|**DLOUHO NEZPRACOVANÁ**|**Binární**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle umožňuje pouze vazby **NCLOB** jako **NCLOB** parametr. Zprostředkovatel dat .NET pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**NCLOB** hodnotu, jako například **System.String** nebo <xref:System.Data.OracleClient.OracleString>.|  
|**ČÍSLO**|**VarNumeric**|**Číslo**||  
|**NVARCHAR2**|**Řetězec**|**NVarChar**||  
|**NEZPRACOVANÁ**|**Binární**|**Nezpracovaná**||  
|**REF KURZORU**||**Kurzor**|Další informace najdete v tématu [Oracle REF kurzory](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**ID ŘÁDKU**|**AnsiString**|**ID řádku**||  
|**ČASOVÉ RAZÍTKO**|**Data a času**|**Časové razítko**|<xref:System.Data.OracleClient.OracleType>je k dispozici pouze v případě použití softwaru i Oracle 9i klienta a serveru.|  
|**ČASOVÉ RAZÍTKO S MÍSTNÍM ČASOVÉM PÁSMU**|**Data a času**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType>je k dispozici pouze v případě použití softwaru i Oracle 9i klienta a serveru.|  
|**ČASOVÉ RAZÍTKO S ČASOVÝM PÁSMEM**|**Data a času**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType>je k dispozici pouze v případě použití softwaru i Oracle 9i klienta a serveru.|  
|**CELÉ ČÍSLO BEZ ZNAMÉNKA**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Uint32 bajtů, UInt16, počet**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Určuje, **System.Data.DBType** a <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **Vstup/výstup**, **výstup**, a **ReturnValue** **ParameterDirection** hodnoty používané <xref:System.Data.OracleClient.OracleParameter.Value%2A> vlastnost <xref:System.Data.OracleClient.OracleParameter> objekt jsou datové typy rozhraní .NET Framework, pokud vstupní hodnota je datového typu Oracle (například <xref:System.Data.OracleClient.OracleNumber> nebo <xref:System.Data.OracleClient.OracleString>). To neplatí pro **REF kurzor**, **BFILE**, nebo **obchodní** datové typy.  
  
## <a name="see-also"></a>Viz také  
 [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
