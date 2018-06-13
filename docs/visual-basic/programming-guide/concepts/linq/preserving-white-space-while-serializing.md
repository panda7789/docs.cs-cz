---
title: Zachování mezer při Serializing2
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: a08d69a817c3e493e571d1b3b98f6f2a144ad995
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644976"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="9f50c-102">Zachování bílé místo při serializaci</span><span class="sxs-lookup"><span data-stu-id="9f50c-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="9f50c-103">Toto téma popisuje, jak řídit mezer při serializaci strom XML.</span><span class="sxs-lookup"><span data-stu-id="9f50c-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="9f50c-104">Běžný scénář je číst zobrazují odsazené XML, vytvořte ve stromu v paměti XML bez mezer text uzlů (tedy ne zachování mezer), provádění některých operací na soubor XML a potom uložte soubor XML s odsazení.</span><span class="sxs-lookup"><span data-stu-id="9f50c-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="9f50c-105">Při serializaci XML s formátování se zachová jenom významné mezer ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="9f50c-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="9f50c-106">Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f50c-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="9f50c-107">Další z typických možností je číst a upravovat kód XML, který je už záměrně zobrazují odsazené.</span><span class="sxs-lookup"><span data-stu-id="9f50c-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="9f50c-108">Možná chcete změnit toto odsazení žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="9f50c-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="9f50c-109">To uděláte v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], zachovat mezer při načtení nebo analyzovat soubor XML a zakázat formátování při serializaci XML.</span><span class="sxs-lookup"><span data-stu-id="9f50c-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="9f50c-110">Prázdné znaky chování metod, které serializovat stromy XML</span><span class="sxs-lookup"><span data-stu-id="9f50c-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="9f50c-111">Následující metody v <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XDocument> třídy serializovat strom XML.</span><span class="sxs-lookup"><span data-stu-id="9f50c-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="9f50c-112">Ve stromu XML do souboru, může serializovat <xref:System.IO.TextReader>, nebo <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9f50c-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="9f50c-113">`ToString` Metoda serializuje na řetězec.</span><span class="sxs-lookup"><span data-stu-id="9f50c-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="9f50c-114">Pokud metoda nevyžaduje <xref:System.Xml.Linq.SaveOptions> jako argument, pak metodu naformátuje (odsazení) serializovaných XML.</span><span class="sxs-lookup"><span data-stu-id="9f50c-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="9f50c-115">V takovém případě se zahodí všechny zanedbatelný mezer ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="9f50c-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="9f50c-116">Pokud metoda <xref:System.Xml.Linq.SaveOptions> jako argument, potom můžete zadat, že metoda není formátu (odsazení) serializovaných XML.</span><span class="sxs-lookup"><span data-stu-id="9f50c-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="9f50c-117">V takovém případě se zachovala všechna mezer ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="9f50c-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f50c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f50c-118">See Also</span></span>  
 [<span data-ttu-id="9f50c-119">Serializace XML stromů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f50c-119">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
