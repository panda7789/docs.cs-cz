---
title: Předávání parametrů typu odkazu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: f4329c525995b8246427072d1f537d91d875ef95
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596263"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Předávání parametrů typu odkazu (Průvodce programováním v C#)
Proměnná [typu odkazu](../../language-reference/keywords/reference-types.md) neobsahuje přímo data; obsahuje odkaz na jeho data. Při předání parametru typu odkazu podle hodnoty je možné změnit data patřící do odkazovaného objektu, jako je například hodnota člena třídy. Nelze však změnit hodnotu samotného odkazu; Nemůžete například použít stejný odkaz pro přidělení paměti pro nový objekt a jeho zachování mimo metodu. Chcete-li to provést, předejte parametr pomocí klíčového slova [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) . Pro zjednodušení používá `ref`následující příklady.  
  
## <a name="passing-reference-types-by-value"></a>Předávání typů odkazů podle hodnoty  
 Následující příklad ukazuje předání parametru typu odkazu, `arr`, podle hodnoty, metodě,. `Change` Vzhledem k tomu, že parametr je `arr`odkaz na, je možné změnit hodnoty prvků pole. Pokus o změnu přiřazení parametru do jiného umístění paměti však funguje pouze uvnitř metody a nemá vliv na původní proměnnou `arr`.  
  
 [!code-csharp[csProgGuideParameters#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#7)]  
  
 V předchozím příkladu je pole, `arr`,, který je odkazový typ, předáno metodě `ref` bez parametru. V takovém případě je kopie odkazu, který odkazuje na `arr`, předána metodě. Výstup ukazuje, že je možné, aby metoda změnila obsah prvku pole v tomto případě z `1` na. `888` Avšak přidělení nové části paměti pomocí operátoru `Change` [New](../../language-reference/operators/new-operator.md) v metodě způsobí, že proměnná `pArray` odkazuje na nové pole. Proto všechny změny, které nejsou ovlivněny, nebudou mít vliv na `arr`původní pole, které je `Main`vytvořeno v rámci. Ve skutečnosti jsou v tomto příkladu vytvořena dvě pole, jedna uvnitř `Main` a jedna `Change` uvnitř metody.  
  
## <a name="passing-reference-types-by-reference"></a>Předávání typů odkazů odkazem  
 Následující příklad je stejný jako předchozí příklad s tím rozdílem, že `ref` klíčové slovo je přidáno do záhlaví metody a volání. Všechny změny, které probíhají v metodě, ovlivňují původní proměnnou v volajícím programu.  
  
 [!code-csharp[csProgGuideParameters#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#8)]  
  
 Všechny změny, které probíhají v metodě, ovlivňují původní pole v `Main`. Ve skutečnosti je původní pole znovu přiděleno pomocí `new` operátoru. Proto po volání `Change` metody všechny `arr` odkazy odkazují na pole s pěti prvky, `Change` které je vytvořeno v metodě.  
  
## <a name="swapping-two-strings"></a>Záměna dvou řetězců  
 Výměna řetězců je dobrým příkladem předání parametrů typu odkazu odkazem. V příkladu jsou dva řetězce `str1` a `str2`, inicializovány `SwapStrings` v `Main` a předány metodě jako parametry upravené `ref` klíčovým slovem. Tyto dva řetězce jsou v rámci metody prohozeny a `Main` uvnitř také.  
  
 [!code-csharp[csProgGuideParameters#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#9)]  
  
 V tomto příkladu musí být parametry předány odkazem na vliv na proměnné v volajícím programu. Odeberete-li `ref` klíčové slovo z hlavičky metody a volání metody, nebudou provedeny žádné změny v volajícím programu.  
  
 Další informace o řetězcích naleznete v tématu [String](../../language-reference/keywords/string.md).  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Předávání parametrů](./passing-parameters.md)
- [ref](../../language-reference/keywords/ref.md)
- [in](../../language-reference/keywords/in-parameter-modifier.md)
- [out](../../language-reference/keywords/out.md)
- [Odkazové typy](../../language-reference/keywords/reference-types.md)
