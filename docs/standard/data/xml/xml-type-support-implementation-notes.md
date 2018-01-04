---
title: "Poznámky k implementaci XML typu podpory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8c2706782ed1242ecdb5af1fdfab7a3f24e19236
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xml-type-support-implementation-notes"></a><span data-ttu-id="6f802-102">Poznámky k implementaci XML typu podpory</span><span class="sxs-lookup"><span data-stu-id="6f802-102">XML Type Support Implementation Notes</span></span>
<span data-ttu-id="6f802-103">Toto téma popisuje některé podrobnosti implementace, které chcete mít na paměti.</span><span class="sxs-lookup"><span data-stu-id="6f802-103">This topic describes some implementation details that you want to be aware of.</span></span>  
  
## <a name="list-mappings"></a><span data-ttu-id="6f802-104">Seznam mapování</span><span class="sxs-lookup"><span data-stu-id="6f802-104">List Mappings</span></span>  
 <span data-ttu-id="6f802-105"><xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Zadejte []**, a <xref:System.String> typy se používají k vyjádření schématu XML definition language (XSD) seznamu typů.</span><span class="sxs-lookup"><span data-stu-id="6f802-105">The <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]**, and <xref:System.String> types are used to represent XML Schema definition language (XSD) list types.</span></span>  
  
## <a name="union-mappings"></a><span data-ttu-id="6f802-106">Union mapování</span><span class="sxs-lookup"><span data-stu-id="6f802-106">Union Mappings</span></span>  
 <span data-ttu-id="6f802-107">Union typy jsou reprezentované pomocí <xref:System.Xml.Schema.XmlAtomicValue> nebo <xref:System.String> typu.</span><span class="sxs-lookup"><span data-stu-id="6f802-107">Union types are represented using the <xref:System.Xml.Schema.XmlAtomicValue> or <xref:System.String> type.</span></span> <span data-ttu-id="6f802-108">Typ zdroje nebo typ cílového proto musí být vždy buď <xref:System.String> nebo <xref:System.Xml.Schema.XmlAtomicValue>.</span><span class="sxs-lookup"><span data-stu-id="6f802-108">The source type or the destination type must therefore always be either <xref:System.String> or <xref:System.Xml.Schema.XmlAtomicValue>.</span></span>  
  
 <span data-ttu-id="6f802-109">Pokud <xref:System.Xml.Schema.XmlSchemaDatatype> objekt představuje typ seznamu převede objekt vstupní řetězec hodnotu na seznam jeden nebo více objektů.</span><span class="sxs-lookup"><span data-stu-id="6f802-109">If the <xref:System.Xml.Schema.XmlSchemaDatatype> object represents a list type the object converts the input string value to a list of one or more objects.</span></span> <span data-ttu-id="6f802-110">Pokud <xref:System.Xml.Schema.XmlSchemaDatatype> představuje typu union, pak je proveden pokus o vstupní hodnotu analyzovat jako typ člena unie.</span><span class="sxs-lookup"><span data-stu-id="6f802-110">If the <xref:System.Xml.Schema.XmlSchemaDatatype> represents a union type then an attempt is made to parse the input value as a member type of the union.</span></span> <span data-ttu-id="6f802-111">Pokud se nezdaří pokus o analýzy pak převod je k pokusu o dalšího člena sjednocení a tak dále dokud převod je úspěšné, nebo nejsou žádné jiné typy člena a zkuste to, v takovém případě je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="6f802-111">If the parse attempt fails then the conversion is attempted with the next member of the union and so on until the conversion is successful, or there are no other member types to try, in which case an exception is thrown.</span></span>  
  
## <a name="differences-between-clr-and-xml-data-types"></a><span data-ttu-id="6f802-112">Rozdíly mezi datové typy XML a CLR</span><span class="sxs-lookup"><span data-stu-id="6f802-112">Differences Between CLR and XML Data Types</span></span>  
 <span data-ttu-id="6f802-113">Následující část popisuje některé problémy, o kterých může proběhnout mezi typy CLR a datové typy XML a jak jsou zpracovávány.</span><span class="sxs-lookup"><span data-stu-id="6f802-113">The following describes certain mismatches that can occur between CLR types and XML data types and how they are handled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f802-114">`xs` Předpona je namapována na http://www.w3.org/2001/XMLSchema a identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6f802-114">The `xs` prefix is mapped to the http://www.w3.org/2001/XMLSchema and namespace URI.</span></span>  
  
