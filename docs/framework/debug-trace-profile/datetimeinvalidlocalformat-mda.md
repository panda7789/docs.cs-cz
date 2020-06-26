---
title: dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění dateTimeInvalidLocalFormat (MDA), který se aktivuje, když hodnota DateTime uložená v UTC Získá formát data a času, který je jenom místní.
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
ms.openlocfilehash: d092b93af55d2cdf14e9284d8cffcdc8440cbf81
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415989"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)
`dateTimeInvalidLocalFormat`Při <xref:System.DateTime> formátování instance, která je uložena jako univerzální koordinovaný čas (UTC), je aktivována aplikace MDA pomocí formátu, který je určen pro použití pouze pro místní <xref:System.DateTime> instance. Pro nespecifikované nebo výchozí instance není tento MDA aktivován <xref:System.DateTime> .  
  
## <a name="symptom"></a>Příznak  
 Aplikace provádí ruční serializaci <xref:System.DateTime> instance UTC pomocí místního formátu:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Příčina  
 Formát "z" pro <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metodu zahrnuje posun místního časového pásma, například "+ 10:00" pro dobu Sydney. V takovém případě bude výsledkem smysluplný výsledek pouze v případě, že hodnota <xref:System.DateTime> je místní. Pokud je hodnota čas UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> zahrnuje posun místního časového pásma, ale nezobrazuje ani neupravuje specifikátor časového pásma.  
  
### <a name="resolution"></a>Řešení  
 <xref:System.DateTime>Instance UTC by měly být formátovány způsobem, který označuje, že jsou UTC. Doporučený formát pro dobu UTC k použití "Z" k označení času UTC:  
  
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
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Zvažte aplikaci, která je nepřímo serializována hodnotu UTC <xref:System.DateTime> pomocí <xref:System.Xml.XmlConvert> <xref:System.Data.DataSet> třídy nebo, následujícím způsobem.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert> <xref:System.Data.DataSet> Serializace a používají ve výchozím nastavení místní formáty pro serializaci. Další možnosti jsou vyžadovány k serializaci jiných druhů <xref:System.DateTime> hodnot, jako je například UTC.  
  
 Pro tento konkrétní příklad předejte `XmlDateTimeSerializationMode.RoundtripKind` `ToString` volání na `XmlConvert` . Tím se data deserializovat jako čas UTC.  
  
 Pokud používáte <xref:System.Data.DataSet> , nastavte <xref:System.Data.DataColumn.DateTimeMode%2A> vlastnost <xref:System.Data.DataColumn> objektu na <xref:System.Data.DataSetDateTime.Utc> .  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Globalization.DateTimeFormatInfo>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
