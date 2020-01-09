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
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>Ověření názvu atributu a elementu XML při vytváření nových uzlů
Model DOM (Document Object Model) XML (DOM) kontroluje platnost názvů při vytváření nových uzlů prvků nebo uzlů atributů. Pokud názvy obsahují neplatné znaky, je vyvolána výjimka. Aby bylo zajištěno, že názvy jsou platné a kódované správně, je nutné použít třídu **XmlConvert** ke kódování názvu a dekódování na úrovni aplikace. Funkce **XmlWriter** má metody, které provedly další práci, aby bylo zajištěno, že kód XML je vygenerován správně.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
