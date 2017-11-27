---
title: "Analýza kódu XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bcbd7e2-d9f1-4c8f-80d6-39915fe17bd1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6eed674ff6168690e627abf8c5c13665c07c35aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="parsing-xml-visual-basic"></a><span data-ttu-id="cda38-102">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cda38-102">Parsing XML (Visual Basic)</span></span>
<span data-ttu-id="cda38-103">Témata v této části popisují, jak analyzovat dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="cda38-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cda38-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cda38-104">In This Section</span></span>  
  
|<span data-ttu-id="cda38-105">Téma</span><span class="sxs-lookup"><span data-stu-id="cda38-105">Topic</span></span>|<span data-ttu-id="cda38-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cda38-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="cda38-107">Postupy: Analýza řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cda38-107">How to: Parse a String (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="cda38-108">Ukazuje, jak analyzovat řetězec k vytvoření strom XML.</span><span class="sxs-lookup"><span data-stu-id="cda38-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="cda38-109">Postupy: načtení XML ze souboru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cda38-109">How to: Load XML from a File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="cda38-110">Ukazuje, jak načíst XML z identifikátoru URI pomocí <xref:System.Xml.Linq.XElement.Load%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="cda38-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="cda38-111">Zachování mezer při načítání nebo analýzu kódu XML</span><span class="sxs-lookup"><span data-stu-id="cda38-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml.md)|<span data-ttu-id="cda38-112">Popisuje, jak řídit chování mezer [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] při načítání stromy XML.</span><span class="sxs-lookup"><span data-stu-id="cda38-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="cda38-113">Postupy: zachycení analýza chyb (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cda38-113">How to: Catch Parsing Errors (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="cda38-114">Ukazuje, jak zjistit XML chybně formátovaný nebo je neplatný.</span><span class="sxs-lookup"><span data-stu-id="cda38-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="cda38-115">Postupy: vytvoření větve z objekt XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cda38-115">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="cda38-116">Ukazuje, jak vytvořit strom XML přímo z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="cda38-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="cda38-117">Postupy: Stream fragmenty XML z objekt XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cda38-117">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="cda38-118">Ukazuje, jak pomocí datového proudu XML fragmenty <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="cda38-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="cda38-119">Až budete mít ke zpracování libovolně velké soubory XML, nemusí být vhodný načíst celý strom XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="cda38-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="cda38-120">Místo toho dá Streamovat fragmenty kódu XML.</span><span class="sxs-lookup"><span data-stu-id="cda38-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cda38-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="cda38-121">See Also</span></span>  
 [<span data-ttu-id="cda38-122">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cda38-122">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
