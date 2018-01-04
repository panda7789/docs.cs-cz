---
title: "Objektový Model schématu XML (SOM)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b11fc10128807dfbd0082bbc1884068c5cde7d32
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="a37f1-102">Objektový Model schématu XML (SOM)</span><span class="sxs-lookup"><span data-stu-id="a37f1-102">XML Schema Object Model (SOM)</span></span>
<span data-ttu-id="a37f1-103">Schéma XML je výkonná a komplexní nástroj pro vytváření a ověřování struktury kompatibilní dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="a37f1-103">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="a37f1-104">Podobně jako u dat modelování v relační databázi, schéma poskytuje způsob, jak definovat strukturu dokumentů XML zadáním prvky, které lze použít v dokumenty, jakož i strukturu a typy, které tyto prvky musí splňovat, aby se pro zadaná platná t konkrétní schématu.</span><span class="sxs-lookup"><span data-stu-id="a37f1-104">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="a37f1-105">Model objektu schématu (SOM) poskytuje sadu tříd v <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů, který umožní číst ze souboru schématu nebo vytváření prostřednictvím kódu programu schéma v paměti.</span><span class="sxs-lookup"><span data-stu-id="a37f1-105">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="a37f1-106">Schéma lze poté procházet a úpravám kompilovat, ověřit nebo zapisují do souboru.</span><span class="sxs-lookup"><span data-stu-id="a37f1-106">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a37f1-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a37f1-107">In This Section</span></span>  
 [<span data-ttu-id="a37f1-108">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="a37f1-108">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 <span data-ttu-id="a37f1-109">Popisuje schéma modelu objektu (SOM) a funkce a třídy, které poskytuje.</span><span class="sxs-lookup"><span data-stu-id="a37f1-109">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="a37f1-110">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="a37f1-110">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="a37f1-111">Popisuje, jak číst a zapisovat schémat XML ze souborů nebo jiné zdroje.</span><span class="sxs-lookup"><span data-stu-id="a37f1-111">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="a37f1-112">Sestavování schémat XML</span><span class="sxs-lookup"><span data-stu-id="a37f1-112">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 <span data-ttu-id="a37f1-113">Popisuje způsob použití třídy v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů k vytvoření XML schémata v paměti.</span><span class="sxs-lookup"><span data-stu-id="a37f1-113">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="a37f1-114">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="a37f1-114">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 <span data-ttu-id="a37f1-115">Popisuje, jak procházet schéma XML pro přístup k prvky, atributy a typy, které jsou uložené v SOM.</span><span class="sxs-lookup"><span data-stu-id="a37f1-115">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="a37f1-116">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="a37f1-116">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 <span data-ttu-id="a37f1-117">Popisuje, jak upravit schématu XML.</span><span class="sxs-lookup"><span data-stu-id="a37f1-117">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="a37f1-118">Zahrnutí nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="a37f1-118">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 <span data-ttu-id="a37f1-119">Popisuje, jak chcete zahrnout nebo import dalších schémat XML doplníte strukturu schématu, která zahrnuje nebo importuje je.</span><span class="sxs-lookup"><span data-stu-id="a37f1-119">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>
