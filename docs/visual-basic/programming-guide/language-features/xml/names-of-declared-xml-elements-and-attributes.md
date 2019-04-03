---
title: Názvy deklarovaných XML elementů a atributů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 2221f2677183cf360fa82a4d73a679a8b68927d1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819681"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="b8c07-102">Názvy deklarovaných XML elementů a atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8c07-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="b8c07-103">Toto téma obsahuje pokyny pro Visual Basic pro vytváření názvů XML elementů a atributů v literálech XML.</span><span class="sxs-lookup"><span data-stu-id="b8c07-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="b8c07-104">V literálu XML můžete zadat místní název nebo kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="b8c07-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="b8c07-105">Úplný název se skládá z předponu oboru názvů XML, dvojtečku a místní název.</span><span class="sxs-lookup"><span data-stu-id="b8c07-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="b8c07-106">Další informace o předpon názvového prostoru XML, naleznete v tématu [literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="b8c07-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b8c07-107">pravidla</span><span class="sxs-lookup"><span data-stu-id="b8c07-107">Rules</span></span>  
 <span data-ttu-id="b8c07-108">Místní název elementu nebo atributu v jazyce Visual Basic musí splňovat následující pravidla.</span><span class="sxs-lookup"><span data-stu-id="b8c07-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="b8c07-109">Můžete začít s oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="b8c07-109">It can begin with a namespace.</span></span> <span data-ttu-id="b8c07-110">Musí začínat znakem abecedy nebo podtržítkem (`_`).</span><span class="sxs-lookup"><span data-stu-id="b8c07-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="b8c07-111">Musí obsahovat jenom abecední znaky, desítkové číslice, podtržítka, tečky (.) a pomlčky (-).</span><span class="sxs-lookup"><span data-stu-id="b8c07-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="b8c07-112">Nesmí být více než 1024 znaků.</span><span class="sxs-lookup"><span data-stu-id="b8c07-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="b8c07-113">Použití dvojteček, které se zobrazují v názvech označení vymezení oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b8c07-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="b8c07-114">Proto můžete pomocí dvojtečky pouze k určení obor názvů XML pro konkrétní název.</span><span class="sxs-lookup"><span data-stu-id="b8c07-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="b8c07-115">Kromě toho by měl splňovat následujícími pravidly.</span><span class="sxs-lookup"><span data-stu-id="b8c07-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="b8c07-116">Specifikace XML 1.0 si vyhrazuje všechna jména začíná tímto řetězcem "xml" jakékoliv změny malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="b8c07-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="b8c07-117">Proto nepoužívejte tyto názvy pro prvek a atributů.</span><span class="sxs-lookup"><span data-stu-id="b8c07-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="b8c07-118">Pokyny pro délka názvu</span><span class="sxs-lookup"><span data-stu-id="b8c07-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="b8c07-119">Prakticky, název by měl být co nejkratší při identifikaci zjevně povaze elementu.</span><span class="sxs-lookup"><span data-stu-id="b8c07-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="b8c07-120">To zlepšuje čitelnost vašeho kódu a zmenší velikost řádku délku a zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="b8c07-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="b8c07-121">Vaše jméno však by neměl být tak krátký, nezabývá se odpovídajícím způsobem elementu nebo jak se váš kód používá.</span><span class="sxs-lookup"><span data-stu-id="b8c07-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="b8c07-122">To je důležité pro čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="b8c07-122">This is important for the readability of your code.</span></span> <span data-ttu-id="b8c07-123">Pokud někdo jiný se snaží ho chápat, nebo pokud chcete sami se na něj dlouhou dobu, po ho napsal, odpovídající prvek názvy můžete ušetřit čas.</span><span class="sxs-lookup"><span data-stu-id="b8c07-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="b8c07-124">Rozlišování velikosti písmen v názvech</span><span class="sxs-lookup"><span data-stu-id="b8c07-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="b8c07-125">Názvy elementů XML jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="b8c07-125">XML element names are case sensitive.</span></span> <span data-ttu-id="b8c07-126">To znamená, že když kompilátor jazyka Visual Basic porovná dva názvy, které se liší abecedním pouze velikostí písmen, to je interpretuje jako odlišné názvy.</span><span class="sxs-lookup"><span data-stu-id="b8c07-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="b8c07-127">Například interpretuje `ABC` a `abc` jako odkazující na jednotlivé prvky.</span><span class="sxs-lookup"><span data-stu-id="b8c07-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="b8c07-128">Obory názvů XML</span><span class="sxs-lookup"><span data-stu-id="b8c07-128">XML Namespaces</span></span>  
 <span data-ttu-id="b8c07-129">Při vytváření XML element literal, můžete zadat předponu oboru názvů XML pro název elementu.</span><span class="sxs-lookup"><span data-stu-id="b8c07-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="b8c07-130">Další informace najdete v tématu [literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="b8c07-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c07-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8c07-131">See also</span></span>

- [<span data-ttu-id="b8c07-132">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b8c07-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="b8c07-133">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="b8c07-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
