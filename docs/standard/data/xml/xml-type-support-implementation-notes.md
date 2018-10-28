---
title: Poznámky k implementaci podpory typů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 73f786c8f1080d0046889958e8b3bd3165870569
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187449"
---
# <a name="xml-type-support-implementation-notes"></a><span data-ttu-id="91bc5-102">Poznámky k implementaci podpory typů XML</span><span class="sxs-lookup"><span data-stu-id="91bc5-102">XML Type Support Implementation Notes</span></span>
<span data-ttu-id="91bc5-103">Toto téma popisuje některé podrobnosti implementace, které chcete mít na paměti.</span><span class="sxs-lookup"><span data-stu-id="91bc5-103">This topic describes some implementation details that you want to be aware of.</span></span>  
  
## <a name="list-mappings"></a><span data-ttu-id="91bc5-104">Seznam mapování</span><span class="sxs-lookup"><span data-stu-id="91bc5-104">List Mappings</span></span>  
 <span data-ttu-id="91bc5-105"><xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type []**, a <xref:System.String> typy se používají k vyjádření schématu XML definice jazyk (XSD) seznam typů.</span><span class="sxs-lookup"><span data-stu-id="91bc5-105">The <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]**, and <xref:System.String> types are used to represent XML Schema definition language (XSD) list types.</span></span>  
  
## <a name="union-mappings"></a><span data-ttu-id="91bc5-106">Mapování typu UNION</span><span class="sxs-lookup"><span data-stu-id="91bc5-106">Union Mappings</span></span>  
 <span data-ttu-id="91bc5-107">Typy sjednocení jsou reprezentovány pomocí <xref:System.Xml.Schema.XmlAtomicValue> nebo <xref:System.String> typu.</span><span class="sxs-lookup"><span data-stu-id="91bc5-107">Union types are represented using the <xref:System.Xml.Schema.XmlAtomicValue> or <xref:System.String> type.</span></span> <span data-ttu-id="91bc5-108">Zdrojový typ nebo typ cíle musí proto vždy být buď <xref:System.String> nebo <xref:System.Xml.Schema.XmlAtomicValue>.</span><span class="sxs-lookup"><span data-stu-id="91bc5-108">The source type or the destination type must therefore always be either <xref:System.String> or <xref:System.Xml.Schema.XmlAtomicValue>.</span></span>  
  
 <span data-ttu-id="91bc5-109">Pokud <xref:System.Xml.Schema.XmlSchemaDatatype> objekt představuje typ seznamu objektu převede vstupní řetězec hodnotu na seznam jednoho nebo více objektů.</span><span class="sxs-lookup"><span data-stu-id="91bc5-109">If the <xref:System.Xml.Schema.XmlSchemaDatatype> object represents a list type the object converts the input string value to a list of one or more objects.</span></span> <span data-ttu-id="91bc5-110">Pokud <xref:System.Xml.Schema.XmlSchemaDatatype> představuje typ sjednocení, pak pokusu parsovat vstupní hodnotu jako typ člena sjednocení.</span><span class="sxs-lookup"><span data-stu-id="91bc5-110">If the <xref:System.Xml.Schema.XmlSchemaDatatype> represents a union type then an attempt is made to parse the input value as a member type of the union.</span></span> <span data-ttu-id="91bc5-111">Pokud se nezdaří pokus o parsování pak převodu dojde k pokusu o s dalšího člena sjednocení a tak dále až převod je úspěšný, nebo nejsou žádné další členské typy chcete vyzkoušet, v takovém případě je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="91bc5-111">If the parse attempt fails then the conversion is attempted with the next member of the union and so on until the conversion is successful, or there are no other member types to try, in which case an exception is thrown.</span></span>  
  
## <a name="differences-between-clr-and-xml-data-types"></a><span data-ttu-id="91bc5-112">Rozdíly mezi typy dat XML a CLR</span><span class="sxs-lookup"><span data-stu-id="91bc5-112">Differences Between CLR and XML Data Types</span></span>  
 <span data-ttu-id="91bc5-113">Následující část popisuje určité problémy, které se mohou vyskytnout mezi typy CLR a typy dat XML a jak se zpracovává.</span><span class="sxs-lookup"><span data-stu-id="91bc5-113">The following describes certain mismatches that can occur between CLR types and XML data types and how they are handled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91bc5-114">`xs` Předpona je namapována na <https://www.w3.org/2001/XMLSchema> a identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="91bc5-114">The `xs` prefix is mapped to the <https://www.w3.org/2001/XMLSchema> and namespace URI.</span></span>
  
