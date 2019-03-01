---
title: GetXmlNamespace – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: e02a7c5c9859352aa07bfaa741b80b7fd18d1da4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979902"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="dec0a-102">GetXmlNamespace – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dec0a-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="dec0a-103">Získá <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá zadané předpony oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="dec0a-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dec0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dec0a-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="dec0a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="dec0a-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="dec0a-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="dec0a-106">Optional.</span></span> <span data-ttu-id="dec0a-107">Řetězec, který identifikuje předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="dec0a-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="dec0a-108">Pokud je zadané, musí být tento řetězec neplatný identifikátor XML.</span><span class="sxs-lookup"><span data-stu-id="dec0a-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="dec0a-109">Další informace najdete v tématu [názvy z deklarované XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="dec0a-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="dec0a-110">Pokud není zadána žádná předpona, vrátí se výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="dec0a-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="dec0a-111">Pokud není zadán žádný výchozí obor názvů, je vrácena prázdný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="dec0a-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dec0a-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dec0a-112">Return Value</span></span>  
 <span data-ttu-id="dec0a-113"><xref:System.Xml.Linq.XNamespace> Objekt, který odpovídá předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="dec0a-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dec0a-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dec0a-114">Remarks</span></span>  
 <span data-ttu-id="dec0a-115">`GetXmlNamespace` Získá operátor <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá předponu oboru názvů XML `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="dec0a-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="dec0a-116">Můžete používat předpony oboru názvů XML přímo v literály XML a vlastnosti OS XML.</span><span class="sxs-lookup"><span data-stu-id="dec0a-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="dec0a-117">Ale musí používat `GetXmlNamespace` operátor převodu předpony oboru názvů <xref:System.Xml.Linq.XNamespace> objektu před použitím v kódu.</span><span class="sxs-lookup"><span data-stu-id="dec0a-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="dec0a-118">Můžete přidat název nekvalifikované elementu do <xref:System.Xml.Linq.XNamespace> můžete získat plně kvalifikovaný <xref:System.Xml.Linq.XName> objekt, který mnoho [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metody vyžadují.</span><span class="sxs-lookup"><span data-stu-id="dec0a-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dec0a-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="dec0a-119">Example</span></span>  
 <span data-ttu-id="dec0a-120">Následující příklad importuje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="dec0a-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="dec0a-121">Poté použije předponu oboru názvů XML vytvoření literálu a přístup k první podřízený uzel, který má úplný název `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="dec0a-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="dec0a-122">Pak předá tento podřízeného uzlu `ShowName` podprogram, který vytvoří úplný název pomocí `GetXmlNamespace` operátor.</span><span class="sxs-lookup"><span data-stu-id="dec0a-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="dec0a-123">`ShowName` Podprogram pak předá kvalifikovaný název <xref:System.Xml.Linq.XNode.Ancestors%2A> metodu k získání nadřazené `ns:contact` uzlu.</span><span class="sxs-lookup"><span data-stu-id="dec0a-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="dec0a-124">Při volání `TestGetXmlNamespace.RunSample()`, zobrazí okno se zprávou, která obsahuje následující text:</span><span class="sxs-lookup"><span data-stu-id="dec0a-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="dec0a-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dec0a-125">See also</span></span>
- [<span data-ttu-id="dec0a-126">Příkaz Imports (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="dec0a-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="dec0a-127">Přístup ke XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dec0a-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
