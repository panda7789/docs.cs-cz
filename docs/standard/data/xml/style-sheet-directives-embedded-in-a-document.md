---
title: Direktivy šablon stylů vložené v dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65987c5e29d593758b21259d6367202c882df2de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026936"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="40cf7-102">Direktivy šablon stylů vložené v dokumentu</span><span class="sxs-lookup"><span data-stu-id="40cf7-102">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="40cf7-103">V některých případech existující kód XML obsahuje direktiva list stylu `<?xml:stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="40cf7-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="40cf7-104">Microsoft Internet Explorer přijímá to jako alternativu k `<?xml-stylesheet?>` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="40cf7-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="40cf7-105">Pokud XML data obsahuje `<?xml:stylesheet?>` direktiv, jak je znázorněno v následující data pokusu o načtení těchto dat do XML Document Object Model (DOM) dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="40cf7-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="40cf7-106">K tomu dochází, `<?xml:stylesheet?>` je považován za neplatný **ProcessingInstruction** do modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="40cf7-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="40cf7-107">Žádné **ProcessingInstruction**, podle oborů názvů ve specifikaci XML, může obsahovat jenom názvy no dvojtečka (NCNames), na rozdíl od kvalifikované názvy (QNames).</span><span class="sxs-lookup"><span data-stu-id="40cf7-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="40cf7-108">Z část 6 oborů názvů ve specifikaci XML, má vliv **zatížení** a **příkaz LoadXml** metody v souladu s specifikace, která je v dokumentu:</span><span class="sxs-lookup"><span data-stu-id="40cf7-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="40cf7-109">Všechny názvy atributů a typy prvků obsahovat dvojtečku nebo vůbec.</span><span class="sxs-lookup"><span data-stu-id="40cf7-109">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="40cf7-110">Žádné názvy entit, ProcessingInstruction cíle nebo názvy výpisů obsahovat jakékoli použití dvojteček.</span><span class="sxs-lookup"><span data-stu-id="40cf7-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="40cf7-111">S `<?xml:stylesheet?>` obsahuje dvojtečku, můžete nyní porušovat pravidla v druhém odrážky.</span><span class="sxs-lookup"><span data-stu-id="40cf7-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="40cf7-112">Podle World Wide Web Consortium (W3C) [přidružení šablony stylů XML dokumenty verze 1.0 doporučení](https://www.w3.org/TR/xml-stylesheet/), instrukce pro zpracování šablony stylů XSLT přidružení k dokumentu XML je `<?xml-stylesheet?>`, se nahrazení dvojtečka Dash.</span><span class="sxs-lookup"><span data-stu-id="40cf7-112">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="40cf7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40cf7-113">See also</span></span>

- [<span data-ttu-id="40cf7-114">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="40cf7-114">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
