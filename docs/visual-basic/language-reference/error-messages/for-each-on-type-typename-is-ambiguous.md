---
title: "& č. 39; Pro každý & č. 39; na typ & č. 39; &lt;typename&gt;& č. 39; je nejednoznačné, protože typ implementuje více instancí možnosti & č. 39; System.Collections.Generic.IEnumerable (Of T) & č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords: BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a74178f3f0b2e7589b87046973473582993f3ed9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>& č. 39; Pro každý & č. 39; na typ & č. 39; &lt;typename&gt;& č. 39; je nejednoznačné, protože typ implementuje více instancí možnosti & č. 39; System.Collections.Generic.IEnumerable (Of T) & č. 39;
A `For Each` příkaz určuje proměnná iterator, která má více než jeden <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda.  
  
 Iterator proměnná musí být typ, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní v jednom z `Collections` názvů [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Je možné pro třídu pro implementaci více než jeden sestavené obecné rozhraní pomocí jiný typ argumentu pro každý konstrukce. Pokud třídu, která k tomu slouží pro proměnnou iterator, tuto proměnnou má více než jeden <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda. V takovém případě [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nejde zvolit, která metoda k volání.  
  
 **ID chyby:** BC32096  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použít [DirectCast – operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) nebo [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md) přetypovat na typ proměnné iterator definování rozhraní <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda, kterou chcete použít.  
  
## <a name="see-also"></a>Viz také  
 [Pro každou... Next – příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
