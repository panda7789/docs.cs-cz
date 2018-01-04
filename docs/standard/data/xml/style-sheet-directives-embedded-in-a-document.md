---
title: "Direktivy list stylu vložených v dokumentu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b0d4589dc73b4effeff553e5b7bf5562a7602c2d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="9922e-102">Direktivy list stylu vložených v dokumentu</span><span class="sxs-lookup"><span data-stu-id="9922e-102">Style Sheet Directives Embedded in a Document</span></span>
<span data-ttu-id="9922e-103">V některých případech existující soubor XML obsahuje direktiva list stylu z `<?xml:stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="9922e-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="9922e-104">Aplikace Microsoft Internet Explorer to přijímá jako alternativu k `<?xml-stylesheet?>` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="9922e-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="9922e-105">Když se XML data obsahuje `<?xml:stylesheet?>` direktivy, jak je uvedené v následující data pokusu o načtení tato data do XML modelu DOM (Document Object) vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="9922e-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 <span data-ttu-id="9922e-106">K tomu dochází, protože `<?xml:stylesheet?>` se považuje za neplatný **ProcessingInstruction** do modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="9922e-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="9922e-107">Všechny **ProcessingInstruction**, podle obory názvů ve specifikaci XML, může být pouze názvy ne dvojtečka (NCNames), a kvalifikované názvy (QNames).</span><span class="sxs-lookup"><span data-stu-id="9922e-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>  
  
 <span data-ttu-id="9922e-108">Z části 6 oborů názvů ve specifikaci XML, účinek toho, že **zatížení** a **příkaz LoadXml** metody v souladu s specifikace je, že v dokumentu:</span><span class="sxs-lookup"><span data-stu-id="9922e-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>  
  
-   <span data-ttu-id="9922e-109">Všechny typy elementů a atributů názvy obsahovat jednou nebo středníkem.</span><span class="sxs-lookup"><span data-stu-id="9922e-109">All element types and attribute names contain either zero or one colon.</span></span>  
  
-   <span data-ttu-id="9922e-110">Žádné entity názvů, ProcessingInstruction cíle nebo zápis obsahovat dvojtečku.</span><span class="sxs-lookup"><span data-stu-id="9922e-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>  
  
 <span data-ttu-id="9922e-111">Pomocí `<?xml:stylesheet?>` obsahující dvojtečkou, můžete nyní porušují pravidlo v druhém bodě.</span><span class="sxs-lookup"><span data-stu-id="9922e-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>  
  
 <span data-ttu-id="9922e-112">Podle World Wide Web Consortium (W3C) přidružení šablony stylů s dokumenty XML verze 1.0 doporučení, nacházející se v www.w3.org/TR/xml-stylesheet, pokyny pro zpracování stylů XSLT přidružit dokument XML je `<?xml-stylesheet?>`, s pomlčkou nahrazení dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="9922e-112">According to the World Wide Web Consortium (W3C) Associating Style Sheets with XML documents Version 1.0 Recommendation, located at www.w3.org/TR/xml-stylesheet, the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9922e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="9922e-113">See Also</span></span>  
 [<span data-ttu-id="9922e-114">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="9922e-114">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
