---
title: Předávání parametrů typu odkazu – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: 6fa0e60fafabaa9fb04cdc5d5bf3f9e29490e84f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714723"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Předávání parametrů typu odkazu (Průvodce programováním v C#)
Proměnná [typu odkazu](../../language-reference/keywords/reference-types.md) neobsahuje jeho data přímo; obsahuje odkaz na jeho data. Když předáte parametr typu odkazu podle hodnoty, je možné změnit data patřící do odkazovaného objektu, například hodnotu člena třídy. Hodnotu samotného odkazu však nelze změnit. Například nelze použít stejný odkaz k přidělení paměti pro nový objekt a mít ji zachovat mimo metodu. Chcete-li to provést, předejte parametr pomocí klíčového slova [ref](../../language-reference/keywords/ref.md) nebo [out.](../../language-reference/keywords/out-parameter-modifier.md) Pro jednoduchost používají `ref`následující příklady .  
  
## <a name="passing-reference-types-by-value"></a>Předávání typů odkazů podle hodnoty  
 Následující příklad ukazuje předání parametru typu `arr`odkazu , podle hodnoty `Change`metodě . Vzhledem k tomu, `arr`že parametr je odkaz na , je možné změnit hodnoty prvků pole. Pokus o opětovné přiřazení parametru do jiného umístění v paměti však funguje `arr`pouze uvnitř metody a nemá vliv na původní proměnnou .  
  
 [!code-csharp[csProgGuideParameters#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#7)]  
  
 V předchozím příkladu je `arr`pole , , což je typ odkazu, `ref` předáno metodě bez parametru. V takovém případě je metoda předána kopie `arr`odkazu, na který odkazuje na , . Výstup ukazuje, že je možné pro metodu změnit obsah prvku pole, v tomto případě z `1` na `888`. Přidělení nové části paměti pomocí [nového](../../language-reference/operators/new-operator.md) operátoru `Change` uvnitř metody však `pArray` způsobí, že proměnná odkazuje na nové pole. Proto žádné změny po které nebude mít `arr`vliv na `Main`původní pole , , který je vytvořen uvnitř . Ve skutečnosti jsou v tomto příkladu vytvořena `Main` dvě pole, jedno uvnitř a jedno uvnitř `Change` metody.  
  
## <a name="passing-reference-types-by-reference"></a>Předávání typů odkazů podle odkazu  
 Následující příklad je stejný jako v předchozím `ref` příkladu s tím rozdílem, že klíčové slovo je přidáno do hlavičky metody a volání. Všechny změny, ke kterým dojde v metodě, ovlivní původní proměnnou v volajícím programu.  
  
 [!code-csharp[csProgGuideParameters#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#8)]  
  
 Všechny změny, které probíhají uvnitř metody ovlivnit `Main`původní pole v . Ve skutečnosti původní pole je přerozdělena pomocí operátoru. `new` Proto po volání `Change` metody, všechny `arr` odkazy na odkazuje na pole pěti `Change` prvků, který je vytvořen v metodě.  
  
## <a name="swapping-two-strings"></a>Výměna dvou řetězců  
 Prohození řetězců je dobrým příkladem předávání parametrů typu odkazu odkazem. V příkladu jsou dva `str1` `str2`řetězce a , `Main` inicializovány a předány metodě `SwapStrings` jako parametry změněné `ref` klíčovým slovem. Dva řetězce jsou vyměněny uvnitř metody `Main` a uvnitř také.  
  
 [!code-csharp[csProgGuideParameters#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#9)]  
  
 V tomto příkladu musí být parametry předány odkazem, aby ovlivnily proměnné v volajícím programu. Pokud odeberete `ref` klíčové slovo z hlavičky metody i volání metody, nebudou v volajícím programu žádné změny.  
  
 Další informace o řetězcích naleznete v [tématu string](../../language-reference/builtin-types/reference-types.md).  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Předávání parametrů](./passing-parameters.md)
- [ref](../../language-reference/keywords/ref.md)
- [In](../../language-reference/keywords/in-parameter-modifier.md)
- [ven](../../language-reference/keywords/out.md)
- [Odkazové typy](../../language-reference/keywords/reference-types.md)
