---
title: Názvy deklarovaných XML elementů a atributů (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07666ead0770c8055a62f75cb481648b0c72ef8b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="6e8df-102">Názvy deklarovaných XML elementů a atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e8df-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="6e8df-103">Toto téma obsahuje pokyny jazyka Visual Basic pro pojmenování XML elementů a atributů v literálech XML.</span><span class="sxs-lookup"><span data-stu-id="6e8df-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="6e8df-104">V XML literálu můžete zadat místní název nebo kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="6e8df-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="6e8df-105">Úplný název se skládá z předponu oboru názvů XML, dvojtečkou a místní název.</span><span class="sxs-lookup"><span data-stu-id="6e8df-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="6e8df-106">Další informace o předpon oboru názvů XML, najdete v části [literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="6e8df-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6e8df-107">Pravidla</span><span class="sxs-lookup"><span data-stu-id="6e8df-107">Rules</span></span>  
 <span data-ttu-id="6e8df-108">Místní název element nebo atribut v jazyce Visual Basic musí splňovat následující pravidla.</span><span class="sxs-lookup"><span data-stu-id="6e8df-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="6e8df-109">Ho můžete začít s názvů.</span><span class="sxs-lookup"><span data-stu-id="6e8df-109">It can begin with a namespace.</span></span> <span data-ttu-id="6e8df-110">Musí začínat alfabetickým znakem nebo podtržítkem (`_`).</span><span class="sxs-lookup"><span data-stu-id="6e8df-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="6e8df-111">Musí obsahovat pouze abecední znaky, číslice desítkové soustavy, podtržítka, tečky (.) a pomlčky (-).</span><span class="sxs-lookup"><span data-stu-id="6e8df-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="6e8df-112">Nesmí být víc než 1 024 znaků.</span><span class="sxs-lookup"><span data-stu-id="6e8df-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="6e8df-113">Použití dvojteček, které se zobrazují v názvech znamenat vymezení oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6e8df-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="6e8df-114">Proto můžete dvojtečky pouze k určení oboru názvů XML pro určitý název.</span><span class="sxs-lookup"><span data-stu-id="6e8df-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="6e8df-115">Kromě toho by měl splňovat tyto zásady.</span><span class="sxs-lookup"><span data-stu-id="6e8df-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="6e8df-116">Specifikace XML 1.0 si vyhrazuje všechna názvy začíná tímto řetězcem "xml" jakékoliv změny malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6e8df-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="6e8df-117">Proto nepoužívejte tyto názvy pro vaše element a atributů.</span><span class="sxs-lookup"><span data-stu-id="6e8df-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="6e8df-118">Název délka pokyny</span><span class="sxs-lookup"><span data-stu-id="6e8df-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="6e8df-119">Prakticky musí být název co nejkratší při identifikaci stále jasně povaha elementu.</span><span class="sxs-lookup"><span data-stu-id="6e8df-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="6e8df-120">Tím zlepšuje čitelnost kódu a snižuje velikost řádku délku a zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="6e8df-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="6e8df-121">Název nesmí být však krátký tak, že nepopisuje adekvátní element nebo jak se používá váš kód.</span><span class="sxs-lookup"><span data-stu-id="6e8df-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="6e8df-122">To je důležité pro čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="6e8df-122">This is important for the readability of your code.</span></span> <span data-ttu-id="6e8df-123">Pokud někdo jiný pokouší porozumět, nebo pokud sami hledáte na to dlouhou dobu, po ho napsal, názvy odpovídající element ušetřit čas.</span><span class="sxs-lookup"><span data-stu-id="6e8df-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="6e8df-124">Malá a velká písmena v názvech</span><span class="sxs-lookup"><span data-stu-id="6e8df-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="6e8df-125">Názvy elementů XML rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6e8df-125">XML element names are case sensitive.</span></span> <span data-ttu-id="6e8df-126">To znamená, že když Visual Basic – kompilátor porovná dva názvy, které se liší v abecedním případě pouze, je je interpretuje jako odlišné názvy.</span><span class="sxs-lookup"><span data-stu-id="6e8df-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="6e8df-127">Například interpretuje `ABC` a `abc` jako odkazující na jednotlivé prvky.</span><span class="sxs-lookup"><span data-stu-id="6e8df-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="6e8df-128">Obory názvů XML</span><span class="sxs-lookup"><span data-stu-id="6e8df-128">XML Namespaces</span></span>  
 <span data-ttu-id="6e8df-129">Při vytváření literál elementu XML, můžete zadat předponu oboru názvů XML pro název elementu.</span><span class="sxs-lookup"><span data-stu-id="6e8df-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="6e8df-130">Další informace najdete v tématu [literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="6e8df-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e8df-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e8df-131">See Also</span></span>  
 [<span data-ttu-id="6e8df-132">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e8df-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="6e8df-133">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="6e8df-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
