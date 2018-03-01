---
title: "& č. 39; &lt;výraz&gt;& č. 39; nelze použít jako omezení typu."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c7271018a93c97ed90dc272f7f5404c0f0a22d42
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a>& č. 39; &lt;výraz&gt;& č. 39; nelze použít jako omezení typu.
Seznam omezení obsahuje výraz, který nepředstavuje platný parametr typu omezení.  
  
 Seznam omezení ukládá požadavky na typ argument předaný parametr typu. V libovolné kombinace můžete určit následující požadavky:  
  
-   Argument typu musí implementovat jednu nebo více rozhraní  
  
-   Argument typu musí dědit z maximálně jednu třídu  
  
-   Argument typu musí vystavit konstruktor bez parametrů, kterým může přistupovat vytváření kódu (zahrnout `New` omezení)  
  
 Pokud neuvedete žádné konkrétní třídy nebo rozhraní v seznamu omezení, můžete použít obecnější požadavek zadáním jednoho z následujících akcí:  
  
-   Argument typu musí být typu hodnoty (zahrnout `Structure` omezení)  
  
-   Argument typu musí být typu odkazu (zahrnout `Class` omezení)  
  
 Nelze zadat současně `Structure` a `Class` pro stejný typ parametru a nelze zadat buď jednu více než jednou.  
  
 **ID chyby:** BC32061  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ověřte, jestli jsou správně zadané ve výrazu a jejích elementů.  
  
-   Výraz není způsobilá pro předchozí seznam požadavků, odeberte ji ze seznamu omezení.  
  
-   Pokud výraz odkazuje na rozhraní nebo třídy, ověřte, zda kompilátor má přístup k tomuto rozhraní nebo třídy. Možná budete muset kvalifikovat jeho název a možná budete muset přidat odkaz na projekt. Další informace najdete v tématu "Odkazy na projekty" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy hodnot a odkazové typy](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 
