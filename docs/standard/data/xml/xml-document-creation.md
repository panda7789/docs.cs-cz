---
title: Vytváření dokumentů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
ms.openlocfilehash: a12555a02b45a964ff7efcbe00e0d2cb8637474a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709982"
---
# <a name="xml-document-creation"></a><span data-ttu-id="eab95-102">Vytváření dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="eab95-102">XML Document Creation</span></span>
<span data-ttu-id="eab95-103">Existují dva způsoby, jak vytvořit dokument XML.</span><span class="sxs-lookup"><span data-stu-id="eab95-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="eab95-104">Jedním ze způsobů je vytvořit **XmlDocument** bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="eab95-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="eab95-105">Druhým způsobem je vytvořit **XmlDocument** a předat mu XmlNameTable jako parametr.</span><span class="sxs-lookup"><span data-stu-id="eab95-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="eab95-106">Následující příklad ukazuje, jak vytvořit novou prázdnou **XmlDocument** pomocí žádného parametru.</span><span class="sxs-lookup"><span data-stu-id="eab95-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="eab95-107">Po vytvoření dokumentu ho můžete načíst s daty z řetězce, datového proudu, adresy URL, čtečky textu nebo odvozené třídy **XmlReader** pomocí metody **Load** .</span><span class="sxs-lookup"><span data-stu-id="eab95-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="eab95-108">Existuje také jiná metoda Load, metoda **LoadXml** , která čte XML z řetězce.</span><span class="sxs-lookup"><span data-stu-id="eab95-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="eab95-109">Další informace o různých metodách **zatížení** naleznete v tématu [čtení dokumentu XML do modelu DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="eab95-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="eab95-110">Existuje třída s názvem **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="eab95-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="eab95-111">Tato třída je tabulka objektů řetězců Atom.</span><span class="sxs-lookup"><span data-stu-id="eab95-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="eab95-112">Tato tabulka poskytuje efektivní způsob, jak analyzátor XML použít stejný objekt řetězce pro všechny opakované názvy elementů a atributů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="eab95-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="eab95-113">**XmlNameTable** se automaticky vytvoří, když se vytvoří dokument, jak je znázorněno výše, a při načtení dokumentu se načte pomocí atributů a názvů elementů.</span><span class="sxs-lookup"><span data-stu-id="eab95-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="eab95-114">Pokud již máte dokument s tabulkou názvů a tyto názvy by byly užitečné v jiném dokumentu, můžete vytvořit nový dokument pomocí metody **Load** , který jako parametr přijímá **XmlNameTable** .</span><span class="sxs-lookup"><span data-stu-id="eab95-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="eab95-115">Když je dokument vytvořen pomocí této metody, používá existující **XmlNameTable** se všemi atributy a prvky, které jsou již do něj načteny z druhého dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eab95-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="eab95-116">Dá se použít pro efektivní porovnávání názvů elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="eab95-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="eab95-117">Další informace o **XmlNameTable**naleznete v tématu [porovnání objektů pomocí XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="eab95-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="eab95-118">Referenční informace najdete v <xref:System.Xml.XmlNameTable>tématu.</span><span class="sxs-lookup"><span data-stu-id="eab95-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab95-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="eab95-119">See also</span></span>

- [<span data-ttu-id="eab95-120">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="eab95-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
