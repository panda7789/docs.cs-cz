---
title: Předávání parametrů typu odkazu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: 6489d31ac1e466fdbf2b47ce1aae7e1139af0960
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419047"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Předávání parametrů typu odkazu (Průvodce programováním v C#)
Proměnná [typu odkazu](../../language-reference/keywords/reference-types.md) neobsahuje přímo data; obsahuje odkaz na jeho data. Při předání parametru typu odkazu podle hodnoty je možné změnit data patřící do odkazovaného objektu, jako je například hodnota člena třídy. Nelze však změnit hodnotu samotného odkazu; Nemůžete například použít stejný odkaz pro přidělení paměti pro nový objekt a jeho zachování mimo metodu. Chcete-li to provést, předejte parametr pomocí klíčového slova [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) . Pro zjednodušení následující příklady používají `ref`.  
  
## <a name="passing-reference-types-by-value"></a>Předávání typů odkazů podle hodnoty  
 Následující příklad ukazuje předání parametru typu odkazu `arr`, podle hodnoty, do metody, `Change`. Vzhledem k tomu, že parametr je odkaz na `arr`, je možné změnit hodnoty prvků pole. Pokus o změnu přiřazení parametru do jiného umístění v paměti však funguje pouze uvnitř metody a nemá vliv na původní proměnnou, `arr`.  
  
 [!code-csharp[csProgGuideParameters#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#7)]  
  
 V předchozím příkladu je pole, `arr`, který je odkazový typ, předáno metodě bez parametru `ref`. V takovém případě je kopie odkazu, který odkazuje na `arr`, předána metodě. Výstup ukazuje, že je možné, aby metoda změnila obsah prvku pole, v tomto případě z `1` na `888`. Avšak přidělení nové části paměti pomocí operátoru [New](../../language-reference/operators/new-operator.md) v metodě `Change` způsobí, že proměnná `pArray` odkazování na nové pole. Všechny změny poté nebudou mít vliv na původní pole, `arr`, který je vytvořen v rámci `Main`. Ve skutečnosti jsou v tomto příkladu vytvořena dvě pole, jedna uvnitř `Main` a jedna uvnitř metody `Change`.  
  
## <a name="passing-reference-types-by-reference"></a>Předávání typů odkazů odkazem  
 Následující příklad je stejný jako předchozí příklad s tím rozdílem, že klíčové slovo `ref` je přidáno do záhlaví metody a volání. Všechny změny, které probíhají v metodě, ovlivňují původní proměnnou v volajícím programu.  
  
 [!code-csharp[csProgGuideParameters#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#8)]  
  
 Všechny změny, které probíhají v metodě, ovlivňují původní pole v `Main`. Ve skutečnosti je původní pole znovu přiděleno pomocí operátoru `new`. Proto po volání metody `Change` všechny odkazy na `arr` odkazují na pole s pěti prvky, které je vytvořeno v metodě `Change`.  
  
## <a name="swapping-two-strings"></a>Záměna dvou řetězců  
 Výměna řetězců je dobrým příkladem předání parametrů typu odkazu odkazem. V příkladu jsou dva řetězce, `str1` a `str2`, inicializovány v `Main` a předány do metody `SwapStrings` jako parametry upravené klíčovým slovem `ref`. Tyto dva řetězce jsou zahozeny uvnitř metody a uvnitř `Main`.  
  
 [!code-csharp[csProgGuideParameters#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#9)]  
  
 V tomto příkladu musí být parametry předány odkazem na vliv na proměnné v volajícím programu. Odeberete-li klíčové slovo `ref` z hlavičky metody a volání metody, nebudou provedeny žádné změny v volajícím programu.  
  
 Další informace o řetězcích naleznete v tématu [String](../../language-reference/builtin-types/reference-types.md).  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Předávání parametrů](./passing-parameters.md)
- [ref](../../language-reference/keywords/ref.md)
- [in](../../language-reference/keywords/in-parameter-modifier.md)
- [out](../../language-reference/keywords/out.md)
- [Odkazové typy](../../language-reference/keywords/reference-types.md)
