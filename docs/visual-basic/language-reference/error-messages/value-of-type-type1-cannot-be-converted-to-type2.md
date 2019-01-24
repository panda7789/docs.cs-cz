---
title: Hodnotu typu &#39;type1&#39; nelze převést na &#39;typ2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 657e0feb675e15b9ece00d40c3d1ebe932a29099
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568283"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>Hodnotu typu &#39;type1&#39; nelze převést na &#39;typ2&#39;
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
