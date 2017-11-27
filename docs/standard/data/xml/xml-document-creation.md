---
title: "Vytváření dokumentů XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a0806e34cfbf7c8e0b5ba995ca4876b8d10405e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-creation"></a><span data-ttu-id="0611d-102">Vytváření dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="0611d-102">XML Document Creation</span></span>
<span data-ttu-id="0611d-103">Existují dva způsoby, jak vytvořit dokument XML.</span><span class="sxs-lookup"><span data-stu-id="0611d-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="0611d-104">Jedním ze způsobů je vytvoření **třídou XMLDocument nastavenou na** bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="0611d-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="0611d-105">Druhý způsob je vytvoření **třídou XMLDocument nastavenou na** a předejte ji XmlNameTable jako parametr.</span><span class="sxs-lookup"><span data-stu-id="0611d-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="0611d-106">Následující příklad ukazuje, jak vytvořit nový, prázdný **třídou XMLDocument nastavenou na** pomocí žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="0611d-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="0611d-107">Po vytvoření dokumentu, můžete ho zatížení s daty z řetězce, stream, adresa URL, čtečku textu nebo **XmlReader** odvozené třídy pomocí **načíst** metoda.</span><span class="sxs-lookup"><span data-stu-id="0611d-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="0611d-108">Je také jinou metodu načtení, **příkaz LoadXML** metodu, která čte XML z řetězce.</span><span class="sxs-lookup"><span data-stu-id="0611d-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="0611d-109">Další informace o různých **zatížení** metody, najdete v části [čtení dokumentu XML do modelu DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="0611d-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="0611d-110">Existuje třída volá **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="0611d-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="0611d-111">Tato třída je tabulka objektů atomized řetězec.</span><span class="sxs-lookup"><span data-stu-id="0611d-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="0611d-112">Tato tabulka obsahuje efektivní prostředky pro analyzátor XML, který chcete použít stejný objekt řetězce pro všechny opakované elementu a názvy atributů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0611d-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="0611d-113">**XmlNameTable** se automaticky vytvoří při dokumentu je vytvořen jako v příkladu nahoře a je načtena s názvy elementu a atributu při načtení dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0611d-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="0611d-114">Pokud již máte dokument s názvem tabulky a tyto názvy by být užitečné do jiného dokumentu, můžete vytvořit nový dokument pomocí **zatížení** metody, která použije **XmlNameTable** jako parametr.</span><span class="sxs-lookup"><span data-stu-id="0611d-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="0611d-115">Pomocí této metody vytvoření dokumentu má použije existující **XmlNameTable** s atributy a elementy, které do ní již načten z jiného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0611d-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="0611d-116">Slouží pro efektivní porovnávání názvy elementu a atributu.</span><span class="sxs-lookup"><span data-stu-id="0611d-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="0611d-117">Další informace o **XmlNameTable**, najdete v části [objekt porovnání pomocí XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="0611d-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="0611d-118">Odkaz, najdete v části <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="0611d-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0611d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0611d-119">See Also</span></span>  
 [<span data-ttu-id="0611d-120">XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="0611d-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
