---
title: Hodnotu typu 'type1' nelze převést na 'type2'.
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 4a0f3eb2b1603899e9acc1273c023ec5d0ed3132
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913349"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a>Hodnotu typu 'type1' nelze převést na 'type2'.
Nelze převést hodnotu typu 'type1' na 'type2'. Vlastnost 'Value' slouží k získání řetězcové hodnoty prvního prvku řetězce "\<parentElement >'.  
  
 Byl proveden pokus o implicitně přetypován na určitý typ literálu XML. Literál XML nelze přetypovat na zadaný typ implicitně.  
  
 **ID chyby:** BC31194  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Použití `Value` vlastnost tak, aby odkazovaly na jeho hodnotu jako literál XML `String`. Použití `CType` funkce, jiné funkce pro převod typu, nebo <xref:System.Convert> k přetypování hodnoty jako zadaný typ třídy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Convert>
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
