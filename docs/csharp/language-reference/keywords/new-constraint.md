---
title: new – omezení (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 77c955102ba9cede831c85838a6a7e57025ad35b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268993"
---
# <a name="new-constraint-c-reference"></a>new – omezení (Referenční dokumentace jazyka C#)
`new` Omezení určuje, že některý argument typu v deklaraci – obecná třída musí mít konstruktor public bez parametrů. Pokud chcete používat nové omezení, typ nemůže být abstraktní.  
  
## <a name="example"></a>Příklad  
 Použít `new` omezení pro parametr typu když obecná třída vytváří nové instance typu, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a>Příklad  
 Při použití `new()` omezení s jiná omezení, musí být zadaná poslední:  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 Další informace najdete v tématu [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Obecné typy](../../../csharp/programming-guide/generics/index.md)
