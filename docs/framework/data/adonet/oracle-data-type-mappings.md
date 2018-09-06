---
title: Oracle datového typu Mappings1
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: 9057a19abb1abc22924b5542f06e21a57a36ed94
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856332"
---
# <a name="oracle-data-type-mappings"></a>Mapování datových typů Oracle
V následující tabulce jsou uvedeny Oracle datových typů a jejich mapování na <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Oracle datového typu|Rozhraní .NET framework na datový typ vracený OracleDataReader.GetValue|OracleClient datový typ vracený OracleDataReader.GetOracleValue|Poznámky|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**OBJEKT BLOB**|**Byte]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**DATOVÝ TYP CLOB**|**řetězec**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATUM**|**Datum a čas**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**PLOVOUCÍ DESETINNOU ČÁRKOU**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Tento typ dat je alias pro **číslo** datový typ a je navržený tak, aby <xref:System.Data.OracleClient.OracleDataReader> vrátí **System.Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo hodnotu s plovoucí desetinnou čárkou. Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**CELÉ ČÍSLO**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Tento typ dat je alias pro **NUMBER(38)** datový typ a je navržený tak, aby <xref:System.Data.OracleClient.OracleDataReader> vrátí **System.Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo celočíselnou hodnotu. Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**INTERVAL ROK MĚSÍC**|**Datový typ Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**DEN INTERVALU SEKUNDY.**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**DLOUHO NEZPRACOVANÉ**|**Byte]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**řetězec**|<xref:System.Data.OracleClient.OracleLob>||  
|**ČÍSLO**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**NVARCHAR2**|**řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**NEZPRACOVANÉ**|**Byte]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR** nepodporuje datový typ <xref:System.Data.OracleClient.OracleDataReader> objektu.|  
|**ID ŘÁDKU**|**řetězec**|<xref:System.Data.OracleClient.OracleString>||  
|**ČASOVÉ RAZÍTKO**|**Datum a čas**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ČASOVÉ RAZÍTKO S MÍSTNÍM ČASOVÉM PÁSMU**|**Datum a čas**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ČASOVÉ RAZÍTKO S ČASOVÝM PÁSMEM**|**Datum a čas**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**CELÉ ČÍSLO BEZ ZNAMÉNKA**|**Číslo**|<xref:System.Data.OracleClient.OracleNumber>|Tento typ dat je alias pro **NUMBER(38)** datový typ a je navržený tak, aby <xref:System.Data.OracleClient.OracleDataReader> vrátí **System.Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo hodnoty celé číslo bez znaménka. Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**VARCHAR2**|**řetězec**|<xref:System.Data.OracleClient.OracleString>||  
  
 Následující tabulka uvádí typy dat Oracle a datové typy rozhraní .NET Framework (**System.Data.DbType** a <xref:System.Data.OracleClient.OracleType>) Chcete-li použít při vytváření vazby je jako parametry.  
  
|Oracle datového typu|Výčtu DbType k vytvoření vazby jako parametr|Výčet OracleType k vytvoření vazby jako parametr|Poznámky|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle umožňuje pouze vazby **BFILE** jako **BFILE** parametru. .NET Data Provider pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**BFILE** hodnoty, jako například **byte []** nebo <xref:System.Data.OracleClient.OracleBinary>.|  
|**OBJEKT BLOB**||**Objekt BLOB**|Oracle umožňuje pouze vazby **BLOB** jako **objektů BLOB** parametr. .NET Data Provider pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**BLOB** hodnoty, jako například **byte []** nebo <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**DATOVÝ TYP CLOB**||**Datový typ CLOB**|Oracle umožňuje pouze vazby **datový typ CLOB** jako **datový typ CLOB** parametru. .NET Data Provider pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**datový typ CLOB** hodnoty, jako například **System.String** nebo <xref:System.Data.OracleClient.OracleString>.|  
|**DATUM**|**Datum a čas**|**Datum a čas**||  
|**PLOVOUCÍ DESETINNOU ČÁRKOU**|**Jednoduché, Double, Decimal**|**Float, dvakrát, číslo**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Určuje, **System.Data.DBType** a <xref:System.Data.OracleClient.OracleType>.|  
|**CELÉ ČÍSLO**|**SByte, Int16, Int32, Int64, desetinné číslo**|**SByte, Int16, Int32, číslo**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Určuje, **System.Data.DBType** a <xref:System.Data.OracleClient.OracleType>.|  
|**INTERVAL ROK MĚSÍC**|**Datový typ Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> je k dispozici pouze při použití softwaru i Oracle 9i klientem a serverem.|  
|**DEN INTERVALU SEKUNDY.**|**objekt**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> je k dispozici pouze při použití softwaru i Oracle 9i klientem a serverem.|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**DLOUHO NEZPRACOVANÉ**|**Binární**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle umožňuje pouze vazby **NCLOB** jako **NCLOB** parametru. .NET Data Provider pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**NCLOB** hodnoty, jako například **System.String** nebo <xref:System.Data.OracleClient.OracleString>.|  
|**ČÍSLO**|**VarNumeric**|**Číslo**||  
|**NVARCHAR2**|**řetězec**|**NVarChar**||  
|**NEZPRACOVANÉ**|**Binární**|**nezpracované**||  
|**REF CURSOR**||**Kurzor**|Další informace najdete v tématu [soubory Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**ID ŘÁDKU**|**AnsiString**|**ID řádku**||  
|**ČASOVÉ RAZÍTKO**|**Datum a čas**|**Časové razítko**|<xref:System.Data.OracleClient.OracleType> je k dispozici pouze při použití softwaru i Oracle 9i klientem a serverem.|  
|**ČASOVÉ RAZÍTKO S MÍSTNÍM ČASOVÉM PÁSMU**|**Datum a čas**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> je k dispozici pouze při použití softwaru i Oracle 9i klientem a serverem.|  
|**ČASOVÉ RAZÍTKO S ČASOVÝM PÁSMEM**|**Datum a čas**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> je k dispozici pouze při použití softwaru i Oracle 9i klientem a serverem.|  
|**CELÉ ČÍSLO BEZ ZNAMÉNKA**|**Byte, UInt16, UInt32, UInt64, desetinné číslo**|**Byte, UInt16, Uint32, číslo**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Určuje, **System.Data.DBType** a <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **Vstup/výstup**, **výstup**, a **ReturnValue** **ParameterDirection** hodnot použitých <xref:System.Data.OracleClient.OracleParameter.Value%2A> vlastnost <xref:System.Data.OracleClient.OracleParameter> objektu jsou datové typy rozhraní .NET Framework, pokud je vstupní hodnota je typu Oracle data (například <xref:System.Data.OracleClient.OracleNumber> nebo <xref:System.Data.OracleClient.OracleString>). Tato akce není požadována k **REF CURSOR**, **BFILE**, nebo **LOB** datové typy.  
  
## <a name="see-also"></a>Viz také  
 [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
