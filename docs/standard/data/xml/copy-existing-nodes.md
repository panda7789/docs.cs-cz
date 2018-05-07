---
title: Zkopírujte existující uzly
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e7f5638d0d1f7bf450be526d7c295d4bb6a79eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="copy-existing-nodes"></a>Zkopírujte existující uzly
Existuje mnoho metody a vlastnosti v XML objektu modelu DOM (Document) můžete použít k výběru uzlu, jako například **SelectSingleNode**, **ChildNodes [int i]**, **atributy [int i]**. Jakmile uzlu je vybraná, můžete je do stromu pomocí jedné z metod vložení, které fungují pro tento typ konkrétním uzlu. Pouze omezení pro vkládání uzlu do stromu je, že je dokument stále ve správném formátu po vložení uzlu. Když stávající uzel vložíte do stromu modelu DOM, je odebrán z jeho původní pozice a přidat do cílové polohy.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
