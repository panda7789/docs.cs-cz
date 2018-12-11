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
ms.openlocfilehash: 54ce0f75ddfbf9f3b62917aa67f4d97140bbdc42
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153334"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)
`dateTimeInvalidLocalFormat` MDA aktivováno, když <xref:System.DateTime> instanci, která je uloženo jako koordinovaný světový čas (UTC), je naformátována pomocí formátu, který je určen pro použití pouze pro místní <xref:System.DateTime> instancí. Toto MDA aktivováno pro tento parametr zadán, nebo výchozí <xref:System.DateTime> instancí.  
  
## <a name="symptom"></a>Příznak  
 Aplikace je ruční serializaci UTC <xref:System.DateTime> instance pomocí místního formátu:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>příčina  
 "z" formát pro <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metoda obsahuje posunu místního časového pásma, například "+ 10:00" Sydney dobu. V důsledku toho se jen vytvoří smysluplný výsledek Pokud hodnota <xref:System.DateTime> je místní. Pokud je hodnota času UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> místní čas zahrnuje posun zóny, ale ne zobrazit nebo upravit specifikátor časové pásmo.  
  
### <a name="resolution"></a>Rozlišení  
 Čas UTC <xref:System.DateTime> instance by měly být formátovány způsobem, který označuje, že jsou UTC. Doporučený formát UTC časy na použití "Z" k označení čas UTC:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Je také ve formátu "o", který serializuje <xref:System.DateTime> využívání <xref:System.DateTime.Kind%2A> vlastnost, která serializuje správně bez ohledu na to, jestli je instance místní, UTC, nebo neurčenou:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá vliv na modul runtime.  
  
## <a name="output"></a>Výstup  
 Neexistuje žádný zvláštní výstup v důsledku tohoto MDA aktivace., ale zásobník volání slouží k určení umístění <xref:System.DateTime.ToString%2A> volání, které MDA aktivováno.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Vezměte v úvahu aplikace, která je nepřímo serializace UTC <xref:System.DateTime> hodnotu s použitím <xref:System.Xml.XmlConvert> nebo <xref:System.Data.DataSet> třídy následujícím způsobem.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert> a <xref:System.Data.DataSet> serializations ve výchozím nastavení použít místní formáty serializace. Další možnosti jsou vyžadována k serializaci jiných typů z <xref:System.DateTime> hodnoty, jako je například UTC.  
  
 V tomto konkrétním příkladu předat `XmlDateTimeSerializationMode.RoundtripKind` k `ToString` volat `XmlConvert`. Toto serializuje data jako čas UTC.  
  
 Pokud používáte <xref:System.Data.DataSet>, nastavte <xref:System.Data.DataColumn.DateTimeMode%2A> vlastnost <xref:System.Data.DataColumn> objektu <xref:System.Data.DataSetDateTime.Utc>.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
