---
title: Hodnotu typu 'type1' nelze převést na 'type2'.
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: eb30d63e83452e75f353c44a9d0445c7dbb1013a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287505"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a>Hodnotu typu 'type1' nelze převést na 'type2'.
Nelze převést hodnotu typu 'type1' na 'type2'. Vlastnost 'Value' slouží k získání řetězcové hodnoty prvního prvku řetězce "\<parentElement >'.  
  
 Byl proveden pokus o implicitně přetypován na určitý typ literálu XML. Literál XML nelze přetypovat na zadaný typ implicitně.  
  
 **ID chyby:** BC31194  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použití `Value` vlastnost tak, aby odkazovaly na jeho hodnotu jako literál XML `String`. Použití `CType` funkce, jiné funkce pro převod typu, nebo <xref:System.Convert> k přetypování hodnoty jako zadaný typ třídy.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Convert>
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
