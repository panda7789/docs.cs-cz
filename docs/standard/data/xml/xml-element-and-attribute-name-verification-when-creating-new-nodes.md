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
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>XML Element a ověření názvu atributu při vytváření nových uzlů
XML modelu DOM (Document Object) zkontroluje platnost názvů při vytváření nových uzlů element nebo atribut uzlů. Pokud se názvy obsahují neplatné znaky, je vyvolána výjimka. Chcete, aby názvy jsou platné a kódovaného správně, budete muset použít **XmlConvert** třídy název kódování a dekódování ji zpět na úrovni aplikace. **XmlWriter** obsahuje metody, které další práci, aby se generuje ve správném formátu XML.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
