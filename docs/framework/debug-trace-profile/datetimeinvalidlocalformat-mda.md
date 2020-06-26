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
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="ad279-103">dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="ad279-103">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="ad279-104">`dateTimeInvalidLocalFormat`Při <xref:System.DateTime> formátování instance, která je uložena jako univerzální koordinovaný čas (UTC), je aktivována aplikace MDA pomocí formátu, který je určen pro použití pouze pro místní <xref:System.DateTime> instance.</span><span class="sxs-lookup"><span data-stu-id="ad279-104">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="ad279-105">Pro nespecifikované nebo výchozí instance není tento MDA aktivován <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="ad279-105">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="ad279-106">Příznak</span><span class="sxs-lookup"><span data-stu-id="ad279-106">Symptom</span></span>  
 <span data-ttu-id="ad279-107">Aplikace provádí ruční serializaci <xref:System.DateTime> instance UTC pomocí místního formátu:</span><span class="sxs-lookup"><span data-stu-id="ad279-107">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="ad279-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="ad279-108">Cause</span></span>  
 <span data-ttu-id="ad279-109">Formát "z" pro <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metodu zahrnuje posun místního časového pásma, například "+ 10:00" pro dobu Sydney.</span><span class="sxs-lookup"><span data-stu-id="ad279-109">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="ad279-110">V takovém případě bude výsledkem smysluplný výsledek pouze v případě, že hodnota <xref:System.DateTime> je místní.</span><span class="sxs-lookup"><span data-stu-id="ad279-110">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="ad279-111">Pokud je hodnota čas UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> zahrnuje posun místního časového pásma, ale nezobrazuje ani neupravuje specifikátor časového pásma.</span><span class="sxs-lookup"><span data-stu-id="ad279-111">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="ad279-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="ad279-112">Resolution</span></span>  
 <span data-ttu-id="ad279-113"><xref:System.DateTime>Instance UTC by měly být formátovány způsobem, který označuje, že jsou UTC.</span><span class="sxs-lookup"><span data-stu-id="ad279-113">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="ad279-114">Doporučený formát pro dobu UTC k použití "Z" k označení času UTC:</span><span class="sxs-lookup"><span data-stu-id="ad279-114">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="ad279-115">K dispozici je také formát "o", který serializace <xref:System.DateTime> využije <xref:System.DateTime.Kind%2A> vlastnost, která bude správně serializován bez ohledu na to, zda je instance místní, UTC nebo neurčená:</span><span class="sxs-lookup"><span data-stu-id="ad279-115">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ad279-116">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="ad279-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="ad279-117">Tento MDA nemá vliv na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="ad279-117">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ad279-118">Výstup</span><span class="sxs-lookup"><span data-stu-id="ad279-118">Output</span></span>  
 <span data-ttu-id="ad279-119">V důsledku této aktivace MDA není k dispozici žádný zvláštní výstup. zásobník volání však lze použít k určení umístění <xref:System.DateTime.ToString%2A> volání, které aktivovalo MDA.</span><span class="sxs-lookup"><span data-stu-id="ad279-119">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ad279-120">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ad279-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="ad279-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad279-121">Example</span></span>  
 <span data-ttu-id="ad279-122">Zvažte aplikaci, která je nepřímo serializována hodnotu UTC <xref:System.DateTime> pomocí <xref:System.Xml.XmlConvert> <xref:System.Data.DataSet> třídy nebo, následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="ad279-122">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="ad279-123"><xref:System.Xml.XmlConvert> <xref:System.Data.DataSet> Serializace a používají ve výchozím nastavení místní formáty pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="ad279-123">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="ad279-124">Další možnosti jsou vyžadovány k serializaci jiných druhů <xref:System.DateTime> hodnot, jako je například UTC.</span><span class="sxs-lookup"><span data-stu-id="ad279-124">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="ad279-125">Pro tento konkrétní příklad předejte `XmlDateTimeSerializationMode.RoundtripKind` `ToString` volání na `XmlConvert` .</span><span class="sxs-lookup"><span data-stu-id="ad279-125">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="ad279-126">Tím se data deserializovat jako čas UTC.</span><span class="sxs-lookup"><span data-stu-id="ad279-126">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="ad279-127">Pokud používáte <xref:System.Data.DataSet> , nastavte <xref:System.Data.DataColumn.DateTimeMode%2A> vlastnost <xref:System.Data.DataColumn> objektu na <xref:System.Data.DataSetDateTime.Utc> .</span><span class="sxs-lookup"><span data-stu-id="ad279-127">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad279-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad279-128">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="ad279-129">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="ad279-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
