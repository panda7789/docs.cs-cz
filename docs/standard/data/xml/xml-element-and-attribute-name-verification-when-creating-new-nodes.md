---
title: Ověření názvu atributu a elementu XML při vytváření nových uzlů
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 1da893261b35c6b57c4f08eb53b7701ec1d81fae
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289847"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>Ověření názvu atributu a elementu XML při vytváření nových uzlů
Model DOM (Document Object Model) XML (DOM) kontroluje platnost názvů při vytváření nových uzlů prvků nebo uzlů atributů. Pokud názvy obsahují neplatné znaky, je vyvolána výjimka. Aby bylo zajištěno, že názvy jsou platné a kódované správně, je nutné použít třídu **XmlConvert** ke kódování názvu a dekódování na úrovni aplikace. Funkce **XmlWriter** má metody, které provedly další práci, aby bylo zajištěno, že kód XML je vygenerován správně.  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
