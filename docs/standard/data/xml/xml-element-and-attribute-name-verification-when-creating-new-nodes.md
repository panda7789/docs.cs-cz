---
title: "XML Element a ověření názvu atributu při vytváření nových uzlů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c041d5d2830222f3fae09a39f1ea10eb08772388
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="5c46c-102">XML Element a ověření názvu atributu při vytváření nových uzlů</span><span class="sxs-lookup"><span data-stu-id="5c46c-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="5c46c-103">XML modelu DOM (Document Object) zkontroluje platnost názvů při vytváření nových uzlů element nebo atribut uzlů.</span><span class="sxs-lookup"><span data-stu-id="5c46c-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="5c46c-104">Pokud se názvy obsahují neplatné znaky, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="5c46c-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="5c46c-105">Chcete, aby názvy jsou platné a kódovaného správně, budete muset použít **XmlConvert** třídy název kódování a dekódování ji zpět na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c46c-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="5c46c-106">**XmlWriter** obsahuje metody, které další práci, aby se generuje ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="5c46c-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c46c-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c46c-107">See Also</span></span>  
 [<span data-ttu-id="5c46c-108">XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="5c46c-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
