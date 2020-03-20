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
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="9d6bf-102">dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="9d6bf-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="9d6bf-103">MDA `dateTimeInvalidLocalFormat` je aktivován, <xref:System.DateTime> když instance, která je uložena jako univerzální koordinovaný čas (UTC) je formátován pomocí formátu, který je určen k použití pouze pro místní <xref:System.DateTime> instance.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="9d6bf-104">Tento MDA není aktivován pro <xref:System.DateTime> nespecifikované nebo výchozí instance.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="9d6bf-105">Příznak</span><span class="sxs-lookup"><span data-stu-id="9d6bf-105">Symptom</span></span>  
 <span data-ttu-id="9d6bf-106">Aplikace ručně serializuje instanci <xref:System.DateTime> UTC pomocí místního formátu:</span><span class="sxs-lookup"><span data-stu-id="9d6bf-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="9d6bf-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="9d6bf-107">Cause</span></span>  
 <span data-ttu-id="9d6bf-108">Formát 'z' pro <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metodu zahrnuje posun místního časového pásma, například "+10:00" pro čas Sydney.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="9d6bf-109">Jako takový bude vytvářet pouze smysluplný výsledek, pokud <xref:System.DateTime> je hodnota místní.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="9d6bf-110">Pokud je hodnota čas UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> zahrnuje posun místního časového pásma, ale nezobrazuje ani neupravuje specifikátor časového pásma.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="9d6bf-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="9d6bf-111">Resolution</span></span>  
 <span data-ttu-id="9d6bf-112">Instance UTC <xref:System.DateTime> by měly být formátovány způsobem, který označuje, že se jedná o utc.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="9d6bf-113">Doporučený formát pro časy UTC pro použití "Z" k označení času UTC:</span><span class="sxs-lookup"><span data-stu-id="9d6bf-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="9d6bf-114">K dispozici je také formát "o", <xref:System.DateTime> který serializuje využití <xref:System.DateTime.Kind%2A> vlastnosti, která serializuje správně bez ohledu na to, zda je instance místní, UTC nebo nespecifikované:</span><span class="sxs-lookup"><span data-stu-id="9d6bf-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9d6bf-115">Vliv na běhový čas</span><span class="sxs-lookup"><span data-stu-id="9d6bf-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="9d6bf-116">Tento MDA nemá vliv na dobu runtime.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9d6bf-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="9d6bf-117">Output</span></span>  
 <span data-ttu-id="9d6bf-118">Neexistuje žádný speciální výstup v důsledku aktivace mda., Však zásobník volání lze použít <xref:System.DateTime.ToString%2A> k určení umístění volání, který aktivoval MDA.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9d6bf-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9d6bf-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9d6bf-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d6bf-120">Example</span></span>  
 <span data-ttu-id="9d6bf-121">Zvažte aplikaci, která nepřímo serializuje <xref:System.DateTime> hodnotu <xref:System.Xml.XmlConvert> UTC pomocí třídy nebo <xref:System.Data.DataSet> následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="9d6bf-122"><xref:System.Xml.XmlConvert> Serializace <xref:System.Data.DataSet> a serializace ve výchozím nastavení používají místní formáty pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="9d6bf-123">Další možnosti jsou nutné serializovat <xref:System.DateTime> jiné druhy hodnot, jako je například UTC.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="9d6bf-124">V tomto konkrétním příkladu `ToString` přejděte `XmlConvert` `XmlDateTimeSerializationMode.RoundtripKind` do volání na .</span><span class="sxs-lookup"><span data-stu-id="9d6bf-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="9d6bf-125">To serializuje data jako čas UTC.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="9d6bf-126">Pokud <xref:System.Data.DataSet>používáte , <xref:System.Data.DataColumn.DateTimeMode%2A> nastavte <xref:System.Data.DataColumn> vlastnost <xref:System.Data.DataSetDateTime.Utc>objektu na .</span><span class="sxs-lookup"><span data-stu-id="9d6bf-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d6bf-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d6bf-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="9d6bf-128">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="9d6bf-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
