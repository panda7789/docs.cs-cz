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
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="59731-102">dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="59731-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="59731-103">`dateTimeInvalidLocalFormat` MDA je aktivována, když je instance <xref:System.DateTime> uložená jako světový koordinovaný čas (UTC) formátována pomocí formátu, který je určen pro použití pouze pro místní instance <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="59731-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="59731-104">Tento MDA není aktivovaný pro nespecifikované nebo výchozí instance <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="59731-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="59731-105">Příznak</span><span class="sxs-lookup"><span data-stu-id="59731-105">Symptom</span></span>  
 <span data-ttu-id="59731-106">Aplikace provádí ruční serializaci <xref:System.DateTime> instance UTC pomocí místního formátu:</span><span class="sxs-lookup"><span data-stu-id="59731-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="59731-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="59731-107">Cause</span></span>  
 <span data-ttu-id="59731-108">Formát "z" pro metodu <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> zahrnuje posun místního časového pásma, například "+ 10:00" pro dobu Sydney.</span><span class="sxs-lookup"><span data-stu-id="59731-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="59731-109">V takovém případě bude výsledkem smysluplný výsledek pouze v případě, že je hodnota <xref:System.DateTime> místní.</span><span class="sxs-lookup"><span data-stu-id="59731-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="59731-110">Pokud je hodnota čas UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> zahrnuje posun místního časového pásma, ale nezobrazuje ani neupravuje specifikátor časového pásma.</span><span class="sxs-lookup"><span data-stu-id="59731-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="59731-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="59731-111">Resolution</span></span>  
 <span data-ttu-id="59731-112">Instance <xref:System.DateTime> UTC by měly být formátovány způsobem, který označuje, že jsou UTC.</span><span class="sxs-lookup"><span data-stu-id="59731-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="59731-113">Doporučený formát pro dobu UTC k použití "Z" k označení času UTC:</span><span class="sxs-lookup"><span data-stu-id="59731-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="59731-114">K dispozici je také formát "o", který serializace <xref:System.DateTime> využívá vlastnost <xref:System.DateTime.Kind%2A>, která je správně serializována bez ohledu na to, zda je instance místní, UTC nebo neurčená:</span><span class="sxs-lookup"><span data-stu-id="59731-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="59731-115">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="59731-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="59731-116">Tento MDA nemá vliv na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="59731-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="59731-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="59731-117">Output</span></span>  
 <span data-ttu-id="59731-118">V důsledku této aktivace MDA není žádný zvláštní výstup. k určení umístění volání <xref:System.DateTime.ToString%2A>, které aktivovalo MDA, však lze použít zásobník volání.</span><span class="sxs-lookup"><span data-stu-id="59731-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="59731-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="59731-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="59731-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="59731-120">Example</span></span>  
 <span data-ttu-id="59731-121">Zvažte aplikaci, která je nepřímo serializována <xref:System.DateTime> hodnotu UTC pomocí třídy <xref:System.Xml.XmlConvert> nebo <xref:System.Data.DataSet> následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="59731-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="59731-122">Serializace <xref:System.Xml.XmlConvert> a <xref:System.Data.DataSet> používají ve výchozím nastavení místní formáty pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="59731-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="59731-123">Další možnosti jsou vyžadovány k serializaci jiných druhů <xref:System.DateTime> hodnot, jako je například UTC.</span><span class="sxs-lookup"><span data-stu-id="59731-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="59731-124">Pro tento konkrétní příklad předejte `XmlDateTimeSerializationMode.RoundtripKind` volání `ToString` na `XmlConvert`.</span><span class="sxs-lookup"><span data-stu-id="59731-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="59731-125">Tím se data deserializovat jako čas UTC.</span><span class="sxs-lookup"><span data-stu-id="59731-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="59731-126">Pokud používáte <xref:System.Data.DataSet>, nastavte vlastnost <xref:System.Data.DataColumn.DateTimeMode%2A> objektu <xref:System.Data.DataColumn> na <xref:System.Data.DataSetDateTime.Utc>.</span><span class="sxs-lookup"><span data-stu-id="59731-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="59731-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="59731-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="59731-128">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="59731-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
