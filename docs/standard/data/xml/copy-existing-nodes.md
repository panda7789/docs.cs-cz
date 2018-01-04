---
title: "Zkopírujte existující uzly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c026d9f825375d74d53d5cc46969ff0f713bab1c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="copy-existing-nodes"></a>Zkopírujte existující uzly
Existuje mnoho metody a vlastnosti v XML objektu modelu DOM (Document) můžete použít k výběru uzlu, jako například **SelectSingleNode**, **ChildNodes [int i]**, **atributy [int i]**. Jakmile uzlu je vybraná, můžete je do stromu pomocí jedné z metod vložení, které fungují pro tento typ konkrétním uzlu. Pouze omezení pro vkládání uzlu do stromu je, že je dokument stále ve správném formátu po vložení uzlu. Když stávající uzel vložíte do stromu modelu DOM, je odebrán z jeho původní pozice a přidat do cílové polohy.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
