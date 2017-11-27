---
title: "Serializace XML stromů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c340695-a726-4030-85be-6975d8a149cf
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 924c4dace92ed306852cd1d7d2fead8588d03dc4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-xml-trees-visual-basic"></a><span data-ttu-id="87f05-102">Serializace XML stromů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87f05-102">Serializing XML Trees (Visual Basic)</span></span>
<span data-ttu-id="87f05-103">Serializace ve stromu XML znamená generování XML ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="87f05-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="87f05-104">Můžete serializovat do souboru, do konkrétní implementaci <xref:System.IO.TextWriter> třídy, nebo na konkrétní implementaci <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="87f05-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="87f05-105">Můžete ovládat různé aspekty serializace.</span><span class="sxs-lookup"><span data-stu-id="87f05-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="87f05-106">Například můžete řídit, jestli se má odsadit serializovaných XML a jestli k zápisu deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="87f05-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="87f05-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="87f05-107">In This Section</span></span>  
  
|<span data-ttu-id="87f05-108">Téma</span><span class="sxs-lookup"><span data-stu-id="87f05-108">Topic</span></span>|<span data-ttu-id="87f05-109">Popis</span><span class="sxs-lookup"><span data-stu-id="87f05-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="87f05-110">Zachování bílé místo při serializaci</span><span class="sxs-lookup"><span data-stu-id="87f05-110">Preserving White Space While Serializing</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="87f05-111">Popisuje, jak můžete řídit chování mezer při serializaci XML stromy.</span><span class="sxs-lookup"><span data-stu-id="87f05-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="87f05-112">Serializace s deklarace XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87f05-112">Serializing with an XML Declaration (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="87f05-113">Popisuje, jak k serializaci XML stromové struktury, která obsahuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="87f05-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="87f05-114">Serializace k souborům, TextWriters a XmlWriters</span><span class="sxs-lookup"><span data-stu-id="87f05-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="87f05-115">Popisuje, jak serializovat dokument <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="87f05-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="87f05-116">Serializace pro objekt XmlReader (volajícím XSLT) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87f05-116">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="87f05-117">Popisuje postup vytvoření <xref:System.Xml.XmlReader> umožňující jiný modul načíst obsah XML stromu.</span><span class="sxs-lookup"><span data-stu-id="87f05-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87f05-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="87f05-118">See Also</span></span>  
 [<span data-ttu-id="87f05-119">Průvodce programováním (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87f05-119">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
