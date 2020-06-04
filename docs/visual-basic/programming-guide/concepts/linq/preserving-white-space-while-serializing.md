---
title: Zachování mezer při Serializing2
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: e9b73089830bf7e6cb0ea9e469bf667f12c571d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396399"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="9d9ff-102">Zachování prázdných znaků při serializaci</span><span class="sxs-lookup"><span data-stu-id="9d9ff-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="9d9ff-103">Toto téma popisuje, jak ovládat prázdné znaky při serializaci stromu XML.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="9d9ff-104">Běžným scénářem je čtení odsazeného XML, vytvoření stromu XML v paměti bez jakýchkoli textových uzlů s prázdnými znaky (tj. bez zachovávání prázdných znaků), provedení některých operací v XML a následné uložení XML s odsazením.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="9d9ff-105">Při serializaci XML s formátováním je zachováno pouze významné prázdné znaky ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="9d9ff-106">Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9d9ff-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="9d9ff-107">Dalším běžným scénářem je číst a upravovat kód XML, který již byl záměrně odsazen.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="9d9ff-108">Toto odsazení nebudete chtít nijak měnit.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="9d9ff-109">Chcete-li to provést v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , zachováte prázdné místo při načítání nebo analýze XML a při serializaci kódu XML zakážete formátování.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="9d9ff-110">Chování prázdných znaků metod, které serializovat stromy XML</span><span class="sxs-lookup"><span data-stu-id="9d9ff-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="9d9ff-111">Následující metody v <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> třídách a SERIALIZOVAT strom XML.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="9d9ff-112">Strom XML lze serializovat do souboru, <xref:System.IO.TextReader> nebo <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="9d9ff-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="9d9ff-113">`ToString`Metoda je serializována do řetězce.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-113">The `ToString` method serializes to a string.</span></span>  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [<span data-ttu-id="9d9ff-114">XElement. ToString ()</span><span class="sxs-lookup"><span data-stu-id="9d9ff-114">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [<span data-ttu-id="9d9ff-115">XDocument. ToString ()</span><span class="sxs-lookup"><span data-stu-id="9d9ff-115">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 <span data-ttu-id="9d9ff-116">Pokud metoda nepřijímá <xref:System.Xml.Linq.SaveOptions> jako argument, pak metoda naformátuje (odsadí) serializovaný kód XML.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-116">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="9d9ff-117">V tomto případě je zahozeno veškeré nevýznamné prázdné znaky ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-117">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="9d9ff-118">Pokud metoda převezme <xref:System.Xml.Linq.SaveOptions> jako argument, můžete určit, že metoda nebude formátovat (odsazovat) serializovaného XML.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-118">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="9d9ff-119">V tomto případě je zachováno veškeré prázdné znaky ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="9d9ff-119">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d9ff-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d9ff-120">See also</span></span>

- [<span data-ttu-id="9d9ff-121">Serializace stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d9ff-121">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
