---
title: Mapování datových typů Oracle
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: c1fb3a6838e6a1b242255d4035c10ab0ec07d536
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104569"
---
# <a name="oracle-data-type-mappings"></a>Mapování datových typů Oracle
V následující tabulce jsou uvedeny Oracle datových typů a jejich mapování na <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Oracle datového typu|Rozhraní .NET framework na datový typ vracený OracleDataReader.GetValue|OracleClient datový typ vracený OracleDataReader.GetOracleValue|Poznámky|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**DATOVÝ TYP CLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE (Datum)**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**PLOVOUCÍ DESETINNOU ČÁRKOU**|**Desetinné číslo**|<xref:System.Data.OracleClient.OracleNumber>|Tento typ dat je alias pro **číslo** datový typ a je navržený tak, aby <xref:System.Data.OracleClient.OracleDataReader> vrátí **System.Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo hodnotu s plovoucí desetinnou čárkou. Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**CELÉ ČÍSLO**|**Desetinné číslo**|<xref:System.Data.OracleClient.OracleNumber>|Tento typ dat je alias pro **NUMBER(38)** datový typ a je navržený tak, aby <xref:System.Data.OracleClient.OracleDataReader> vrátí **System.Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo celočíselnou hodnotu. Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**INTERVAL ROK MĚSÍC**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**DEN INTERVALU SEKUNDY.**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**DLOUHO NEZPRACOVANÉ**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**ČÍSLO**|**Desetinné číslo**|<xref:System.Data.OracleClient.OracleNumber>|Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR** nepodporuje datový typ <xref:System.Data.OracleClient.OracleDataReader> objektu.|  
|**ID ŘÁDKU**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**ČASOVÉ RAZÍTKO**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ČASOVÉ RAZÍTKO S MÍSTNÍM ČASOVÉM PÁSMU**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ČASOVÉ RAZÍTKO S ČASOVÝM PÁSMEM**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**CELÉ ČÍSLO BEZ ZNAMÉNKA**|**Číslo**|<xref:System.Data.OracleClient.OracleNumber>|Tento typ dat je alias pro **NUMBER(38)** datový typ a je navržený tak, aby <xref:System.Data.OracleClient.OracleDataReader> vrátí **System.Decimal** nebo <xref:System.Data.OracleClient.OracleNumber> místo hodnoty celé číslo bez znaménka. Použití datový typ rozhraní .NET Framework může způsobit přetečení.|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 Následující tabulka uvádí typy dat Oracle a datové typy rozhraní .NET Framework (**System.Data.DbType** a <xref:System.Data.OracleClient.OracleType>) Chcete-li použít při vytváření vazby je jako parametry.  
  
|Oracle datového typu|Výčtu DbType k vytvoření vazby jako parametr|Výčet OracleType k vytvoření vazby jako parametr|Poznámky|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle umožňuje pouze vazby **BFILE** jako **BFILE** parametru. .NET Data Provider pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**BFILE** hodnoty, jako například **byte []** nebo <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Objekt blob**|Oracle umožňuje pouze vazby **BLOB** jako **objektů BLOB** parametr. .NET Data Provider pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**BLOB** hodnoty, jako například **byte []** nebo <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**DATOVÝ TYP CLOB**||**Clob**|Oracle umožňuje pouze vazby **datový typ CLOB** jako **datový typ CLOB** parametru. .NET Data Provider pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**datový typ CLOB** hodnoty, jako například **System.String** nebo <xref:System.Data.OracleClient.OracleString>.|  
|**DATE (Datum)**|**DateTime**|**DateTime**||  
|**PLOVOUCÍ DESETINNOU ČÁRKOU**|**Jednoduché, Double, Decimal**|**Float, dvakrát, číslo**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Určuje, **System.Data.DBType** a <xref:System.Data.OracleClient.OracleType>.|  
|**CELÉ ČÍSLO**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, číslo**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Určuje, **System.Data.DBType** a <xref:System.Data.OracleClient.OracleType>.|  
|**INTERVAL ROK MĚSÍC**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> je k dispozici pouze při použití softwaru i Oracle 9i klientem a serverem.|  
|**DEN INTERVALU SEKUNDY.**|**Objekt**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> je k dispozici pouze při použití softwaru i Oracle 9i klientem a serverem.|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**DLOUHO NEZPRACOVANÉ**|**binární**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**nChar**||  
|**NCLOB**||**NClob**|Oracle umožňuje pouze vazby **NCLOB** jako **NCLOB** parametru. .NET Data Provider pro Oracle není vytvořit automaticky za vás při pokusu vytvořit vazbu jinou hodnotu než**NCLOB** hodnoty, jako například **System.String** nebo <xref:System.Data.OracleClient.OracleString>.|  
|**ČÍSLO**|**VarNumeric**|**Číslo**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**RAW**|**binární**|**nezpracované**||  
|**REF CURSOR**||**Kurzor**|Další informace najdete v tématu [soubory Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**ID ŘÁDKU**|**AnsiString**|**ID řádku**||  
|**ČASOVÉ RAZÍTKO**|**DateTime**|**Timestamp**|<xref:System.Data.OracleClient.OracleType> je k dispozici pouze při použití softwaru i Oracle 9i klientem a serverem.|  
|**ČASOVÉ RAZÍTKO S MÍSTNÍM ČASOVÉM PÁSMU**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> je k dispozici pouze při použití softwaru i Oracle 9i klientem a serverem.|  
|**ČASOVÉ RAZÍTKO S ČASOVÝM PÁSMEM**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> je k dispozici pouze při použití softwaru i Oracle 9i klientem a serverem.|  
|**CELÉ ČÍSLO BEZ ZNAMÉNKA**|**Byte, UInt16, UInt32, UInt64, desetinné číslo**|**Byte, UInt16, Uint32, číslo**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Určuje, **System.Data.DBType** a <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **Vstup/výstup**, **výstup**, a **ReturnValue** **ParameterDirection** hodnot použitých <xref:System.Data.OracleClient.OracleParameter.Value%2A> vlastnost <xref:System.Data.OracleClient.OracleParameter> objektu jsou datové typy rozhraní .NET Framework, pokud je vstupní hodnota je typu Oracle data (například <xref:System.Data.OracleClient.OracleNumber> nebo <xref:System.Data.OracleClient.OracleString>). Tato akce není požadována k **REF CURSOR**, **BFILE**, nebo **LOB** datové typy.  
  
## <a name="see-also"></a>Viz také:

- [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
