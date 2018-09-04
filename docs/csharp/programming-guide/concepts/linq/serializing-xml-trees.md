---
title: Serializace stromů XML (C#)
ms.date: 07/20/2015
ms.assetid: b3937e54-4ce9-4236-ac96-14e7972aa594
ms.openlocfilehash: f9bcf049eb6cfe129971923657f5d70a833209cc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500477"
---
# <a name="serializing-xml-trees-c"></a><span data-ttu-id="64d27-102">Serializace stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="64d27-102">Serializing XML Trees (C#)</span></span>
<span data-ttu-id="64d27-103">Serializaci stromu XML znamená, že generování XML ze stromu XML.</span><span class="sxs-lookup"><span data-stu-id="64d27-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="64d27-104">Může serializovat do souboru, do konkrétní implementaci <xref:System.IO.TextWriter> třídy, nebo na konkrétní implementaci <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="64d27-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="64d27-105">Můžete ovládat různé aspekty serializace.</span><span class="sxs-lookup"><span data-stu-id="64d27-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="64d27-106">Můžete například řídit, jestli se má odsadit serializovaná XML a jestli se mají zapsat deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="64d27-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64d27-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="64d27-107">In This Section</span></span>  
  
|<span data-ttu-id="64d27-108">Téma</span><span class="sxs-lookup"><span data-stu-id="64d27-108">Topic</span></span>|<span data-ttu-id="64d27-109">Popis</span><span class="sxs-lookup"><span data-stu-id="64d27-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="64d27-110">Zachování prázdných znaků při serializaci</span><span class="sxs-lookup"><span data-stu-id="64d27-110">Preserving White Space While Serializing</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="64d27-111">Popisuje, jak řídit chování mezer při serializace stromů XML.</span><span class="sxs-lookup"><span data-stu-id="64d27-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="64d27-112">Serializace pomocí deklarace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="64d27-112">Serializing with an XML Declaration (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="64d27-113">Popisuje, jak k serializaci stromu XML, který obsahuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="64d27-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="64d27-114">Serializace do tříd File, TextWriter a XmlWriter</span><span class="sxs-lookup"><span data-stu-id="64d27-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="64d27-115">Popisuje, jak k serializaci do dokumentu <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="64d27-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="64d27-116">Serializace do třídy XmlReader (vyvolání XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="64d27-116">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="64d27-117">Popisuje, jak vytvořit <xref:System.Xml.XmlReader> , která umožňuje jiný modul číst obsah stromu XML.</span><span class="sxs-lookup"><span data-stu-id="64d27-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64d27-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="64d27-118">See Also</span></span>

- [<span data-ttu-id="64d27-119">Průvodce programováním (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="64d27-119">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
