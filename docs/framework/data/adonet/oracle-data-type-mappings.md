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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: adb0fc332e00e766a62d0af1c110c5a7ce2d42c3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-data-type-mappings"></a>Mapování datového typu Oracle
Následující tabulka uvádí typy dat Oracle a jejich mapování <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Oracle datový typ|Datový typ rozhraní .NET framework vrácený OracleDataReader.GetValue|OracleClient datový typ vrácený OracleDataReader.GetOracleValue|Poznámky|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR –**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**Řetězec**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATUM**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**PLOVOUCÍ DESETINNÁ ČÁRKA**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Tento datový typ je alias **číslo** datového typu a je navržený tak, tak, aby <xref:System.Data.OracleClient.OracleDataReader> vrátí **System.Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo hodnotu s plovoucí desetinnou čárkou. Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**CELÉ ČÍSLO**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Tento datový typ je alias **NUMBER(38)** datového typu a je navržený tak, tak, aby <xref:System.Data.OracleClient.OracleDataReader> vrátí **System.Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo celočíselnou hodnotu. Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**INTERVAL ROK, MĚSÍC**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**DENNÍ INTERVAL SEKUNDY.**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**DLOUHÁ**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**DLOUHO NEZPRACOVANÁ**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Řetězec**|<xref:System.Data.OracleClient.OracleLob>||  
|**ČÍSLO**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**NVARCHAR2**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**NEZPRACOVANÁ**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF KURZORU**|||Oracle **REF kurzor** datový typ není podporován <xref:System.Data.OracleClient.OracleDataReader> objektu.|  
|**ID ŘÁDKU**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**ČASOVÉ RAZÍTKO**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ČASOVÉ RAZÍTKO S MÍSTNÍM ČASOVÉM PÁSMU**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ČASOVÉ RAZÍTKO S ČASOVÝM PÁSMEM**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**CELÉ ČÍSLO BEZ ZNAMÉNKA**|**Číslo**|<xref:System.Data.OracleClient.OracleNumber>|Tento datový typ je alias **NUMBER(38)** datového typu a je navržený tak, tak, aby <xref:System.Data.OracleClient.OracleDataReader> vrátí **System.Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo hodnoty celé číslo bez znaménka. Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**VARCHAR2**|**Řetězec**|<xref:System.Data.OracleClient.OracleString>||  
  
 Následující tabulka uvádí typy dat Oracle a datové typy rozhraní .NET Framework (**System.Data.DbType** a <xref:System.Data.OracleClient.OracleType>) chcete použít při vazbě je jako parametry.  
  
|Oracle datový typ|Hodnota DbType výčtu pro vazbu jako parametr|Výčet OracleType pro vazbu jako parametr|Poznámky|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle umožňuje pouze vazby **BFILE** jako **BFILE** parametr. Zprostředkovatel dat .NET pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**BFILE** hodnotu, jako například **byte []** nebo <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Objekt BLOB**|Oracle umožňuje pouze vazby **BLOB** jako **BLOB** parametr. Zprostředkovatel dat .NET pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**BLOB** hodnotu, jako například **byte []** nebo <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR –**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Datový typ CLOB**|Oracle umožňuje pouze vazby **datový typ CLOB** jako **datový typ CLOB** parametr. Zprostředkovatel dat .NET pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**datový typ CLOB** hodnotu, jako například **System.String** nebo <xref:System.Data.OracleClient.OracleString>.|  
|**DATUM**|**DateTime**|**DateTime**||  
|**PLOVOUCÍ DESETINNÁ ČÁRKA**|**Jednoduché, Double, Decimal**|**Float, dvakrát, počet**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Určuje, **System.Data.DBType** a <xref:System.Data.OracleClient.OracleType>.|  
|**CELÉ ČÍSLO**|**SByte, Int16, Int32, Int64, Decimal**|**SByte –, Int16, Int32, počet**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Určuje, **System.Data.DBType** a <xref:System.Data.OracleClient.OracleType>.|  
|**INTERVAL ROK, MĚSÍC**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType>je k dispozici pouze v případě použití softwaru i Oracle 9i klienta a serveru.|  
|**DENNÍ INTERVAL SEKUNDY.**|**Object**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType>je k dispozici pouze v případě použití softwaru i Oracle 9i klienta a serveru.|  
|**DLOUHÁ**|**AnsiString**|**LongVarChar**||  
|**DLOUHO NEZPRACOVANÁ**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle umožňuje pouze vazby **NCLOB** jako **NCLOB** parametr. Zprostředkovatel dat .NET pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**NCLOB** hodnotu, jako například **System.String** nebo <xref:System.Data.OracleClient.OracleString>.|  
|**ČÍSLO**|**VarNumeric**|**Číslo**||  
|**NVARCHAR2**|**Řetězec**|**NVarChar**||  
|**NEZPRACOVANÁ**|**Binary**|**Raw**||  
|**REF KURZORU**||**Kurzor**|Další informace najdete v tématu [Oracle REF kurzory](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**ID ŘÁDKU**|**AnsiString**|**ID řádku**||  
|**ČASOVÉ RAZÍTKO**|**DateTime**|**Časové razítko**|<xref:System.Data.OracleClient.OracleType>je k dispozici pouze v případě použití softwaru i Oracle 9i klienta a serveru.|  
|**ČASOVÉ RAZÍTKO S MÍSTNÍM ČASOVÉM PÁSMU**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType>je k dispozici pouze v případě použití softwaru i Oracle 9i klienta a serveru.|  
|**ČASOVÉ RAZÍTKO S ČASOVÝM PÁSMEM**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType>je k dispozici pouze v případě použití softwaru i Oracle 9i klienta a serveru.|  
|**CELÉ ČÍSLO BEZ ZNAMÉNKA**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Uint32 bajtů, UInt16, počet**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Určuje, **System.Data.DBType** a <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **Vstup/výstup**, **výstup**, a **ReturnValue** **ParameterDirection** hodnoty používané <xref:System.Data.OracleClient.OracleParameter.Value%2A> vlastnost <xref:System.Data.OracleClient.OracleParameter> objekt jsou datové typy rozhraní .NET Framework, pokud vstupní hodnota je datového typu Oracle (například <xref:System.Data.OracleClient.OracleNumber> nebo <xref:System.Data.OracleClient.OracleString>). To neplatí pro **REF kurzor**, **BFILE**, nebo **obchodní** datové typy.  
  
## <a name="see-also"></a>Viz také  
 [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
