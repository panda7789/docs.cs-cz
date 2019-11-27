---
title: Názvy deklarovaných XML elementů a atributů
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 12fbd1f4332391b1acdcf12e101d82627ebbeaff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335988"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="38a22-102">Názvy deklarovaných XML elementů a atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38a22-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="38a22-103">Toto téma poskytuje pokyny pro Visual Basic pro pojmenovávání elementů XML a atributů v literálech XML.</span><span class="sxs-lookup"><span data-stu-id="38a22-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="38a22-104">V literálu XML můžete zadat místní název nebo kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="38a22-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="38a22-105">Úplný název se skládá z předpony oboru názvů XML, dvojtečky a místního názvu.</span><span class="sxs-lookup"><span data-stu-id="38a22-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="38a22-106">Další informace o předponách oboru názvů XML naleznete v tématu [literál elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="38a22-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="38a22-107">Pravidla</span><span class="sxs-lookup"><span data-stu-id="38a22-107">Rules</span></span>  
 <span data-ttu-id="38a22-108">Místní název elementu nebo atributu v Visual Basic musí splňovat následující pravidla.</span><span class="sxs-lookup"><span data-stu-id="38a22-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
- <span data-ttu-id="38a22-109">Může začít s oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="38a22-109">It can begin with a namespace.</span></span> <span data-ttu-id="38a22-110">Musí začínat abecedním znakem nebo podtržítkem (`_`).</span><span class="sxs-lookup"><span data-stu-id="38a22-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="38a22-111">Musí obsahovat jenom abecední znaky, desítkové číslice, podtržítka, tečky (.) a spojovníky (-).</span><span class="sxs-lookup"><span data-stu-id="38a22-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
- <span data-ttu-id="38a22-112">Nesmí být delší než 1 024 znaků.</span><span class="sxs-lookup"><span data-stu-id="38a22-112">It must not be more than 1,024 characters long.</span></span>  
  
- <span data-ttu-id="38a22-113">Dvojtečky, které se zobrazují v názvech označují vymezení oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="38a22-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="38a22-114">Proto můžete použít dvojtečky pouze k určení oboru názvů XML pro konkrétní název.</span><span class="sxs-lookup"><span data-stu-id="38a22-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="38a22-115">Kromě toho byste měli dodržovat následující pravidla.</span><span class="sxs-lookup"><span data-stu-id="38a22-115">In addition, you should adhere to the following guideline.</span></span>  
  
- <span data-ttu-id="38a22-116">Specifikace XML 1,0 rezervuje všechny názvy začínající řetězcem "XML" a jakékoli variace v malých písmenech.</span><span class="sxs-lookup"><span data-stu-id="38a22-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="38a22-117">Proto tyto názvy nepoužívejte pro názvy elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="38a22-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="38a22-118">Pokyny pro délku názvu</span><span class="sxs-lookup"><span data-stu-id="38a22-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="38a22-119">V důsledku praktického hlediska by měl být název co nejkratší, ale stále jasně identifikuje povahu prvku.</span><span class="sxs-lookup"><span data-stu-id="38a22-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="38a22-120">To zlepšuje čitelnost kódu a zkracuje délku řádku a velikost zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="38a22-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="38a22-121">Nicméně vaše jméno by nemělo být tak krátké, že není dostatečně popisovat element nebo jak ho váš kód používá.</span><span class="sxs-lookup"><span data-stu-id="38a22-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="38a22-122">To je důležité pro čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="38a22-122">This is important for the readability of your code.</span></span> <span data-ttu-id="38a22-123">Pokud se někdo jiný snaží ho pochopit, nebo pokud si ho po jeho zapsání sami napíšete, můžete si ušetřit čas vhodnými názvy elementů.</span><span class="sxs-lookup"><span data-stu-id="38a22-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="38a22-124">Rozlišování velkých a malých písmen v názvech</span><span class="sxs-lookup"><span data-stu-id="38a22-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="38a22-125">Názvy elementů XML rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="38a22-125">XML element names are case sensitive.</span></span> <span data-ttu-id="38a22-126">To znamená, že když kompilátor Visual Basic Porovná dva názvy, které se liší pouze v abecedním případě, interpretuje je jako jiné názvy.</span><span class="sxs-lookup"><span data-stu-id="38a22-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="38a22-127">Například interpretuje `ABC` a `abc` jako odkazování na samostatné prvky.</span><span class="sxs-lookup"><span data-stu-id="38a22-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="38a22-128">XML – obory názvů</span><span class="sxs-lookup"><span data-stu-id="38a22-128">XML Namespaces</span></span>  
 <span data-ttu-id="38a22-129">Při vytváření literálu elementu XML můžete zadat předponu oboru názvů XML pro název elementu.</span><span class="sxs-lookup"><span data-stu-id="38a22-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="38a22-130">Další informace naleznete v tématu [literál elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="38a22-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a22-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38a22-131">See also</span></span>

- [<span data-ttu-id="38a22-132">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38a22-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="38a22-133">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="38a22-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
