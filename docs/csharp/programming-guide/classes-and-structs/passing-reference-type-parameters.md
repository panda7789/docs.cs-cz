---
title: Předávání parametrů typu odkazu – Průvodce programováním v C#
description: Při předání parametru typu odkazu podle hodnoty v jazyce C# lze změnit data v odkazovaném objektu, ale nikoli hodnotu samotného odkazu.
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: 64a4735eded7a468549862b3221b4fbd0966e64d
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864706"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Předávání parametrů typu odkazu (Průvodce programováním v C#)
Proměnná [typu odkazu](../../language-reference/keywords/reference-types.md) neobsahuje přímo data; obsahuje odkaz na jeho data. Při předání parametru typu odkazu podle hodnoty je možné změnit data patřící do odkazovaného objektu, jako je například hodnota člena třídy. Nelze však změnit hodnotu samotného odkazu; Nemůžete například použít stejný odkaz pro přidělení paměti pro nový objekt a jeho zachování mimo metodu. Chcete-li to provést, předejte parametr pomocí klíčového slova [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) . Pro zjednodušení používá následující příklady `ref` .  
  
## <a name="passing-reference-types-by-value"></a>Předávání typů odkazů podle hodnoty  
 Následující příklad ukazuje předání parametru typu odkazu, `arr` , podle hodnoty, metodě, `Change` . Vzhledem k tomu, že parametr je odkaz na `arr` , je možné změnit hodnoty prvků pole. Pokus o změnu přiřazení parametru do jiného umístění paměti však funguje pouze uvnitř metody a nemá vliv na původní proměnnou `arr` .  
  
 [!code-csharp[csProgGuideParameters#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#7)]  
  
 V předchozím příkladu je pole, `arr` ,, který je odkazový typ, předáno metodě bez `ref` parametru. V takovém případě je kopie odkazu, který odkazuje na `arr` , předána metodě. Výstup ukazuje, že je možné, aby metoda změnila obsah prvku pole v tomto případě z `1` na `888` . Avšak přidělení nové části paměti pomocí operátoru [New](../../language-reference/operators/new-operator.md) v `Change` metodě způsobí, že proměnná `pArray` odkazuje na nové pole. Proto všechny změny, které nejsou ovlivněny, nebudou mít vliv na původní pole, `arr` které je vytvořeno v rámci `Main` . Ve skutečnosti jsou v tomto příkladu vytvořena dvě pole, jedna uvnitř `Main` a jedna uvnitř `Change` metody.  
  
## <a name="passing-reference-types-by-reference"></a>Předávání typů odkazů odkazem  
 Následující příklad je stejný jako předchozí příklad s tím rozdílem, že `ref` klíčové slovo je přidáno do záhlaví metody a volání. Všechny změny, které probíhají v metodě, ovlivňují původní proměnnou v volajícím programu.  
  
 [!code-csharp[csProgGuideParameters#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#8)]  
  
 Všechny změny, které probíhají v metodě, ovlivňují původní pole v `Main` . Ve skutečnosti je původní pole znovu přiděleno pomocí `new` operátoru. Proto po volání `Change` metody všechny odkazy odkazují na pole s `arr` pěti prvky, které je vytvořeno v `Change` metodě.  
  
## <a name="swapping-two-strings"></a>Záměna dvou řetězců  
 Výměna řetězců je dobrým příkladem předání parametrů typu odkazu odkazem. V příkladu jsou dva řetězce `str1` a `str2` , inicializovány v `Main` a předány `SwapStrings` metodě jako parametry upravené `ref` klíčovým slovem. Tyto dva řetězce jsou v rámci metody prohozeny a uvnitř `Main` také.  
  
 [!code-csharp[csProgGuideParameters#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#9)]  
  
 V tomto příkladu musí být parametry předány odkazem na vliv na proměnné v volajícím programu. Odeberete-li `ref` klíčové slovo z hlavičky metody a volání metody, nebudou provedeny žádné změny v volajícím programu.  
  
 Další informace o řetězcích naleznete v tématu [String](../../language-reference/builtin-types/reference-types.md).  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Předávání parametrů](./passing-parameters.md)
- [ref](../../language-reference/keywords/ref.md)
- [pro](../../language-reference/keywords/in-parameter-modifier.md)
- [mimo](../../language-reference/keywords/out.md)
- [Typy odkazů](../../language-reference/keywords/reference-types.md)
