---
title: Direktivy šablon stylů vložené v dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 19e25ab7262bb006144eea71e74bd7454066b3f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710151"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="14615-102">Direktivy šablon stylů vložené v dokumentu</span><span class="sxs-lookup"><span data-stu-id="14615-102">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="14615-103">Existující kód XML může občas obsahovat direktivu šablon stylů `<?xml:stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="14615-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="14615-104">Aplikace Microsoft Internet Explorer přijímá jako alternativu k `<?xml-stylesheet?>` syntaxi.</span><span class="sxs-lookup"><span data-stu-id="14615-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="14615-105">Pokud data XML obsahují `<?xml:stylesheet?>` direktivu, jak je znázorněno na následujících datech, pokus o načtení těchto dat do XML model DOM (Document Object Model) (DOM) vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="14615-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="14615-106">K tomu dochází, `<?xml:stylesheet?>` protože se v modelu DOM považuje neplatný **ProcessingInstruction** .</span><span class="sxs-lookup"><span data-stu-id="14615-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="14615-107">Jakékoli **ProcessingInstruction**, v závislosti na oborech názvů ve specifikaci XML, mohou být pouze názvy bez dvojtečky (NCNames), nikoli kvalifikované názvy (QName).</span><span class="sxs-lookup"><span data-stu-id="14615-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="14615-108">Z oddílu 6 specifikací oboru názvů ve specifikaci XML je účinek, aby metody **Load** a **LoadXml** splňovaly specifikace je v dokumentu:</span><span class="sxs-lookup"><span data-stu-id="14615-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="14615-109">Všechny typy prvků a názvy atributů obsahují buď žádnou, nebo jednu dvojtečku.</span><span class="sxs-lookup"><span data-stu-id="14615-109">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="14615-110">Názvy entit, cíle ProcessingInstruction ani názvy Notation neobsahují žádné dvojtečky.</span><span class="sxs-lookup"><span data-stu-id="14615-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="14615-111">V případě `<?xml:stylesheet?>` , že obsahuje dvojtečku, jste teď poznamenali pravidlo ve druhé odrážce.</span><span class="sxs-lookup"><span data-stu-id="14615-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="14615-112">V závislosti na konsorcium World Wide Web (W3C), které spojují [šablony stylů s dokumenty XML verze 1,0](https://www.w3.org/TR/xml-stylesheet/), je `<?xml-stylesheet?>`pokyn ke zpracování k přidružení šablony stylů XSLT k dokumentu XML s pomlčkou, která nahrazuje dvojtečku.</span><span class="sxs-lookup"><span data-stu-id="14615-112">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="14615-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="14615-113">See also</span></span>

- [<span data-ttu-id="14615-114">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="14615-114">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