### <a name="systemtimespan-and-xsduration"></a><span data-ttu-id="91bc5-115">Hodnota System.TimeSpan a značku xs: Duration</span><span class="sxs-lookup"><span data-stu-id="91bc5-115">System.TimeSpan and xs:duration</span></span>  
 <span data-ttu-id="91bc5-116">`xs:duration` Typ je částečně seřazených v, které existují ale ekvivalentní určité hodnoty typu duration, které se liší.</span><span class="sxs-lookup"><span data-stu-id="91bc5-116">The `xs:duration` type is partially ordered in that there are certain duration values that are different but equivalent.</span></span> <span data-ttu-id="91bc5-117">To znamená, že pro `xs:duration` hodnota typu, jako je například 1 měsíc (P1M) je menší než 32 dní (P32D) větší než 27 dnů (P27D) a je ekvivalentní se 28, 29 nebo 30 dní.</span><span class="sxs-lookup"><span data-stu-id="91bc5-117">This means that for the `xs:duration` type value such as 1 month (P1M) is less than 32 days (P32D), larger than 27 days (P27D) and equivalent to 28, 29 or 30 days.</span></span>  
  
 <span data-ttu-id="91bc5-118"><xref:System.TimeSpan> Třída nepodporuje částečné řazení.</span><span class="sxs-lookup"><span data-stu-id="91bc5-118">The <xref:System.TimeSpan> class does not support this partial ordering.</span></span> <span data-ttu-id="91bc5-119">Místo toho použije určitý počet dní pro 1 rok a 1 měsíc; 365 dnů a 30 dnů v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="91bc5-119">Instead, it picks a specific number of days for 1 year and 1 month; 365 days and 30 days respectively.</span></span>  
  
 <span data-ttu-id="91bc5-120">Další informace o `xs:duration` zadejte naleznete v tématu W3C [XML schématu část 2: datové typy doporučení](https://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="91bc5-120">For more information on the `xs:duration` type, see the W3C [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a><span data-ttu-id="91bc5-121">: Time gregoriánské datum typy a System.DateTime</span><span class="sxs-lookup"><span data-stu-id="91bc5-121">xs:time, Gregorian Date Types, and System.DateTime</span></span>  
 <span data-ttu-id="91bc5-122">Při `xs:time` hodnota je namapována na <xref:System.DateTime> objektu, <xref:System.DateTime.MinValue> pole slouží k inicializaci vlastnosti datum <xref:System.DateTime> objektu (, jako <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, a <xref:System.DateTime.Day%2A>) na nejmenší <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="91bc5-122">When an `xs:time` value is mapped to a <xref:System.DateTime> object, the <xref:System.DateTime.MinValue> field is used to initialize the date properties of the <xref:System.DateTime> object (such as <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>) to the smallest possible <xref:System.DateTime> value.</span></span>  
  
 <span data-ttu-id="91bc5-123">Obdobně instance `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` a `xs:gMonthDay` mapovaly na <xref:System.DateTime> objektu.</span><span class="sxs-lookup"><span data-stu-id="91bc5-123">Similarly, instances of `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` and `xs:gMonthDay` are also mapped to a <xref:System.DateTime> object.</span></span> <span data-ttu-id="91bc5-124">Nepoužívané vlastnosti na <xref:System.DateTime> objektu jsou inicializovány na ty z <xref:System.DateTime.MinValue>.</span><span class="sxs-lookup"><span data-stu-id="91bc5-124">Unused properties on the <xref:System.DateTime> object are initialized to those from <xref:System.DateTime.MinValue>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91bc5-125">Nelze spoléhat na <xref:System.DateTime.Year%2A?displayProperty=nameWithType> hodnotu, pokud je obsah typu `xs:gMonthDay`.</span><span class="sxs-lookup"><span data-stu-id="91bc5-125">You cannot rely on the <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value when the content is typed as `xs:gMonthDay`.</span></span> <span data-ttu-id="91bc5-126"><xref:System.DateTime.Year%2A?displayProperty=nameWithType> Hodnota je vždycky nastavený na 1904 v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="91bc5-126">The <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value is always set to 1904 in this case.</span></span>  
  
### <a name="xsanyuri-and-systemuri"></a><span data-ttu-id="91bc5-127">xs:anyURI a System.Uri</span><span class="sxs-lookup"><span data-stu-id="91bc5-127">xs:anyURI and System.Uri</span></span>  
 <span data-ttu-id="91bc5-128">Pokud instance `xs:anyURI` představuje relativní identifikátor URI je namapována na <xref:System.Uri>, <xref:System.Uri> objekt nemá žádné základní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="91bc5-128">When an instance of `xs:anyURI` that represents a relative URI is mapped to a <xref:System.Uri>, the <xref:System.Uri> object does not have a base URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91bc5-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91bc5-129">See also</span></span>

- [<span data-ttu-id="91bc5-130">Podpora typu v třídách System.Xml</span><span class="sxs-lookup"><span data-stu-id="91bc5-130">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
