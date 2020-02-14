---
title: dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
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
ms.openlocfilehash: 2fdace8a9c7bcc090fd801be3bd717e4a2b34a87
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217539"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)
`dateTimeInvalidLocalFormat` MDA je aktivována, když je instance <xref:System.DateTime> uložená jako světový koordinovaný čas (UTC) formátována pomocí formátu, který je určen pro použití pouze pro místní instance <xref:System.DateTime>. Tento MDA není aktivovaný pro nespecifikované nebo výchozí instance <xref:System.DateTime>.  
  
## <a name="symptom"></a>Příznak  
 Aplikace provádí ruční serializaci <xref:System.DateTime> instance UTC pomocí místního formátu:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Příčina  
 Formát "z" pro metodu <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> zahrnuje posun místního časového pásma, například "+ 10:00" pro dobu Sydney. V takovém případě bude výsledkem smysluplný výsledek pouze v případě, že je hodnota <xref:System.DateTime> místní. Pokud je hodnota čas UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> zahrnuje posun místního časového pásma, ale nezobrazuje ani neupravuje specifikátor časového pásma.  
  
### <a name="resolution"></a>Řešení  
 Instance <xref:System.DateTime> UTC by měly být formátovány způsobem, který označuje, že jsou UTC. Doporučený formát pro dobu UTC k použití "Z" k označení času UTC:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 K dispozici je také formát "o", který serializace <xref:System.DateTime> využívá vlastnost <xref:System.DateTime.Kind%2A>, která je správně serializována bez ohledu na to, zda je instance místní, UTC nebo neurčená:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá vliv na modul runtime.  
  
## <a name="output"></a>Výstup  
 V důsledku této aktivace MDA není žádný zvláštní výstup. k určení umístění volání <xref:System.DateTime.ToString%2A>, které aktivovalo MDA, však lze použít zásobník volání.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Zvažte aplikaci, která je nepřímo serializována <xref:System.DateTime> hodnotu UTC pomocí třídy <xref:System.Xml.XmlConvert> nebo <xref:System.Data.DataSet> následujícím způsobem.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 Serializace <xref:System.Xml.XmlConvert> a <xref:System.Data.DataSet> používají ve výchozím nastavení místní formáty pro serializaci. Další možnosti jsou vyžadovány k serializaci jiných druhů <xref:System.DateTime> hodnot, jako je například UTC.  
  
 Pro tento konkrétní příklad předejte `XmlDateTimeSerializationMode.RoundtripKind` volání `ToString` na `XmlConvert`. Tím se data deserializovat jako čas UTC.  
  
 Pokud používáte <xref:System.Data.DataSet>, nastavte vlastnost <xref:System.Data.DataColumn.DateTimeMode%2A> objektu <xref:System.Data.DataColumn> na <xref:System.Data.DataSetDateTime.Utc>.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Globalization.DateTimeFormatInfo>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
