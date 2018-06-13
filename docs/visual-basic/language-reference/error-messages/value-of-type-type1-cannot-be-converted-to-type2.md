---
title: Hodnotu typu &#39;type1&#39; nelze převést na &#39;type2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 9e59d3bc5e2bfca3628248d08ffc475334d4da79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602752"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>Hodnotu typu &#39;type1&#39; nelze převést na &#39;type2&#39;
Hodnotu typu 'type1' nelze převést na 'type2'. Vlastnost 'Hodnota' můžete získat hodnotu řetězce první prvek '\<parentElement > ".  
  
 Byl proveden pokus o implicitně převést literál na určitý typ XML. Literál XML nelze implicitně převést na zadaný typ.  
  
 **ID chyby:** BC31194  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použití `Value` vlastnost literál XML tak, aby odkazovaly jako jeho hodnotu `String`. Použití `CType` funkce, funkce Převod jiného typu, nebo <xref:System.Convert> třída přetypovat na hodnotu jako zadaného typu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Convert>  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
