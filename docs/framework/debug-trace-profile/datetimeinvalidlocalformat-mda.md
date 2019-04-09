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
ms.openlocfilehash: 380334dbe9b91ea369de6cbe58686a9a74254c2c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148223"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="f98bd-102">dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="f98bd-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="f98bd-103">`dateTimeInvalidLocalFormat` MDA aktivováno, když <xref:System.DateTime> instanci, která je uloženo jako koordinovaný světový čas (UTC), je naformátována pomocí formátu, který je určen pro použití pouze pro místní <xref:System.DateTime> instancí.</span><span class="sxs-lookup"><span data-stu-id="f98bd-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="f98bd-104">Toto MDA aktivováno pro tento parametr zadán, nebo výchozí <xref:System.DateTime> instancí.</span><span class="sxs-lookup"><span data-stu-id="f98bd-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="f98bd-105">Příznak</span><span class="sxs-lookup"><span data-stu-id="f98bd-105">Symptom</span></span>  
 <span data-ttu-id="f98bd-106">Aplikace je ruční serializaci UTC <xref:System.DateTime> instance pomocí místního formátu:</span><span class="sxs-lookup"><span data-stu-id="f98bd-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="f98bd-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="f98bd-107">Cause</span></span>  
 <span data-ttu-id="f98bd-108">"z" formát pro <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metoda obsahuje posunu místního časového pásma, například "+ 10:00" Sydney dobu.</span><span class="sxs-lookup"><span data-stu-id="f98bd-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="f98bd-109">V důsledku toho se jen vytvoří smysluplný výsledek Pokud hodnota <xref:System.DateTime> je místní.</span><span class="sxs-lookup"><span data-stu-id="f98bd-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="f98bd-110">Pokud je hodnota času UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> místní čas zahrnuje posun zóny, ale ne zobrazit nebo upravit specifikátor časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="f98bd-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="f98bd-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="f98bd-111">Resolution</span></span>  
 <span data-ttu-id="f98bd-112">Čas UTC <xref:System.DateTime> instance by měly být formátovány způsobem, který označuje, že jsou UTC.</span><span class="sxs-lookup"><span data-stu-id="f98bd-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="f98bd-113">Doporučený formát UTC časy na použití "Z" k označení čas UTC:</span><span class="sxs-lookup"><span data-stu-id="f98bd-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="f98bd-114">Je také ve formátu "o", který serializuje <xref:System.DateTime> využívání <xref:System.DateTime.Kind%2A> vlastnost, která serializuje správně bez ohledu na to, jestli je instance místní, UTC, nebo neurčenou:</span><span class="sxs-lookup"><span data-stu-id="f98bd-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f98bd-115">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="f98bd-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="f98bd-116">Toto MDA nemá vliv na modul runtime.</span><span class="sxs-lookup"><span data-stu-id="f98bd-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f98bd-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="f98bd-117">Output</span></span>  
 <span data-ttu-id="f98bd-118">Neexistuje žádný zvláštní výstup v důsledku tohoto MDA aktivace., ale zásobník volání slouží k určení umístění <xref:System.DateTime.ToString%2A> volání, které MDA aktivováno.</span><span class="sxs-lookup"><span data-stu-id="f98bd-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f98bd-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f98bd-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="f98bd-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="f98bd-120">Example</span></span>  
 <span data-ttu-id="f98bd-121">Vezměte v úvahu aplikace, která je nepřímo serializace UTC <xref:System.DateTime> hodnotu s použitím <xref:System.Xml.XmlConvert> nebo <xref:System.Data.DataSet> třídy následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="f98bd-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="f98bd-122"><xref:System.Xml.XmlConvert> a <xref:System.Data.DataSet> serializations ve výchozím nastavení použít místní formáty serializace.</span><span class="sxs-lookup"><span data-stu-id="f98bd-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="f98bd-123">Další možnosti jsou vyžadována k serializaci jiných typů z <xref:System.DateTime> hodnoty, jako je například UTC.</span><span class="sxs-lookup"><span data-stu-id="f98bd-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="f98bd-124">V tomto konkrétním příkladu předat `XmlDateTimeSerializationMode.RoundtripKind` k `ToString` volat `XmlConvert`.</span><span class="sxs-lookup"><span data-stu-id="f98bd-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="f98bd-125">Toto serializuje data jako čas UTC.</span><span class="sxs-lookup"><span data-stu-id="f98bd-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="f98bd-126">Pokud používáte <xref:System.Data.DataSet>, nastavte <xref:System.Data.DataColumn.DateTimeMode%2A> vlastnost <xref:System.Data.DataColumn> objektu <xref:System.Data.DataSetDateTime.Utc>.</span><span class="sxs-lookup"><span data-stu-id="f98bd-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="f98bd-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f98bd-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="f98bd-128">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="f98bd-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
