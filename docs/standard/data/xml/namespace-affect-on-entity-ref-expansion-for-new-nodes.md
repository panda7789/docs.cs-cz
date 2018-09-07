---
title: Namespace vliv na rozšíření odkazu Entity pro nové uzly, který obsahují elementy a atributy
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4231516848cc50212a3a6a03d101907b2f6b3920
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44069587"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Namespace vliv na rozšíření odkazu Entity pro nové uzly, který obsahují elementy a atributy
Protože obsah entity deklarace může obsahovat prakticky cokoli, je možné, že obsah by mohl obsahovat prvky jako `<!ENTITY aname "<elem>test</elem>">`.  
  
 Když je analyzovat kód XML, `&aname;` není rozbalen jeho nahrazení obsahu při analýze. Rozšíření XML není provést, protože rozlišení oboru názvů pro element nelze provést, dokud se uzel je umístěn v dokumentu. Do té doby není k dispozici žádné znalosti z jaké obor názvů je v oboru. Pokud uzel přejde do dokumentu, pak dojde k rozlišení oboru názvů a výsledné entity obsahu je analyzován do jeho odpovídající uzly.  
  
> [!NOTE]
>  Jakmile dojde k rozšíření v uzlu odkaz na nově vytvořenou entitu, se nikdy bude vyskytovat i nadále. Proto jsou obory názvů používané v náhradní text pro prvek vázány v době, který je nastaven na nadřazený uzel. Ale oboru názvů lze změnit pro existující uzly odkaz na entitu když odeberete a vložit je někde jinde, nebo odkaz na uzlech entity, které se klonují se **CloneNode** metody.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
