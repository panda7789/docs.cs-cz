---
title: Serializace stromů XML (C#)
ms.date: 07/20/2015
ms.assetid: b3937e54-4ce9-4236-ac96-14e7972aa594
ms.openlocfilehash: a1c39c4c85cbd01fa7c3f3f99f2dfae49e3721d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583441"
---
# <a name="serializing-xml-trees-c"></a><span data-ttu-id="94a8a-102">Serializace stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="94a8a-102">Serializing XML Trees (C#)</span></span>
<span data-ttu-id="94a8a-103">Serializaci stromu XML znamená, že generování XML ze stromu XML.</span><span class="sxs-lookup"><span data-stu-id="94a8a-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="94a8a-104">Může serializovat do souboru, do konkrétní implementaci <xref:System.IO.TextWriter> třídy, nebo na konkrétní implementaci <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="94a8a-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="94a8a-105">Můžete ovládat různé aspekty serializace.</span><span class="sxs-lookup"><span data-stu-id="94a8a-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="94a8a-106">Můžete například řídit, jestli se má odsadit serializovaná XML a jestli se mají zapsat deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="94a8a-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94a8a-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="94a8a-107">In This Section</span></span>  
  
|<span data-ttu-id="94a8a-108">Téma</span><span class="sxs-lookup"><span data-stu-id="94a8a-108">Topic</span></span>|<span data-ttu-id="94a8a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="94a8a-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="94a8a-110">Zachování prázdných znaků při serializaci</span><span class="sxs-lookup"><span data-stu-id="94a8a-110">Preserving White Space While Serializing</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="94a8a-111">Popisuje, jak řídit chování mezer při serializace stromů XML.</span><span class="sxs-lookup"><span data-stu-id="94a8a-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="94a8a-112">Serializace pomocí deklarace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="94a8a-112">Serializing with an XML Declaration (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="94a8a-113">Popisuje, jak k serializaci stromu XML, který obsahuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="94a8a-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="94a8a-114">Serializace do tříd File, TextWriter a XmlWriter</span><span class="sxs-lookup"><span data-stu-id="94a8a-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="94a8a-115">Popisuje, jak k serializaci do dokumentu <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="94a8a-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="94a8a-116">Serializace do třídy XmlReader (vyvolání XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="94a8a-116">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="94a8a-117">Popisuje, jak vytvořit <xref:System.Xml.XmlReader> , která umožňuje jiný modul číst obsah stromu XML.</span><span class="sxs-lookup"><span data-stu-id="94a8a-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94a8a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94a8a-118">See also</span></span>

- [<span data-ttu-id="94a8a-119">Průvodce programováním (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="94a8a-119">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
