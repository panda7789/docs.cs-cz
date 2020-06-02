---
title: Kopírování existujících uzlů
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 392490d04ff713529d501e199ac2496ff37de1a0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289210"
---
# <a name="copy-existing-nodes"></a>Kopírování existujících uzlů
Existuje mnoho metod a vlastností v souboru XML model DOM (Document Object Model) (DOM), které můžete použít k výběru uzlu, například **SelectSingleNode**, **ChildNodes [int i]**, **atributů [int i]**. Po výběru uzlu jej můžete vložit do stromu pomocí jedné z metod vložení, které fungují pro daný typ uzlu. Jediným omezením pro vložení uzlu do stromu je, že dokument musí být po vložení uzlu stále správně vytvořen. Když je existující uzel vložen do stromu modelu DOM, je odebrán z původní pozice a přidán na jeho cílovou pozici.  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
