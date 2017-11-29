---
title: "dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dates [.NET Framework], formatting
- invalid date time local format
- invalid local formats
- MDAs (managed debugging assistants), invalid local formats
- managed debugging assistants (MDAs), invalid local formats
- dateTimeInvalidLocalFormat MDA
- date formatting
- time formatting
- UTC formatting
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3181acec440f2d01e928bb051b297fba75de1e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)
`dateTimeInvalidLocalFormat` MDA se aktivuje při <xref:System.DateTime> instanci, která je uloženo jako světového koordinovaného času (UTC) je formátován pomocí formátu, který je určen pro použití pouze pro místní <xref:System.DateTime> instance. Tato MDA není aktivován pro tento parametr nezadáte, nebo výchozí <xref:System.DateTime> instance.  
  
## <a name="symptom"></a>Příznaky  
 Aplikace je ručně serializaci UTC <xref:System.DateTime> pomocí místního formátu:  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>příčina  
 'z' formátu pro <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metoda zahrnuje posun místního času zóny, například "+ 10:00" Sydney dobu. Jako takový ho pouze vytvoří smysluplný výsledku Pokud hodnota <xref:System.DateTime> je místní. Pokud je hodnota času UTC <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> zahrnuje místního času posun zóny, ale nemá zobrazit nebo upravit specifikátor časové pásmo.  
  
### <a name="resolution"></a>Rozlišení  
 UTC <xref:System.DateTime> instancí musí být formátována způsobem, který označuje, že jsou UTC. Doporučený formát UTC – časové hodnoty a Z používat k označení čas UTC:  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Je také formátu "o", který serializuje <xref:System.DateTime> , které využívají <xref:System.DateTime.Kind%2A> vlastnost, která serializuje správně bez ohledu na to, zda je místní, instance UTC, nebo nezadanou:  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA neovlivňuje modulu runtime.  
  
## <a name="output"></a>Výstup  
 Neexistuje žádný speciální výstup v důsledku této aktivace MDA., ale zásobník volání slouží k určení umístění <xref:System.DateTime.ToString%2A> volání, které aktivuje (mda).  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Zvažte aplikaci, která je nepřímo serializaci UTC <xref:System.DateTime> hodnotu pomocí <xref:System.Xml.XmlConvert> nebo <xref:System.Data.DataSet> třída tímto způsobem.  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert> a <xref:System.Data.DataSet> serializations ve výchozím nastavení používá místní formáty pro serializaci. Další možnosti jsou vyžadována k serializaci jiné typy z <xref:System.DateTime> hodnoty, například UTC.  
  
 V tomto konkrétním příkladu předat `XmlDateTimeSerializationMode.RoundtripKind` k `ToString` volání na `XmlConvert`. To serializuje data jako čas UTC.  
  
 Pokud se používá <xref:System.Data.DataSet>, nastavte <xref:System.Data.DataColumn.DateTimeMode%2A> vlastnost na <xref:System.Data.DataColumn> do objektu <xref:System.Data.DataSetDateTime.Utc>.  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
