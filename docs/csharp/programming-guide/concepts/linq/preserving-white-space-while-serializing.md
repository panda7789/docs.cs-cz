---
title: Zachování mezer při Serializing3
description: Naučte se ovládat prázdné znaky při serializaci stromu XML pomocí metod v třídách XElement a XDocument.
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 01e68671e2fde1a2b5b1d0bc429841077ba0205f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303410"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="7ad8d-103">Zachování prázdných znaků při serializaci</span><span class="sxs-lookup"><span data-stu-id="7ad8d-103">Preserving White Space While Serializing</span></span>
<span data-ttu-id="7ad8d-104">Toto téma popisuje, jak ovládat prázdné znaky při serializaci stromu XML.</span><span class="sxs-lookup"><span data-stu-id="7ad8d-104">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="7ad8d-105">Běžným scénářem je čtení odsazeného XML, vytvoření stromu XML ve formátu paměti bez prázdných textových uzlů (tj. Neuchování prázdných znaků), provedení některých operací v XML a následné uložení XML s odsazením.</span><span class="sxs-lookup"><span data-stu-id="7ad8d-105">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="7ad8d-106">Při serializaci XML s formátováním je zachováno pouze významné prázdné znaky ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="7ad8d-106">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="7ad8d-107">Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7ad8d-107">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="7ad8d-108">Dalším běžným scénářem je číst a upravovat kód XML, který již byl záměrně odsazen.</span><span class="sxs-lookup"><span data-stu-id="7ad8d-108">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="7ad8d-109">Toto odsazení nebudete chtít nijak měnit.</span><span class="sxs-lookup"><span data-stu-id="7ad8d-109">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="7ad8d-110">Chcete-li to provést v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , zachováte prázdné místo při načítání nebo analýze XML a při serializaci kódu XML zakážete formátování.</span><span class="sxs-lookup"><span data-stu-id="7ad8d-110">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="7ad8d-111">Chování metod, které serializovat stromy XML, v prázdném prostoru</span><span class="sxs-lookup"><span data-stu-id="7ad8d-111">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="7ad8d-112">Následující metody v <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> třídách a SERIALIZOVAT strom XML.</span><span class="sxs-lookup"><span data-stu-id="7ad8d-112">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="7ad8d-113">Strom XML lze serializovat do souboru, <xref:System.IO.TextReader> nebo <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="7ad8d-113">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="7ad8d-114">`ToString`Metoda je serializována do řetězce.</span><span class="sxs-lookup"><span data-stu-id="7ad8d-114">The `ToString` method serializes to a string.</span></span>  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [<span data-ttu-id="7ad8d-115">XElement. ToString ()</span><span class="sxs-lookup"><span data-stu-id="7ad8d-115">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [<span data-ttu-id="7ad8d-116">XDocument. ToString ()</span><span class="sxs-lookup"><span data-stu-id="7ad8d-116">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 <span data-ttu-id="7ad8d-117">Pokud metoda nepřijímá <xref:System.Xml.Linq.SaveOptions> jako argument, pak metoda naformátuje (odsadí) serializovaný kód XML.</span><span class="sxs-lookup"><span data-stu-id="7ad8d-117">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="7ad8d-118">V tomto případě je zahozeno veškeré nevýznamné prázdné znaky ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="7ad8d-118">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="7ad8d-119">Pokud metoda převezme <xref:System.Xml.Linq.SaveOptions> jako argument, můžete určit, že metoda nebude formátovat (odsazovat) serializovaného XML.</span><span class="sxs-lookup"><span data-stu-id="7ad8d-119">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="7ad8d-120">V tomto případě je zachováno veškeré prázdné znaky ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="7ad8d-120">In this case, all white space in the XML tree is preserved.</span></span>  
