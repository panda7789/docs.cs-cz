---
title: Odebrání obsahu uzlu v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: f5086bdea8ff1f0ee5329f347223ebb4a6bd71da
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710333"
---
# <a name="removing-node-content-in-the-dom"></a>Odebrání obsahu uzlu v modelu DOM
U typů uzlů, které dědí z <xref:System.Xml.XmlCharacterData>typy uzlů <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>a <xref:System.Xml.XmlSignificantWhitespace> můžete odebrat znaky pomocí metody <xref:System.Xml.XmlCharacterData.DeleteData%2A>, která odebere rozsah znaků z uzlu. Pokud chcete zcela odebrat obsah, odeberte uzel obsahující obsah. Pokud chcete zachovat uzel, ale obsah není správný, upravte obsah. Informace o úpravách obsahu uzlu naleznete [v tématu Úprava uzlů, obsahu a hodnot v dokumentu XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
