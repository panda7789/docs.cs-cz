---
title: Zachování prázdných znaků při Serializing3
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 7fd0a38d2a9ed8c4712b8e9a03a24a23b408f38a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185214"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="a5b40-102">Zachování prázdných znaků při serializaci</span><span class="sxs-lookup"><span data-stu-id="a5b40-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="a5b40-103">Toto téma popisuje, jak řídit prázdných znaků při serializaci stromu XML.</span><span class="sxs-lookup"><span data-stu-id="a5b40-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="a5b40-104">Běžný scénář, kdy je pro čtení odsazený XML, vytvoření stromu XML v paměti bez ostatní uzly text prázdné místo (tedy ne zachování prázdné znaky), provádění některých operací na XML a pak uložte soubor XML s odsazením.</span><span class="sxs-lookup"><span data-stu-id="a5b40-104">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="a5b40-105">Při serializaci XML s formátováním je zachována pouze významný prázdný znak ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="a5b40-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="a5b40-106">Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5b40-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="a5b40-107">Další z typických možností je číst a upravovat kód XML, který již byl záměrně odsazeny.</span><span class="sxs-lookup"><span data-stu-id="a5b40-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="a5b40-108">Nebudete chtít změnit tento odsazení žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="a5b40-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="a5b40-109">Chcete-li to provést v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], zachovat mezer při načtení nebo analyzovat kód XML a zakázat formátování při serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="a5b40-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="a5b40-110">Prázdné místo chování metody, které serializace stromů XML</span><span class="sxs-lookup"><span data-stu-id="a5b40-110">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="a5b40-111">Následující metody u <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XDocument> třídy serializaci stromu XML.</span><span class="sxs-lookup"><span data-stu-id="a5b40-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="a5b40-112">Může serializovat stromu XML do souboru <xref:System.IO.TextReader>, nebo <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="a5b40-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="a5b40-113">`ToString` Metoda provede serializaci do řetězce.</span><span class="sxs-lookup"><span data-stu-id="a5b40-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="a5b40-114">Pokud metoda nepřijímá <xref:System.Xml.Linq.SaveOptions> jako argument, pak metoda naformátuje (odsazení) serializovaném kódu XML.</span><span class="sxs-lookup"><span data-stu-id="a5b40-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="a5b40-115">V takovém případě se zahodí všechny neplatné prázdné znaky ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="a5b40-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="a5b40-116">Pokud trvá, než metoda <xref:System.Xml.Linq.SaveOptions> jako argument, potom můžete zadat, že metoda není formátování (odsazení) serializovaném kódu XML.</span><span class="sxs-lookup"><span data-stu-id="a5b40-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="a5b40-117">V takovém případě se zachovají všechny prázdné znaky ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="a5b40-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b40-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5b40-118">See Also</span></span>

- [<span data-ttu-id="a5b40-119">Serializace stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a5b40-119">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
