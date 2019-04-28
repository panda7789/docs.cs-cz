---
title: Analýza kódu XML (C#)
ms.date: 07/20/2015
ms.assetid: 7ea83f83-a779-423a-9875-4ea4e51f97fc
ms.openlocfilehash: f19e5a316621262bfe0f3fb56a13275336cf763f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61682206"
---
# <a name="parsing-xml-c"></a><span data-ttu-id="baa68-102">Analýza kódu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="baa68-102">Parsing XML (C#)</span></span>
<span data-ttu-id="baa68-103">Témata v této části popisují, jak k analýze dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="baa68-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="baa68-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="baa68-104">In This Section</span></span>  
  
|<span data-ttu-id="baa68-105">Téma</span><span class="sxs-lookup"><span data-stu-id="baa68-105">Topic</span></span>|<span data-ttu-id="baa68-106">Popis</span><span class="sxs-lookup"><span data-stu-id="baa68-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="baa68-107">Postupy: Analyzovat řetězec (C#)</span><span class="sxs-lookup"><span data-stu-id="baa68-107">How to: Parse a String (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="baa68-108">Ukazuje, jak analyzovat řetězec k vytvoření stromu XML.</span><span class="sxs-lookup"><span data-stu-id="baa68-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="baa68-109">Postupy: Načtení XML ze souboru (C#)</span><span class="sxs-lookup"><span data-stu-id="baa68-109">How to: Load XML from a File (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="baa68-110">Ukazuje, jak načíst XML z identifikátoru URI pomocí <xref:System.Xml.Linq.XElement.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="baa68-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="baa68-111">Zachování prázdných znaků při načítání nebo analýze XML</span><span class="sxs-lookup"><span data-stu-id="baa68-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml1.md)|<span data-ttu-id="baa68-112">Popisuje, jak řídit chování mezer [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] při načítání stromů XML.</span><span class="sxs-lookup"><span data-stu-id="baa68-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="baa68-113">Postupy: Zachycení chyb při analýze (C#)</span><span class="sxs-lookup"><span data-stu-id="baa68-113">How to: Catch Parsing Errors (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="baa68-114">Ukazuje, jak detekovat XML chybně vytvořený nebo je neplatný.</span><span class="sxs-lookup"><span data-stu-id="baa68-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="baa68-115">Postupy: Vytvoření stromu ze třídy XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="baa68-115">How to: Create a Tree from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="baa68-116">Ukazuje, jak vytvořit stromu XML přímo ze <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="baa68-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="baa68-117">Postupy: Stream fragmentů XML ze třídy XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="baa68-117">How to: Stream XML Fragments from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="baa68-118">Ukazuje, jak pomocí streamování fragmentů XML <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="baa68-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="baa68-119">Až budete mít ke zpracování libovolně velkých souborů XML, nemusí být možné načíst celý strom XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="baa68-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="baa68-120">Místo toho můžete streamování fragmentů XML.</span><span class="sxs-lookup"><span data-stu-id="baa68-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="baa68-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="baa68-121">See also</span></span>

- [<span data-ttu-id="baa68-122">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="baa68-122">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
