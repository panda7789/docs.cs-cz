---
title: Vytváření dokumentů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b76140fb7d79b1e191c0451cd7556963130d224a
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44369014"
---
# <a name="xml-document-creation"></a><span data-ttu-id="491f6-102">Vytváření dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="491f6-102">XML Document Creation</span></span>
<span data-ttu-id="491f6-103">Existují dva způsoby, jak vytvořit dokument XML.</span><span class="sxs-lookup"><span data-stu-id="491f6-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="491f6-104">Jedním ze způsobů je vytvoření **XmlDocument** bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="491f6-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="491f6-105">Druhý způsob je k vytvoření **XmlDocument** a předat jako parametr XmlNameTable.</span><span class="sxs-lookup"><span data-stu-id="491f6-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="491f6-106">Následující příklad ukazuje, jak vytvořit nový, prázdný **XmlDocument** pomocí žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="491f6-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="491f6-107">Po vytvoření dokumentu, můžete je načíst data pomocí dat z řetězce, Streamovat, adresa URL, čtečky textu nebo **XmlReader** odvozené třídy pomocí **načíst** metody.</span><span class="sxs-lookup"><span data-stu-id="491f6-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="491f6-108">Je také jinou metodu načtení, **příkaz LoadXML** metodu, která čte z řetězce XML.</span><span class="sxs-lookup"><span data-stu-id="491f6-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="491f6-109">Další informace o různých **zatížení** metody, naleznete v tématu [čtení dokumentu XML do modelu DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="491f6-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="491f6-110">Existuje třída volá se, **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="491f6-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="491f6-111">Tato třída je tabulka atomizované objekty řetězcových objektů.</span><span class="sxs-lookup"><span data-stu-id="491f6-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="491f6-112">Tato tabulka poskytuje efektivní způsob k analyzátoru XML používat stejný objekt řetězce pro všechny opakované elementu a názvy atributů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="491f6-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="491f6-113">**XmlNameTable** se automaticky vytvoří během dokumentu se vytvoří, jak je znázorněno výše a je načtena s názvy elementu a atributu při načtení dokumentu.</span><span class="sxs-lookup"><span data-stu-id="491f6-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="491f6-114">Pokud už máte dokument s názvem tabulky a tyto názvy může být užitečné v jiném dokumentu, můžete vytvořit nový dokument pomocí **zatížení** metodu, která přebírá **XmlNameTable** jako parametr.</span><span class="sxs-lookup"><span data-stu-id="491f6-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="491f6-115">Když se dokument s touto metodou, využívá existující **XmlNameTable** s atributy a elementy, které už jsou do něho načtené z jiného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="491f6-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="491f6-116">Je možné pro efektivní porovnání názvy prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="491f6-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="491f6-117">Další informace o **XmlNameTable**, naleznete v tématu [porovnání objektů pomocí XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="491f6-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="491f6-118">Odkaz, naleznete v tématu <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="491f6-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491f6-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="491f6-119">See also</span></span>

- [<span data-ttu-id="491f6-120">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="491f6-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
