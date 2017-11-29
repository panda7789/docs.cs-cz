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
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>XML Element a ověření názvu atributu při vytváření nových uzlů
XML modelu DOM (Document Object) zkontroluje platnost názvů při vytváření nových uzlů element nebo atribut uzlů. Pokud se názvy obsahují neplatné znaky, je vyvolána výjimka. Chcete, aby názvy jsou platné a kódovaného správně, budete muset použít **XmlConvert** třídy název kódování a dekódování ji zpět na úrovni aplikace. **XmlWriter** obsahuje metody, které další práci, aby se generuje ve správném formátu XML.  
  
## <a name="see-also"></a>Viz také  
 [XML Document Object Model (DOM).](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
