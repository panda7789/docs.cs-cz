---
title: Analýza XML
ms.date: 07/20/2015
ms.assetid: 5bcbd7e2-d9f1-4c8f-80d6-39915fe17bd1
ms.openlocfilehash: 3517a0925e886dcd3d2d7860be606c4e44127cd6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406856"
---
# <a name="parsing-xml-visual-basic"></a><span data-ttu-id="a2da8-102">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2da8-102">Parsing XML (Visual Basic)</span></span>
<span data-ttu-id="a2da8-103">Témata v této části popisují, jak analyzovat dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="a2da8-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2da8-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a2da8-104">In This Section</span></span>  
  
|<span data-ttu-id="a2da8-105">Téma</span><span class="sxs-lookup"><span data-stu-id="a2da8-105">Topic</span></span>|<span data-ttu-id="a2da8-106">Description</span><span class="sxs-lookup"><span data-stu-id="a2da8-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a2da8-107">Postupy: Analýza řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2da8-107">How to: Parse a String (Visual Basic)</span></span>](how-to-parse-a-string.md)|<span data-ttu-id="a2da8-108">Ukazuje, jak analyzovat řetězec pro vytvoření stromu XML.</span><span class="sxs-lookup"><span data-stu-id="a2da8-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="a2da8-109">Postupy: načtení XML ze souboru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2da8-109">How to: Load XML from a File (Visual Basic)</span></span>](how-to-load-xml-from-a-file.md)|<span data-ttu-id="a2da8-110">Ukazuje, jak načíst XML z identifikátoru URI pomocí <xref:System.Xml.Linq.XElement.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a2da8-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="a2da8-111">Zachování prázdných znaků při načítání nebo analýze XML</span><span class="sxs-lookup"><span data-stu-id="a2da8-111">Preserving White Space while Loading or Parsing XML</span></span>](preserving-white-space-while-loading-or-parsing-xml.md)|<span data-ttu-id="a2da8-112">Popisuje, jak řídit chování prázdného místa [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] při načítání stromů XML.</span><span class="sxs-lookup"><span data-stu-id="a2da8-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="a2da8-113">Postupy: zachycení chyb při analýze (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2da8-113">How to: Catch Parsing Errors (Visual Basic)</span></span>](how-to-catch-parsing-errors.md)|<span data-ttu-id="a2da8-114">Ukazuje, jak rozpoznat chybně vytvořený nebo neplatný kód XML.</span><span class="sxs-lookup"><span data-stu-id="a2da8-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="a2da8-115">Postupy: vytvoření stromu ze třídy XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2da8-115">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>](how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="a2da8-116">Ukazuje, jak vytvořit strom XML přímo z <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="a2da8-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="a2da8-117">Postupy: streamování fragmentů XML ze třídy XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2da8-117">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>](how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="a2da8-118">Ukazuje, jak streamovat fragmenty XML pomocí <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="a2da8-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="a2da8-119">Pokud je nutné zpracovat libovolně velké soubory XML, nemusí být vhodné načíst celý strom XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="a2da8-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="a2da8-120">Místo toho můžete streamovat fragmenty XML.</span><span class="sxs-lookup"><span data-stu-id="a2da8-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2da8-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2da8-121">See also</span></span>

- [<span data-ttu-id="a2da8-122">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2da8-122">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
