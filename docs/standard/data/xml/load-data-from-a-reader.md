---
title: "Načtení dat z čtečka čipových karet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9e9f934d6bff2c9ff3733551bca89b43920f3104
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="load-data-from-a-reader"></a><span data-ttu-id="6d4b8-102">Načtení dat z čtečka čipových karet</span><span class="sxs-lookup"><span data-stu-id="6d4b8-102">Load Data from a Reader</span></span>
<span data-ttu-id="6d4b8-103">Pokud dokument XML je načíst pomocí <xref:System.Xml.XmlDocument.Load%2A> metoda a parametr <xref:System.Xml.XmlReader>, jsou rozdíly v chování, k níž dojde v porovnání s chování načítání dat z jiných formátů.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-103">If an XML document is loaded using the <xref:System.Xml.XmlDocument.Load%2A> method and a parameter of an <xref:System.Xml.XmlReader>, there are differences in the behavior that occurs when compared to the behavior of loading data from the other formats.</span></span> <span data-ttu-id="6d4b8-104">Pokud čtečka je ve stavu počáteční <xref:System.Xml.XmlDocument.Load%2A> využívá celý obsah ze čtečky a vytvoří kódu XML modelu DOM (Document Object) ze všech dat ve čtečce.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-104">If the reader is in its initial state, <xref:System.Xml.XmlDocument.Load%2A> consumes the entire contents from the reader and builds the XML Document Object Model (DOM) from all the data in the reader.</span></span>  
  
 <span data-ttu-id="6d4b8-105">Pokud čtečka je už umístěna v uzlu někde v dokumentu a čtečka se pak předá do <xref:System.Xml.XmlDocument.Load%2A> metody <xref:System.Xml.XmlDocument.Load%2A> se pokusí přečíst na aktuální uzel a všechny uzly na stejné úrovni, až koncovou značku, která zavře aktuální hloubka do paměti.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-105">If the reader is already positioned on a node somewhere in the document, and the reader is then passed to the <xref:System.Xml.XmlDocument.Load%2A> method, <xref:System.Xml.XmlDocument.Load%2A> attempts to read the current node and all of its siblings, up to the end tag that closes the current depth into memory.</span></span> <span data-ttu-id="6d4b8-106">Úspěch pokusu o <xref:System.Xml.XmlDocument.Load%2A> závisí na uzlu, který je čtečka na při pokusu o zatížení jako <xref:System.Xml.XmlDocument.Load%2A> ověřuje, že je ve správném formátu XML ze čtečky.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-106">The success of the attempted <xref:System.Xml.XmlDocument.Load%2A> depends on the node that the reader is on when the load is attempted, as <xref:System.Xml.XmlDocument.Load%2A> verifies that the XML from the reader is well-formed.</span></span> <span data-ttu-id="6d4b8-107">Pokud není ve správném formátu XML <xref:System.Xml.XmlDocument.Load%2A> vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-107">If the XML is not well-formed, the <xref:System.Xml.XmlDocument.Load%2A> throws an exception.</span></span> <span data-ttu-id="6d4b8-108">Například následující sada uzlů obsahovat dva elementy úrovni kořenového adresáře, kód XML není ve správném formátu, a <xref:System.Xml.XmlDocument.Load%2A> vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-108">For example, the following set of nodes contain two root-level elements, the XML is not well-formed, and <xref:System.Xml.XmlDocument.Load%2A> throws an exception.</span></span>  
  
-   <span data-ttu-id="6d4b8-109">Uzel komentáře, za nímž následuje do uzlu Element, za nímž následuje do uzlu Element, za nímž následuje do EndElement uzlu.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-109">Comment node, followed by an Element node, followed by an Element node, followed by an EndElement node.</span></span>  
  
 <span data-ttu-id="6d4b8-110">Následující sada uzlů vytvoří neúplné DOM, protože neexistuje žádný element kořenové úrovni.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-110">The following set of nodes creates an incomplete DOM, because there is no root-level element.</span></span>  
  
-   <span data-ttu-id="6d4b8-111">Uzel komentáře, za nímž následuje uzel komentáře, za nímž následuje do uzlu EndElement ProcessingInstruction uzel.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-111">Comment node followed by a ProcessingInstruction node followed by a Comment node followed by an EndElement node.</span></span>  
  
 <span data-ttu-id="6d4b8-112">To nevyvolá výjimku a načíst data.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-112">This does not throw an exception, and the data is loaded.</span></span> <span data-ttu-id="6d4b8-113">Můžete přidat kořenový element do horní části tyto uzly a vytvořit ve správném formátu XML, který lze uložit bez chyby.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-113">You can add a root element to the top of these nodes and create well-formed XML that can be saved without error.</span></span>  
  
 <span data-ttu-id="6d4b8-114">Pokud čtečka je umístěn na uzel typu list, který je neplatný pro kořenové úrovni dokumentu (například bílé místo nebo atributu uzlu), čtečky pokračovat ve čtení, dokud je umístěný na uzel, který lze použít pro kořenový adresář.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-114">If the reader is positioned on a leaf node that is invalid for the root level of a document (for example, a white space or attribute node), the reader continues to read until it is positioned on a node that can be used for the root.</span></span> <span data-ttu-id="6d4b8-115">Dokument začíná načítání v tomto okamžiku.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-115">The document begins loading at this point.</span></span>  
  
 <span data-ttu-id="6d4b8-116">Ve výchozím nastavení <xref:System.Xml.XmlDocument.Load%2A> neověřuje, zda je platný, pomocí definice typu dokumentu (DTD) nebo ověřování schématu XML.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-116">By default, <xref:System.Xml.XmlDocument.Load%2A> does not verify whether the XML is valid using document type definition (DTD) or schema validation.</span></span> <span data-ttu-id="6d4b8-117">Pouze ověřuje, zda je soubor XML ve správném formátu.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-117">It only verifies whether the XML is well-formed.</span></span> <span data-ttu-id="6d4b8-118">Aby k ověření, je potřeba vytvořit <xref:System.Xml.XmlReader> pomocí <xref:System.Xml.XmlReaderSettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-118">In order for validation to occur, you need to create an <xref:System.Xml.XmlReader> using the <xref:System.Xml.XmlReaderSettings> class.</span></span> <span data-ttu-id="6d4b8-119"><xref:System.Xml.XmlReader> Třídy můžete vynutit pomocí DTD nebo schéma definition language (XSD) schématu ověření.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-119">The <xref:System.Xml.XmlReader> class can enforce validation using a DTD or Schema definition language (XSD) schema.</span></span> <span data-ttu-id="6d4b8-120"><xref:System.Xml.ValidationType> Vlastnost <xref:System.Xml.XmlReaderSettings> Určuje třídu zda <xref:System.Xml.XmlReader> instance vynucuje ověřování.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-120">The <xref:System.Xml.ValidationType> property on the <xref:System.Xml.XmlReaderSettings> class determines whether the <xref:System.Xml.XmlReader> instance enforces validation.</span></span> <span data-ttu-id="6d4b8-121">Další informace o ověření XML data, najdete v části poznámky <xref:System.Xml.XmlReader> stránka s referencemi k.</span><span class="sxs-lookup"><span data-stu-id="6d4b8-121">For more information about validating XML data, see the Remarks section of the <xref:System.Xml.XmlReader> reference page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d4b8-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d4b8-122">See Also</span></span>  
 [<span data-ttu-id="6d4b8-123">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="6d4b8-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
