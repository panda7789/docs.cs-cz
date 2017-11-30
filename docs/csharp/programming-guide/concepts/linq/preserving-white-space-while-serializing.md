---
title: "Zachování mezer při Serializing3"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: df0ee9bedd4123ac47c06d1c64f305fcf0b0825a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="d368e-102">Zachování bílé místo při serializaci</span><span class="sxs-lookup"><span data-stu-id="d368e-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="d368e-103">Toto téma popisuje, jak řídit mezer při serializaci strom XML.</span><span class="sxs-lookup"><span data-stu-id="d368e-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="d368e-104">Běžný scénář je číst zobrazují odsazené XML, vytvořte ve stromu v paměti XML bez mezer text uzlů (tedy ne zachování mezer), provádění některých operací na soubor XML a potom uložte soubor XML s odsazení.</span><span class="sxs-lookup"><span data-stu-id="d368e-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="d368e-105">Při serializaci XML s formátování se zachová jenom významné mezer ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="d368e-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="d368e-106">Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d368e-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="d368e-107">Další z typických možností je číst a upravovat kód XML, který je už záměrně zobrazují odsazené.</span><span class="sxs-lookup"><span data-stu-id="d368e-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="d368e-108">Možná chcete změnit toto odsazení žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d368e-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="d368e-109">To uděláte v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], zachovat mezer při načtení nebo analyzovat soubor XML a zakázat formátování při serializaci XML.</span><span class="sxs-lookup"><span data-stu-id="d368e-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="d368e-110">Prázdné znaky chování metod, které serializovat stromy XML</span><span class="sxs-lookup"><span data-stu-id="d368e-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="d368e-111">Následující metody v <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XDocument> třídy serializovat strom XML.</span><span class="sxs-lookup"><span data-stu-id="d368e-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="d368e-112">Ve stromu XML do souboru, může serializovat <xref:System.IO.TextReader>, nebo <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d368e-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d368e-113">`ToString` Metoda serializuje na řetězec.</span><span class="sxs-lookup"><span data-stu-id="d368e-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="d368e-114">Pokud metoda nevyžaduje <xref:System.Xml.Linq.SaveOptions> jako argument, pak metodu naformátuje (odsazení) serializovaných XML.</span><span class="sxs-lookup"><span data-stu-id="d368e-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="d368e-115">V takovém případě se zahodí všechny zanedbatelný mezer ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="d368e-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="d368e-116">Pokud metoda <xref:System.Xml.Linq.SaveOptions> jako argument, potom můžete zadat, že metoda není formátu (odsazení) serializovaných XML.</span><span class="sxs-lookup"><span data-stu-id="d368e-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="d368e-117">V takovém případě se zachovala všechna mezer ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="d368e-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d368e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d368e-118">See Also</span></span>  
 [<span data-ttu-id="d368e-119">Serializace XML stromů (C#)</span><span class="sxs-lookup"><span data-stu-id="d368e-119">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
