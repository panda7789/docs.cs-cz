---
title: Vliv oboru názvů na rozšíření odkazu na entitu pro nové uzly, který obsahují elementy a atributy
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
ms.openlocfilehash: 4772e3f7365069c537c4ec3bc8571f2f710bc9fc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710619"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Vliv oboru názvů na rozšíření odkazu na entitu pro nové uzly, který obsahují elementy a atributy
Vzhledem k tomu, že obsah deklarace entity může obsahovat téměř cokoli, existuje možnost, že obsah může obsahovat element jako `<!ENTITY aname "<elem>test</elem>">`.  
  
 Když je kód XML analyzován, `&aname;` není rozbalený s jeho náhradním obsahem v době analýzy. Rozšíření XML není provedeno, protože překlad oboru názvů pro element nemůže nastat, dokud není uzel umístěn v dokumentu. Až do této doby nebudete znát obor názvů, který je v oboru. Když je uzel umístěn do dokumentu, pak dojde k překladu oboru názvů a výsledný obsah entity se analyzuje v příslušných uzlech.  
  
> [!NOTE]
> Jakmile dojde k rozšíření u nově vytvořeného uzlu odkazu na entitu, nikdy se znovu nespustí. Proto jsou obory názvů použité v náhradním textu pro element vázány v době, kdy je nastaven nadřazený uzel. Obor názvů lze však změnit pro existující uzly odkazů na entity, když je odeberete a vložíte někam jinam nebo na referenční uzly entit, které jsou naklonovány metodou **CloneNode** .  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
