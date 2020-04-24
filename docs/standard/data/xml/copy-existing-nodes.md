---
title: Kopírování existujících uzlů
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: fb9ccd7b16d00355ba87bb32f5447906feeecd94
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711061"
---
# <a name="copy-existing-nodes"></a>Kopírování existujících uzlů
Existuje mnoho metod a vlastností v souboru XML model DOM (Document Object Model) (DOM), které můžete použít k výběru uzlu, například **SelectSingleNode**, **ChildNodes [int i]**, **atributů [int i]**. Po výběru uzlu jej můžete vložit do stromu pomocí jedné z metod vložení, které fungují pro daný typ uzlu. Jediným omezením pro vložení uzlu do stromu je, že dokument musí být po vložení uzlu stále správně vytvořen. Když je existující uzel vložen do stromu modelu DOM, je odebrán z původní pozice a přidán na jeho cílovou pozici.  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
