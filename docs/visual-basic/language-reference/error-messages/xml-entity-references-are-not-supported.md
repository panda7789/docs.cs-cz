---
title: Odkazy na entity XML nejsou podporovány.
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: ae997d853a93999a3b29215ea1257da7a1d48c84
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406453"
---
# <a name="xml-entity-references-are-not-supported"></a>Odkazy na entity XML nejsou podporovány.
Odkaz na entitu (například `©` ), který není definován ve specifikaci XML 1,0, je obsažen jako hodnota pro LITERÁL XML. `&` `"` `<` `>` `'` V literálech XML jsou podporovány pouze odkazy na entity XML,,, a.  
  
 **ID chyby:** BC31180  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte odkaz na nepodporovanou entitu.  
  
## <a name="see-also"></a>Viz také

- [Literály XML a specifikace XML 1.0](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [Literály XML](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