### <a name="systemtimespan-and-xsduration"></a><span data-ttu-id="6f802-115">System.TimeSpan a xs</span><span class="sxs-lookup"><span data-stu-id="6f802-115">System.TimeSpan and xs:duration</span></span>  
 <span data-ttu-id="6f802-116">`xs:duration` Typ je částečně pořadí, v tom, že existují ale ekvivalentní určité hodnoty doby trvání, které se liší.</span><span class="sxs-lookup"><span data-stu-id="6f802-116">The `xs:duration` type is partially ordered in that there are certain duration values that are different but equivalent.</span></span> <span data-ttu-id="6f802-117">To znamená, že pro `xs:duration` hodnota typu, například 1 měsíc (P1M) je menší než 32 dní (P32D) větší než 27 dní (P27D), odpovídající 28, 29 nebo 30 dnů.</span><span class="sxs-lookup"><span data-stu-id="6f802-117">This means that for the `xs:duration` type value such as 1 month (P1M) is less than 32 days (P32D), larger than 27 days (P27D) and equivalent to 28, 29 or 30 days.</span></span>  
  
 <span data-ttu-id="6f802-118"><xref:System.TimeSpan> Třída nepodporuje toto částečné řazení.</span><span class="sxs-lookup"><span data-stu-id="6f802-118">The <xref:System.TimeSpan> class does not support this partial ordering.</span></span> <span data-ttu-id="6f802-119">Místo toho se vybere určitý počet dní pro 1 rok a 1 měsíce; 365 dnů a 30 dní v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6f802-119">Instead, it picks a specific number of days for 1 year and 1 month; 365 days and 30 days respectively.</span></span>  
  
 <span data-ttu-id="6f802-120">Další informace o `xs:duration` zadejte najdete v tématu W3C XML schéma část 2: datové typy doporučení v http://www.w3.org/TR/xmlschema-2/.</span><span class="sxs-lookup"><span data-stu-id="6f802-120">For more information on the `xs:duration` type, see the W3C XML Schema Part 2: Datatypes Recommendation at http://www.w3.org/TR/xmlschema-2/.</span></span>  
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a><span data-ttu-id="6f802-121">: Time, typy Datum gregoriánského a System.DateTime</span><span class="sxs-lookup"><span data-stu-id="6f802-121">xs:time, Gregorian Date Types, and System.DateTime</span></span>  
 <span data-ttu-id="6f802-122">Při `xs:time` hodnota je namapována na <xref:System.DateTime> objekt, <xref:System.DateTime.MinValue> pole slouží k inicializaci vlastnosti kalendářních dat u <xref:System.DateTime> objektu (například <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, a <xref:System.DateTime.Day%2A>) na nejmenší možné <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6f802-122">When an `xs:time` value is mapped to a <xref:System.DateTime> object, the <xref:System.DateTime.MinValue> field is used to initialize the date properties of the <xref:System.DateTime> object (such as <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>) to the smallest possible <xref:System.DateTime> value.</span></span>  
  
 <span data-ttu-id="6f802-123">Podobně instancí `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` a `xs:gMonthDay` taky namapovaný na <xref:System.DateTime> objektu.</span><span class="sxs-lookup"><span data-stu-id="6f802-123">Similarly, instances of `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` and `xs:gMonthDay` are also mapped to a <xref:System.DateTime> object.</span></span> <span data-ttu-id="6f802-124">Nepoužívané vlastnosti <xref:System.DateTime> objekt jsou inicializovány na ty z <xref:System.DateTime.MinValue>.</span><span class="sxs-lookup"><span data-stu-id="6f802-124">Unused properties on the <xref:System.DateTime> object are initialized to those from <xref:System.DateTime.MinValue>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f802-125">Nelze spoléhat na <xref:System.DateTime.Year%2A?displayProperty=nameWithType> hodnotu, pokud je obsah typu `xs:gMonthDay`.</span><span class="sxs-lookup"><span data-stu-id="6f802-125">You cannot rely on the <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value when the content is typed as `xs:gMonthDay`.</span></span> <span data-ttu-id="6f802-126"><xref:System.DateTime.Year%2A?displayProperty=nameWithType> Hodnota je vždycky nastavený na 1904 v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="6f802-126">The <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value is always set to 1904 in this case.</span></span>  
  
### <a name="xsanyuri-and-systemuri"></a><span data-ttu-id="6f802-127">xs:anyURI a System.Uri</span><span class="sxs-lookup"><span data-stu-id="6f802-127">xs:anyURI and System.Uri</span></span>  
 <span data-ttu-id="6f802-128">Pokud instance `xs:anyURI` představuje relativní identifikátor URI je namapována na <xref:System.Uri>, <xref:System.Uri> objekt nemá základní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="6f802-128">When an instance of `xs:anyURI` that represents a relative URI is mapped to a <xref:System.Uri>, the <xref:System.Uri> object does not have a base URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f802-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f802-129">See Also</span></span>  
 [<span data-ttu-id="6f802-130">Podpora typu v třídách System.Xml</span><span class="sxs-lookup"><span data-stu-id="6f802-130">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
