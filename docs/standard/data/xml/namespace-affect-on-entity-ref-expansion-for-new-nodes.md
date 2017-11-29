---
title: "Namespace vlivu na Entity odkaz na rozšíření pro nové uzly, který obsahuje elementy a atributy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 39110a9b44e6efbe7ad0331cfdb4fbe6078e7cfc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Namespace vlivu na Entity odkaz na rozšíření pro nové uzly, který obsahuje elementy a atributy
Protože obsah deklarace entita může obsahovat prakticky jakoukoli, je možné, který obsah by mohl obsahovat element jako `<!ENTITY aname "<elem>test</elem>">`.  
  
 Když je analyzovat kód XML, `&aname;` není rozbalen s jeho obsahem nahrazení při analýze. Rozšíření XML není provést, protože překlad názvů pro element nemůže proběhnout, dokud uzlu je umístěn v dokumentu. Do té doby není k dispozici žádné znalosti o jaký obor názvů je v oboru. Pokud uzel umístí do dokumentu, pak dojde k rozlišení názvů a výsledného obsahu entity je analyzován do její odpovídající uzly.  
  
> [!NOTE]
>  Jakmile dojde k rozšíření v uzlu odkazu nově vytvořené entity, se nikdy opakovat. Proto oborů názvů používaných v Nahrazovací text pro prvek je vázána na čas, který je nastavený nadřazený uzel. Ale oboru názvů lze změnit pro existující odkaz uzly entity, když odeberete a vložte je někde jinde, nebo na uzlech odkaz entity, které jsou klonovat s **CloneNode** metoda.  
  
## <a name="see-also"></a>Viz také  
 [XML Document Object Model (DOM).](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
