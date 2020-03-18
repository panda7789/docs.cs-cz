---
title: Zachování prázdného místa při serializaci3
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d357d40c13a66a152b3c8bb5f61e3a3374c4055
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484074"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="b29ce-102">Zachování prázdných znaků při serializaci</span><span class="sxs-lookup"><span data-stu-id="b29ce-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="b29ce-103">Toto téma popisuje, jak řídit prázdné místo při serializaci stromu XML.</span><span class="sxs-lookup"><span data-stu-id="b29ce-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="b29ce-104">Běžným scénářem je čtení odsazeného xml, vytvoření stromu XML v paměti bez neložených uzl (tj. nezachování prázdného místa), provedení některých operací v xml a následné uložení XML s odsazením.</span><span class="sxs-lookup"><span data-stu-id="b29ce-104">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="b29ce-105">Při serializaci xml s formátováním se zachová pouze významné prázdné místo ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="b29ce-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="b29ce-106">Toto je výchozí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]chování pro aplikace .</span><span class="sxs-lookup"><span data-stu-id="b29ce-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="b29ce-107">Dalším běžným scénářem je čtení a úprava xml, který již byl záměrně odsazen.</span><span class="sxs-lookup"><span data-stu-id="b29ce-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="b29ce-108">Možná nebudete chtít změnit toto odsazení v žádném případě.</span><span class="sxs-lookup"><span data-stu-id="b29ce-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="b29ce-109">Chcete-li [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]to provést v aplikace , zachovejte prázdné místo při načtení nebo analýzě xml a zakázat formátování při serializaci XML.</span><span class="sxs-lookup"><span data-stu-id="b29ce-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="b29ce-110">Prázdné místo Chování metod, které serializovat stromy XML</span><span class="sxs-lookup"><span data-stu-id="b29ce-110">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="b29ce-111">Následující metody v <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> a třídy serializovat strom XML.</span><span class="sxs-lookup"><span data-stu-id="b29ce-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="b29ce-112">Strom XML můžete serializovat do souboru, stromu <xref:System.IO.TextReader>NEBO . <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="b29ce-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="b29ce-113">Metoda `ToString` serializuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="b29ce-113">The `ToString` method serializes to a string.</span></span>  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [<span data-ttu-id="b29ce-114">XElement.ToString()</span><span class="sxs-lookup"><span data-stu-id="b29ce-114">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [<span data-ttu-id="b29ce-115">XDocument.ToString()</span><span class="sxs-lookup"><span data-stu-id="b29ce-115">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 <span data-ttu-id="b29ce-116">Pokud metoda nebere <xref:System.Xml.Linq.SaveOptions> jako argument, pak metoda bude formátovat (odsazení) serializované XML.</span><span class="sxs-lookup"><span data-stu-id="b29ce-116">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="b29ce-117">V tomto případě jsou zahozeny všechny nevýznamné prázdné místo ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="b29ce-117">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="b29ce-118">Pokud metoda trvá <xref:System.Xml.Linq.SaveOptions> jako argument, můžete určit, že metoda není formátovat (odsazení) serializovanéXML.</span><span class="sxs-lookup"><span data-stu-id="b29ce-118">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="b29ce-119">V tomto případě je zachováno všechny prázdné místo ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="b29ce-119">In this case, all white space in the XML tree is preserved.</span></span>  
