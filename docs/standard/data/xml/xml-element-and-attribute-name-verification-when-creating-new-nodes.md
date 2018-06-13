---
title: XML Element a ověření názvu atributu při vytváření nových uzlů
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de11c190310dec90bd23d044f77d0c38e3a34fcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568846"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>XML Element a ověření názvu atributu při vytváření nových uzlů
XML modelu DOM (Document Object) zkontroluje platnost názvů při vytváření nových uzlů element nebo atribut uzlů. Pokud se názvy obsahují neplatné znaky, je vyvolána výjimka. Chcete, aby názvy jsou platné a kódovaného správně, budete muset použít **XmlConvert** třídy název kódování a dekódování ji zpět na úrovni aplikace. **XmlWriter** obsahuje metody, které další práci, aby se generuje ve správném formátu XML.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
