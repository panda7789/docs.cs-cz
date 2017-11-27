---
title: "Analýza kódu XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7ea83f83-a779-423a-9875-4ea4e51f97fc
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d262fd2177ac77ab5109362f94cc51d03c9563c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="parsing-xml-c"></a><span data-ttu-id="c1687-102">Analýza kódu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c1687-102">Parsing XML (C#)</span></span>
<span data-ttu-id="c1687-103">Témata v této části popisují, jak analyzovat dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="c1687-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1687-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c1687-104">In This Section</span></span>  
  
|<span data-ttu-id="c1687-105">Téma</span><span class="sxs-lookup"><span data-stu-id="c1687-105">Topic</span></span>|<span data-ttu-id="c1687-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c1687-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c1687-107">Postupy: Analýza řetězců (C#)</span><span class="sxs-lookup"><span data-stu-id="c1687-107">How to: Parse a String (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="c1687-108">Ukazuje, jak analyzovat řetězec k vytvoření strom XML.</span><span class="sxs-lookup"><span data-stu-id="c1687-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="c1687-109">Postupy: načtení XML ze souboru (C#)</span><span class="sxs-lookup"><span data-stu-id="c1687-109">How to: Load XML from a File (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="c1687-110">Ukazuje, jak načíst XML z identifikátoru URI pomocí <xref:System.Xml.Linq.XElement.Load%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="c1687-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="c1687-111">Zachování mezer při načítání nebo analýzu kódu XML</span><span class="sxs-lookup"><span data-stu-id="c1687-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml1.md)|<span data-ttu-id="c1687-112">Popisuje, jak řídit chování mezer [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] při načítání stromy XML.</span><span class="sxs-lookup"><span data-stu-id="c1687-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="c1687-113">Postupy: zachycení analýza chyb (C#)</span><span class="sxs-lookup"><span data-stu-id="c1687-113">How to: Catch Parsing Errors (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="c1687-114">Ukazuje, jak zjistit XML chybně formátovaný nebo je neplatný.</span><span class="sxs-lookup"><span data-stu-id="c1687-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="c1687-115">Postupy: vytvoření větve z XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="c1687-115">How to: Create a Tree from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="c1687-116">Ukazuje, jak vytvořit strom XML přímo z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c1687-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="c1687-117">Postupy: Stream fragmenty XML z XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="c1687-117">How to: Stream XML Fragments from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="c1687-118">Ukazuje, jak pomocí datového proudu XML fragmenty <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c1687-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="c1687-119">Až budete mít ke zpracování libovolně velké soubory XML, nemusí být vhodný načíst celý strom XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="c1687-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="c1687-120">Místo toho dá Streamovat fragmenty kódu XML.</span><span class="sxs-lookup"><span data-stu-id="c1687-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1687-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1687-121">See Also</span></span>  
 [<span data-ttu-id="c1687-122">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c1687-122">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
