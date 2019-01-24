---
title: Zachování prázdných znaků při Serializing2
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: cbfa9a39c52a40831627429f7ffc9971e0074a50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602036"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="83923-102">Zachování prázdných znaků při serializaci</span><span class="sxs-lookup"><span data-stu-id="83923-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="83923-103">Toto téma popisuje, jak řídit prázdných znaků při serializaci stromu XML.</span><span class="sxs-lookup"><span data-stu-id="83923-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="83923-104">Běžný scénář, kdy je pro čtení odsazený XML, vytvoření stromu XML v paměti bez ostatní uzly text prázdné znaky (tedy ne zachování prázdné znaky), provádění některých operací na XML a pak uložte soubor XML s odsazením.</span><span class="sxs-lookup"><span data-stu-id="83923-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="83923-105">Při serializaci XML s formátováním je zachována pouze významný prázdný znak ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="83923-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="83923-106">Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83923-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="83923-107">Další z typických možností je číst a upravovat kód XML, který již byl záměrně odsazeny.</span><span class="sxs-lookup"><span data-stu-id="83923-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="83923-108">Nebudete chtít změnit tento odsazení žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="83923-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="83923-109">Chcete-li to provést v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], zachovat mezer při načtení nebo analyzovat kód XML a zakázat formátování při serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="83923-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="83923-110">Chování mezer metod, které serializace stromů XML</span><span class="sxs-lookup"><span data-stu-id="83923-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="83923-111">Následující metody u <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XDocument> třídy serializaci stromu XML.</span><span class="sxs-lookup"><span data-stu-id="83923-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="83923-112">Může serializovat stromu XML do souboru <xref:System.IO.TextReader>, nebo <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="83923-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="83923-113">`ToString` Metoda provede serializaci do řetězce.</span><span class="sxs-lookup"><span data-stu-id="83923-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="83923-114">Pokud metoda nepřijímá <xref:System.Xml.Linq.SaveOptions> jako argument, pak metoda naformátuje (odsazení) serializovaném kódu XML.</span><span class="sxs-lookup"><span data-stu-id="83923-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="83923-115">V takovém případě se zahodí všechny neplatné prázdné znaky ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="83923-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="83923-116">Pokud trvá, než metoda <xref:System.Xml.Linq.SaveOptions> jako argument, potom můžete zadat, že metoda není formátování (odsazení) serializovaném kódu XML.</span><span class="sxs-lookup"><span data-stu-id="83923-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="83923-117">V takovém případě se zachovají všechny prázdné znaky ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="83923-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83923-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83923-118">See also</span></span>
- [<span data-ttu-id="83923-119">Serializace stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83923-119">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
