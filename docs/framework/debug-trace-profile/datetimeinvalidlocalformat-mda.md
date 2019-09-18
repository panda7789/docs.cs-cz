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
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="49d65-102">dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="49d65-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="49d65-103">Při formátování <xref:System.DateTime> instance, která je uložena jako univerzální koordinovaný čas (UTC), je aktivována aplikace MDApomocíformátu,kterýjeurčenpropoužitípouzepromístníinstance.`dateTimeInvalidLocalFormat` <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="49d65-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="49d65-104">Pro nespecifikované nebo výchozí <xref:System.DateTime> instance není tento MDA aktivován.</span><span class="sxs-lookup"><span data-stu-id="49d65-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="49d65-105">Příznak</span><span class="sxs-lookup"><span data-stu-id="49d65-105">Symptom</span></span>  
 <span data-ttu-id="49d65-106">Aplikace provádí ruční serializaci instance UTC <xref:System.DateTime> pomocí místního formátu:</span><span class="sxs-lookup"><span data-stu-id="49d65-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="49d65-107">příčina</span><span class="sxs-lookup"><span data-stu-id="49d65-107">Cause</span></span>  
 <span data-ttu-id="49d65-108">Formát "z" pro <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metodu zahrnuje posun místního časového pásma, například "+ 10:00" pro dobu Sydney.</span><span class="sxs-lookup"><span data-stu-id="49d65-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="49d65-109">V takovém případě bude výsledkem smysluplný výsledek pouze v <xref:System.DateTime> případě, že hodnota je místní.</span><span class="sxs-lookup"><span data-stu-id="49d65-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="49d65-110">Pokud je hodnota čas UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> zahrnuje posun místního časového pásma, ale nezobrazuje ani neupravuje specifikátor časového pásma.</span><span class="sxs-lookup"><span data-stu-id="49d65-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="49d65-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="49d65-111">Resolution</span></span>  
 <span data-ttu-id="49d65-112">Instance <xref:System.DateTime> UTC by měly být formátovány způsobem, který označuje, že jsou UTC.</span><span class="sxs-lookup"><span data-stu-id="49d65-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="49d65-113">Doporučený formát pro dobu UTC k použití "Z" k označení času UTC:</span><span class="sxs-lookup"><span data-stu-id="49d65-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="49d65-114">K dispozici je také formát "o", který serializace <xref:System.DateTime> využije <xref:System.DateTime.Kind%2A> vlastnost, která bude správně serializován bez ohledu na to, zda je instance místní, UTC nebo neurčená:</span><span class="sxs-lookup"><span data-stu-id="49d65-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="49d65-115">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="49d65-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="49d65-116">Tento MDA nemá vliv na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="49d65-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="49d65-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="49d65-117">Output</span></span>  
 <span data-ttu-id="49d65-118">V důsledku této aktivace MDA není k dispozici žádný zvláštní výstup. zásobník volání však lze použít k určení umístění <xref:System.DateTime.ToString%2A> volání, které aktivovalo MDA.</span><span class="sxs-lookup"><span data-stu-id="49d65-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="49d65-119">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="49d65-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="49d65-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="49d65-120">Example</span></span>  
 <span data-ttu-id="49d65-121">Zvažte aplikaci, která je nepřímo serializována hodnotu UTC <xref:System.DateTime> <xref:System.Xml.XmlConvert> pomocí třídy nebo <xref:System.Data.DataSet> , následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="49d65-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="49d65-122">Serializace <xref:System.Data.DataSet> a používají ve výchozím nastavení místní formáty pro serializaci. <xref:System.Xml.XmlConvert></span><span class="sxs-lookup"><span data-stu-id="49d65-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="49d65-123">Další možnosti jsou vyžadovány k serializaci jiných <xref:System.DateTime> druhů hodnot, jako je například UTC.</span><span class="sxs-lookup"><span data-stu-id="49d65-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="49d65-124">Pro tento konkrétní příklad předejte `XmlDateTimeSerializationMode.RoundtripKind` `ToString` volání na `XmlConvert`.</span><span class="sxs-lookup"><span data-stu-id="49d65-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="49d65-125">Tím se data deserializovat jako čas UTC.</span><span class="sxs-lookup"><span data-stu-id="49d65-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="49d65-126">Pokud používáte <xref:System.Data.DataSet>, <xref:System.Data.DataColumn.DateTimeMode%2A> nastavte vlastnost <xref:System.Data.DataColumn> objektu na <xref:System.Data.DataSetDateTime.Utc>.</span><span class="sxs-lookup"><span data-stu-id="49d65-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="49d65-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49d65-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="49d65-128">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="49d65-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
