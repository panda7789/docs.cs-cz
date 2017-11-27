---
title: "Při načítání nebo analýza XML2 zachování prázdných znaků"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d99cea37bb9817c40a6d3876b72ccdbd84d7e7ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a><span data-ttu-id="61921-102">Zachování mezer při načítání nebo analýzu kódu XML</span><span class="sxs-lookup"><span data-stu-id="61921-102">Preserving White Space while Loading or Parsing XML</span></span>
<span data-ttu-id="61921-103">Toto téma popisuje, jak řídit chování mezer [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61921-103">This topic describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="61921-104">Běžný scénář je číst zobrazují odsazené XML, vytvořte ve stromu v paměti XML bez mezer text uzlů (tedy ne zachování mezer), provádění některých operací na soubor XML a potom uložte soubor XML s odsazení.</span><span class="sxs-lookup"><span data-stu-id="61921-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="61921-105">Při serializaci XML s formátování se zachová jenom významné mezer ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="61921-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="61921-106">Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61921-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="61921-107">Další z typických možností je číst a upravovat kód XML, který je už záměrně zobrazují odsazené.</span><span class="sxs-lookup"><span data-stu-id="61921-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="61921-108">Možná chcete změnit toto odsazení žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="61921-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="61921-109">To uděláte v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], zachovat mezer při načtení nebo analyzovat soubor XML a zakázat formátování při serializaci XML.</span><span class="sxs-lookup"><span data-stu-id="61921-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="61921-110">Toto téma popisuje chování mezer metody, která naplní stromy XML.</span><span class="sxs-lookup"><span data-stu-id="61921-110">This topic describes the white space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="61921-111">Informace o řízení mezer při serializaci XML stromy najdete v tématu [zachování mezer při serializaci](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="61921-111">For information about controlling white space when you serialize XML trees, see [Preserving White Space While Serializing](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="61921-112">Chování metod, která naplní stromy XML</span><span class="sxs-lookup"><span data-stu-id="61921-112">Behavior of Methods that Populate XML Trees</span></span>  
 <span data-ttu-id="61921-113">Následující metody v <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XDocument> třídy naplnit strom XML.</span><span class="sxs-lookup"><span data-stu-id="61921-113">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="61921-114">Ve stromu XML ze souboru, může naplnění <xref:System.IO.TextReader>, <xref:System.Xml.XmlReader>, nebo řetězec:</span><span class="sxs-lookup"><span data-stu-id="61921-114">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="61921-115">Pokud metoda nevyžaduje <xref:System.Xml.Linq.LoadOptions> jako argument, nebude metoda zachování zanedbatelný prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="61921-115">If the method does not take <xref:System.Xml.Linq.LoadOptions> as an argument, the method will not preserve insignificant white space.</span></span>  
  
 <span data-ttu-id="61921-116">Ve většině případů, pokud metoda přebírá <xref:System.Xml.Linq.LoadOptions> jako argument, můžete volitelně zachovat mezer zanedbatelný jako textové uzly ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="61921-116">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="61921-117">Ale pokud metoda načítá XML z <xref:System.Xml.XmlReader>, pak se <xref:System.Xml.XmlReader> Určuje, zda bude zachována mezer, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="61921-117">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="61921-118">Nastavení <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> nebude mít žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="61921-118">Setting <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> will have no effect.</span></span>  
  
 <span data-ttu-id="61921-119">Pomocí těchto metod, pokud je zachovají mezeru, mezer zanedbatelný vložena do stromu XML jako <xref:System.Xml.Linq.XText> uzlů.</span><span class="sxs-lookup"><span data-stu-id="61921-119">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="61921-120">Pokud není zachovají mezeru, nejsou vložit textové uzly.</span><span class="sxs-lookup"><span data-stu-id="61921-120">If white space is not preserved, text nodes are not inserted.</span></span>  
  
 <span data-ttu-id="61921-121">Ve stromu XML můžete vytvořit pomocí <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="61921-121">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="61921-122">Uzly, které se zapisují do <xref:System.Xml.XmlWriter> zaplní se ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="61921-122">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="61921-123">Při sestavování ve stromu XML pomocí této metody všechny uzly jsou však zachovaných bez ohledu na to, zda uzel je prázdný znak nebo Ne, nebo jestli je prázdné místo důležité nebo ne.</span><span class="sxs-lookup"><span data-stu-id="61921-123">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61921-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="61921-124">See Also</span></span>  
 [<span data-ttu-id="61921-125">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61921-125">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
