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
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>Ověření názvu atributu a elementu XML při vytváření nových uzlů
XML Document Object Model (DOM) zkontroluje platnost názvů při vytváření nového elementu nebo atributu uzlů. Pokud název obsahuje neplatné znaky, je vyvolána výjimka. Chcete-li zajistit, aby názvy jsou platná a kódovaného správně, budete muset použít **XmlConvert** třídy název kódování a dekódování zpět na úrovni aplikace. **XmlWriter** má metod, které provádí další prací zajistíte, že se vygeneruje ve správném formátu XML.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
