---
title: Kopírování existujících uzlů
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eda5c9b4851b29c0a76e45414d7c47ba52252455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864127"
---
# <a name="copy-existing-nodes"></a>Kopírování existujících uzlů
Existuje mnoho metod a vlastností v XML dokumentu objektu modelu modelu DOM () vám pomůže se vyberte uzel, jako je například **SelectSingleNode**, **ChildNodes [int můžu]**, **atributy [int můžu]**. Po výběru uzlu ji můžete vložit do stromu pomocí jedné z metod vložení, které fungují pro daný typ konkrétní uzel. Jediným omezením při vkládání uzlu do stromu je, že dokument přesto musí být ve správném formátu po vložení uzlu. Když existující uzel je vložen do stromu modelu DOM, je odebrán z jeho původní pozice a přidány do cílového umístění.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
