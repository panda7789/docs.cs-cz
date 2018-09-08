---
title: Odebrání obsahu uzlu v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 737766586ee920a87c25dd42896bdfb14ae69d98
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44136768"
---
# <a name="removing-node-content-in-the-dom"></a>Odebrání obsahu uzlu v modelu DOM
Pro typy uzlů, které dědí z <xref:System.Xml.XmlCharacterData>, které jsou <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, a <xref:System.Xml.XmlSignificantWhitespace> typy uzlů, můžete odebrat pomocí znaků <xref:System.Xml.XmlCharacterData.DeleteData%2A> metodu, která odebere rozsah znaky z uzlu. Pokud chcete úplně odebrat obsah, můžete odebrat uzel, který obsahuje obsah. Pokud chcete zachovat uzlu, ale obsah je nesprávná, změňte obsah. Informace o úpravě obsahu uzlu najdete v tématu [úprava uzlů, obsahu a hodnot v dokumentu XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
