---
title: GetXmlNamespace – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 4d6e738f4e3a47d73e37c395dd74fe19e99d81bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353196"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="84261-102">GetXmlNamespace – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84261-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="84261-103">Získá objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá zadané předponě oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="84261-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84261-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84261-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="84261-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="84261-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="84261-106">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="84261-106">Optional.</span></span> <span data-ttu-id="84261-107">Řetězec, který identifikuje předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="84261-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="84261-108">Je-li tento řetězec zadán, musí být platným identifikátorem XML.</span><span class="sxs-lookup"><span data-stu-id="84261-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="84261-109">Další informace najdete v tématu [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="84261-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="84261-110">Pokud není zadána žádná předpona, je vrácen výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="84261-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="84261-111">Pokud není zadán žádný výchozí obor názvů, je vrácen prázdný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="84261-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84261-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="84261-112">Return Value</span></span>  
 <span data-ttu-id="84261-113">Objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá předponě oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="84261-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84261-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84261-114">Remarks</span></span>  
 <span data-ttu-id="84261-115">Operátor `GetXmlNamespace` Získá objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá předponě oboru názvů XML `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="84261-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="84261-116">Předpony oboru názvů XML lze použít přímo v literálech XML a vlastnostech osy XML.</span><span class="sxs-lookup"><span data-stu-id="84261-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="84261-117">Je však nutné použít operátor `GetXmlNamespace` k převedení předpony oboru názvů na objekt <xref:System.Xml.Linq.XNamespace> předtím, než jej můžete použít ve svém kódu.</span><span class="sxs-lookup"><span data-stu-id="84261-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="84261-118">K objektu <xref:System.Xml.Linq.XNamespace> můžete připojit Nekvalifikovaný název elementu, abyste získali plně kvalifikovaný <xref:System.Xml.Linq.XName> objekt, který vyžaduje mnoho [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metod.</span><span class="sxs-lookup"><span data-stu-id="84261-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84261-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="84261-119">Example</span></span>  
 <span data-ttu-id="84261-120">Následující příklad importuje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="84261-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="84261-121">Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu, který má kvalifikovaný název `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="84261-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="84261-122">Poté předává tento podřízený uzel do dílčí rutiny `ShowName`, která vytvoří kvalifikovaný název pomocí operátoru `GetXmlNamespace`.</span><span class="sxs-lookup"><span data-stu-id="84261-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="84261-123">Podprogram `ShowName` pak předá metodě <xref:System.Xml.Linq.XNode.Ancestors%2A>, aby získal nadřazený `ns:contact` uzel.</span><span class="sxs-lookup"><span data-stu-id="84261-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="84261-124">Při volání `TestGetXmlNamespace.RunSample()`se zobrazí okno se zprávou, které obsahuje následující text:</span><span class="sxs-lookup"><span data-stu-id="84261-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="84261-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84261-125">See also</span></span>

- [<span data-ttu-id="84261-126">Příkaz Imports (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="84261-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="84261-127">Přístup k XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84261-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
