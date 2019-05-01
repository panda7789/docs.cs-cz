---
title: Ověření názvu atributu a elementu XML při vytváření nových uzlů
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 008cf14e63b8458feebf26eaf27be516bb79f933
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959039"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="52fb9-102">Ověření názvu atributu a elementu XML při vytváření nových uzlů</span><span class="sxs-lookup"><span data-stu-id="52fb9-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="52fb9-103">XML Document Object Model (DOM) zkontroluje platnost názvů při vytváření nového elementu nebo atributu uzlů.</span><span class="sxs-lookup"><span data-stu-id="52fb9-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="52fb9-104">Pokud název obsahuje neplatné znaky, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="52fb9-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="52fb9-105">Chcete-li zajistit, aby názvy jsou platná a kódovaného správně, budete muset použít **XmlConvert** třídy název kódování a dekódování zpět na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="52fb9-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="52fb9-106">**XmlWriter** má metod, které provádí další prací zajistíte, že se vygeneruje ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="52fb9-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52fb9-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52fb9-107">See also</span></span>

- [<span data-ttu-id="52fb9-108">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="52fb9-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
