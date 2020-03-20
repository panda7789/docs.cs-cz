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
ms.openlocfilehash: b01f030c474e426cb87fb907f99f241eeb76a7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174755"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)
MDA `dateTimeInvalidLocalFormat` je aktivován, <xref:System.DateTime> když instance, která je uložena jako univerzální koordinovaný čas (UTC) je formátován pomocí formátu, který je určen k použití pouze pro místní <xref:System.DateTime> instance. Tento MDA není aktivován pro <xref:System.DateTime> nespecifikované nebo výchozí instance.  
  
## <a name="symptom"></a>Příznak  
 Aplikace ručně serializuje instanci <xref:System.DateTime> UTC pomocí místního formátu:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Příčina  
 Formát 'z' pro <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metodu zahrnuje posun místního časového pásma, například "+10:00" pro čas Sydney. Jako takový bude vytvářet pouze smysluplný výsledek, pokud <xref:System.DateTime> je hodnota místní. Pokud je hodnota čas UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> zahrnuje posun místního časového pásma, ale nezobrazuje ani neupravuje specifikátor časového pásma.  
  
### <a name="resolution"></a>Řešení  
 Instance UTC <xref:System.DateTime> by měly být formátovány způsobem, který označuje, že se jedná o utc. Doporučený formát pro časy UTC pro použití "Z" k označení času UTC:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 K dispozici je také formát "o", <xref:System.DateTime> který serializuje využití <xref:System.DateTime.Kind%2A> vlastnosti, která serializuje správně bez ohledu na to, zda je instance místní, UTC nebo nespecifikované:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Vliv na běhový čas  
 Tento MDA nemá vliv na dobu runtime.  
  
## <a name="output"></a>Výstup  
 Neexistuje žádný speciální výstup v důsledku aktivace mda., Však zásobník volání lze použít <xref:System.DateTime.ToString%2A> k určení umístění volání, který aktivoval MDA.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Zvažte aplikaci, která nepřímo serializuje <xref:System.DateTime> hodnotu <xref:System.Xml.XmlConvert> UTC pomocí třídy nebo <xref:System.Data.DataSet> následujícím způsobem.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert> Serializace <xref:System.Data.DataSet> a serializace ve výchozím nastavení používají místní formáty pro serializaci. Další možnosti jsou nutné serializovat <xref:System.DateTime> jiné druhy hodnot, jako je například UTC.  
  
 V tomto konkrétním příkladu `ToString` přejděte `XmlConvert` `XmlDateTimeSerializationMode.RoundtripKind` do volání na . To serializuje data jako čas UTC.  
  
 Pokud <xref:System.Data.DataSet>používáte , <xref:System.Data.DataColumn.DateTimeMode%2A> nastavte <xref:System.Data.DataColumn> vlastnost <xref:System.Data.DataSetDateTime.Utc>objektu na .  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Globalization.DateTimeFormatInfo>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
