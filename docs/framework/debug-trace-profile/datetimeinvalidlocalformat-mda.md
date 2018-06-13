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
ms.openlocfilehash: bb5777e275fd7c48f7125b9e0315b08d3095c373
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357803"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="0e59c-102">dateTimeInvalidLocalFormat – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="0e59c-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="0e59c-103">`dateTimeInvalidLocalFormat` MDA se aktivuje při <xref:System.DateTime> instanci, která je uloženo jako světového koordinovaného času (UTC) je formátován pomocí formátu, který je určen pro použití pouze pro místní <xref:System.DateTime> instance.</span><span class="sxs-lookup"><span data-stu-id="0e59c-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="0e59c-104">Tato MDA není aktivován pro tento parametr nezadáte, nebo výchozí <xref:System.DateTime> instance.</span><span class="sxs-lookup"><span data-stu-id="0e59c-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="0e59c-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="0e59c-105">Symptom</span></span>  
 <span data-ttu-id="0e59c-106">Aplikace je ručně serializaci UTC <xref:System.DateTime> pomocí místního formátu:</span><span class="sxs-lookup"><span data-stu-id="0e59c-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="0e59c-107">příčina</span><span class="sxs-lookup"><span data-stu-id="0e59c-107">Cause</span></span>  
 <span data-ttu-id="0e59c-108">'z' formátu pro <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metoda zahrnuje posun místního času zóny, například "+ 10:00" Sydney dobu.</span><span class="sxs-lookup"><span data-stu-id="0e59c-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="0e59c-109">Jako takový ho pouze vytvoří smysluplný výsledku Pokud hodnota <xref:System.DateTime> je místní.</span><span class="sxs-lookup"><span data-stu-id="0e59c-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="0e59c-110">Pokud je hodnota času UTC <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> zahrnuje místního času posun zóny, ale nemá zobrazit nebo upravit specifikátor časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="0e59c-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="0e59c-111">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="0e59c-111">Resolution</span></span>  
 <span data-ttu-id="0e59c-112">UTC <xref:System.DateTime> instancí musí být formátována způsobem, který označuje, že jsou UTC.</span><span class="sxs-lookup"><span data-stu-id="0e59c-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="0e59c-113">Doporučený formát UTC – časové hodnoty a Z používat k označení čas UTC:</span><span class="sxs-lookup"><span data-stu-id="0e59c-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="0e59c-114">Je také formátu "o", který serializuje <xref:System.DateTime> , které využívají <xref:System.DateTime.Kind%2A> vlastnost, která serializuje správně bez ohledu na to, zda je místní, instance UTC, nebo nezadanou:</span><span class="sxs-lookup"><span data-stu-id="0e59c-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0e59c-115">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="0e59c-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="0e59c-116">Tato MDA neovlivňuje modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0e59c-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0e59c-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="0e59c-117">Output</span></span>  
 <span data-ttu-id="0e59c-118">Neexistuje žádný speciální výstup v důsledku této aktivace MDA., ale zásobník volání slouží k určení umístění <xref:System.DateTime.ToString%2A> volání, které aktivuje (mda).</span><span class="sxs-lookup"><span data-stu-id="0e59c-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0e59c-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="0e59c-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="0e59c-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e59c-120">Example</span></span>  
 <span data-ttu-id="0e59c-121">Zvažte aplikaci, která je nepřímo serializaci UTC <xref:System.DateTime> hodnotu pomocí <xref:System.Xml.XmlConvert> nebo <xref:System.Data.DataSet> třída tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="0e59c-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="0e59c-122"><xref:System.Xml.XmlConvert> a <xref:System.Data.DataSet> serializations ve výchozím nastavení používá místní formáty pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="0e59c-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="0e59c-123">Další možnosti jsou vyžadována k serializaci jiné typy z <xref:System.DateTime> hodnoty, například UTC.</span><span class="sxs-lookup"><span data-stu-id="0e59c-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="0e59c-124">V tomto konkrétním příkladu předat `XmlDateTimeSerializationMode.RoundtripKind` k `ToString` volání na `XmlConvert`.</span><span class="sxs-lookup"><span data-stu-id="0e59c-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="0e59c-125">To serializuje data jako čas UTC.</span><span class="sxs-lookup"><span data-stu-id="0e59c-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="0e59c-126">Pokud se používá <xref:System.Data.DataSet>, nastavte <xref:System.Data.DataColumn.DateTimeMode%2A> vlastnost na <xref:System.Data.DataColumn> do objektu <xref:System.Data.DataSetDateTime.Utc>.</span><span class="sxs-lookup"><span data-stu-id="0e59c-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e59c-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e59c-127">See Also</span></span>  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [<span data-ttu-id="0e59c-128">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="0e59c-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
