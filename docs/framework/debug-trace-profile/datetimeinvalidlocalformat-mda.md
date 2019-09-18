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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32217b9e681179c246560ff5b51b65b4f4e044d5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052888"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)
Při formátování <xref:System.DateTime> instance, která je uložena jako univerzální koordinovaný čas (UTC), je aktivována aplikace MDApomocíformátu,kterýjeurčenpropoužitípouzepromístníinstance.`dateTimeInvalidLocalFormat` <xref:System.DateTime> Pro nespecifikované nebo výchozí <xref:System.DateTime> instance není tento MDA aktivován.  
  
## <a name="symptom"></a>Příznak  
 Aplikace provádí ruční serializaci instance UTC <xref:System.DateTime> pomocí místního formátu:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>příčina  
 Formát "z" pro <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metodu zahrnuje posun místního časového pásma, například "+ 10:00" pro dobu Sydney. V takovém případě bude výsledkem smysluplný výsledek pouze v <xref:System.DateTime> případě, že hodnota je místní. Pokud je hodnota čas UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> zahrnuje posun místního časového pásma, ale nezobrazuje ani neupravuje specifikátor časového pásma.  
  
### <a name="resolution"></a>Řešení  
 Instance <xref:System.DateTime> UTC by měly být formátovány způsobem, který označuje, že jsou UTC. Doporučený formát pro dobu UTC k použití "Z" k označení času UTC:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 K dispozici je také formát "o", který serializace <xref:System.DateTime> využije <xref:System.DateTime.Kind%2A> vlastnost, která bude správně serializován bez ohledu na to, zda je instance místní, UTC nebo neurčená:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá vliv na modul runtime.  
  
## <a name="output"></a>Výstup  
 V důsledku této aktivace MDA není k dispozici žádný zvláštní výstup. zásobník volání však lze použít k určení umístění <xref:System.DateTime.ToString%2A> volání, které aktivovalo MDA.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Zvažte aplikaci, která je nepřímo serializována hodnotu UTC <xref:System.DateTime> <xref:System.Xml.XmlConvert> pomocí třídy nebo <xref:System.Data.DataSet> , následujícím způsobem.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 Serializace <xref:System.Data.DataSet> a používají ve výchozím nastavení místní formáty pro serializaci. <xref:System.Xml.XmlConvert> Další možnosti jsou vyžadovány k serializaci jiných <xref:System.DateTime> druhů hodnot, jako je například UTC.  
  
 Pro tento konkrétní příklad předejte `XmlDateTimeSerializationMode.RoundtripKind` `ToString` volání na `XmlConvert`. Tím se data deserializovat jako čas UTC.  
  
 Pokud používáte <xref:System.Data.DataSet>, <xref:System.Data.DataColumn.DateTimeMode%2A> nastavte vlastnost <xref:System.Data.DataColumn> objektu na <xref:System.Data.DataSetDateTime.Utc>.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.DateTimeFormatInfo>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
