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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 36b9761cefb1dba47c88d053773c89e4312dee9d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="77c71-102">XML Element a ověření názvu atributu při vytváření nových uzlů</span><span class="sxs-lookup"><span data-stu-id="77c71-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="77c71-103">XML modelu DOM (Document Object) zkontroluje platnost názvů při vytváření nových uzlů element nebo atribut uzlů.</span><span class="sxs-lookup"><span data-stu-id="77c71-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="77c71-104">Pokud se názvy obsahují neplatné znaky, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="77c71-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="77c71-105">Chcete, aby názvy jsou platné a kódovaného správně, budete muset použít **XmlConvert** třídy název kódování a dekódování ji zpět na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="77c71-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="77c71-106">**XmlWriter** obsahuje metody, které další práci, aby se generuje ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="77c71-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c71-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="77c71-107">See Also</span></span>  
 [<span data-ttu-id="77c71-108">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="77c71-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
