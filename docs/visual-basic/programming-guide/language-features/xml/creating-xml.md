---
title: "Vytvoření XML v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 95ab82f2a8ae11b04e3887d5a179931c47346155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="df098-102">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="df098-102">Creating XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="df098-103">umožňuje používat *XML – literály* přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="df098-103"> enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="df098-104">Představuje literálu syntaxe XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty a je podobná syntaxe XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="df098-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="df098-105">Díky tomu je snazší vytvářet elementů XML, dokumenty a fragmenty prostřednictvím kódu programu, protože váš kód má stejné struktuře jako poslední XML.</span><span class="sxs-lookup"><span data-stu-id="df098-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df098-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="df098-106">In This Section</span></span>  
  
|<span data-ttu-id="df098-107">Termín</span><span class="sxs-lookup"><span data-stu-id="df098-107">Term</span></span>|<span data-ttu-id="df098-108">Definice</span><span class="sxs-lookup"><span data-stu-id="df098-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="df098-109">Přehled literálů XML</span><span class="sxs-lookup"><span data-stu-id="df098-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="df098-110">Úvod do literály XML a jak se vztahují k [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="df098-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="df098-111">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="df098-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="df098-112">Popisuje, jak používat vložené výrazy v XML – literály.</span><span class="sxs-lookup"><span data-stu-id="df098-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="df098-113">Postupy: vytváření literálů XML</span><span class="sxs-lookup"><span data-stu-id="df098-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="df098-114">Popisuje, jak vytvořit XML element v kódu pomocí literál XML.</span><span class="sxs-lookup"><span data-stu-id="df098-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="df098-115">Prázdné znaky v literálech XML</span><span class="sxs-lookup"><span data-stu-id="df098-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="df098-116">Popisuje, jak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zpracovává prázdné znaky v literálech XML.</span><span class="sxs-lookup"><span data-stu-id="df098-116">Describes how [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="df098-117">Literály XML a XML 1.0 specifikace</span><span class="sxs-lookup"><span data-stu-id="df098-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="df098-118">Popisuje, jak literálu syntaxe XML [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] má vztah k specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="df098-118">Describes how the XML literal syntax in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="df098-119">Postupy: vložení výrazů do literálů XML</span><span class="sxs-lookup"><span data-stu-id="df098-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="df098-120">Popisuje, jak používat vložené výrazy v XML – literály k vytváření obsahu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="df098-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="df098-121">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="df098-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="df098-122">Popisuje pravidla pro vytváření názvů XML elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="df098-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df098-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="df098-123">See Also</span></span>  
 [<span data-ttu-id="df098-124">XML</span><span class="sxs-lookup"><span data-stu-id="df098-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
