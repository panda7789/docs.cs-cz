---
title: Odebrání obsahu uzlu v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: 02737c5b680321392d93d785b757c58f2b8da9ee
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288651"
---
# <a name="removing-node-content-in-the-dom"></a>Odebrání obsahu uzlu v modelu DOM
U typů uzlů, které dědí z <xref:System.Xml.XmlCharacterData> , což jsou <xref:System.Xml.XmlComment> <xref:System.Xml.XmlText> typy uzlů,, <xref:System.Xml.XmlCDataSection> , <xref:System.Xml.XmlWhitespace> a <xref:System.Xml.XmlSignificantWhitespace> , můžete odebrat znaky pomocí <xref:System.Xml.XmlCharacterData.DeleteData%2A> metody, která odebere rozsah znaků z uzlu. Pokud chcete zcela odebrat obsah, odeberte uzel obsahující obsah. Pokud chcete zachovat uzel, ale obsah není správný, upravte obsah. Informace o úpravách obsahu uzlu naleznete [v tématu Úprava uzlů, obsahu a hodnot v dokumentu XML](modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
