---
title: "Hodnota typu & č. 39; type1 & č. 39; nelze převést na & č. 39; type2 & č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords: BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: efa6fcd4d996fb3277cc4cac2af16a86a2d65977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>Hodnota typu & č. 39; type1 & č. 39; nelze převést na & č. 39; type2 & č. 39;
Hodnotu typu 'type1' nelze převést na 'type2'. Vlastnost 'Hodnota' můžete získat hodnotu řetězce první prvek '\<parentElement > ".  
  
 Byl proveden pokus o implicitně převést literál na určitý typ XML. Literál XML nelze implicitně převést na zadaný typ.  
  
 **ID chyby:** BC31194  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použití `Value` vlastnost literál XML tak, aby odkazovaly jako jeho hodnotu `String`. Použití `CType` funkce, funkce Převod jiného typu, nebo <xref:System.Convert> třída přetypovat na hodnotu jako zadaného typu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Convert>  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [XML – literály](../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
