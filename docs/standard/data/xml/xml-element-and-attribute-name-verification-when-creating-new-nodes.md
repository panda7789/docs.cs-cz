---
title: Ověření názvu atributu a elementu XML při vytváření nových uzlů
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 7c99ffa9d139d94d26c562cb1668f1b855bed32d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709943"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="5e4be-102">Ověření názvu atributu a elementu XML při vytváření nových uzlů</span><span class="sxs-lookup"><span data-stu-id="5e4be-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="5e4be-103">Model DOM (Document Object Model) XML (DOM) kontroluje platnost názvů při vytváření nových uzlů prvků nebo uzlů atributů.</span><span class="sxs-lookup"><span data-stu-id="5e4be-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="5e4be-104">Pokud názvy obsahují neplatné znaky, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="5e4be-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="5e4be-105">Aby bylo zajištěno, že názvy jsou platné a kódované správně, je nutné použít třídu **XmlConvert** ke kódování názvu a dekódování na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="5e4be-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="5e4be-106">Funkce **XmlWriter** má metody, které provedly další práci, aby bylo zajištěno, že kód XML je vygenerován správně.</span><span class="sxs-lookup"><span data-stu-id="5e4be-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e4be-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e4be-107">See also</span></span>

- [<span data-ttu-id="5e4be-108">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="5e4be-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
