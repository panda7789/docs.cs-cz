---
title: "Předávání parametrů typu odkazu (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 282929d82822f81f12dae91d2f422da51a0f43e5
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Předávání parametrů typu odkazu (Průvodce programováním v C#)
Proměnná [odkazují na typ](../../../csharp/language-reference/keywords/reference-types.md) neobsahuje data přímo; obsahuje odkaz na jeho data. Pokud předáte parametr typu odkazu podle hodnoty, je možné změnit data patřící do odkazovaného objektu, například hodnotu člena třídy. Však nelze změnit hodnotu odkaz sám; například nelze použít odkaz na stejnou přidělit paměť pro novou třídu a jej zachovat mimo metodu. Kvůli tomu předat pomocí parametru [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) – klíčové slovo. Pro jednoduchost, použijte následující příklady `ref`.  
  
## <a name="passing-reference-types-by-value"></a>Typy odkazů předávání podle hodnoty  
 Následující příklad ukazuje předání parametru typu odkazu, `arr`, podle hodnoty, na metodu `Change`. Vzhledem k tomu, že je odkaz na parametr `arr`, je možné ke změně hodnot prvků pole. Ale pokus o přiřazení parametr pouze umístění různých paměti funguje uvnitř metody a nemá vliv na původní proměnná `arr`.  
  
 [!code-csharp[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 V předchozím příkladu poli `arr`, který je typu odkazu je předaný metodě bez `ref` parametr. V takovém případě kopii odkaz, který odkazuje na `arr`, je předaná metodě. Výstup ukazuje, že je možné metody pro změnu obsahu elementu pole, v tomto případě z `1` k `888`. Však přidělování novou část paměti pomocí [nové](../../../csharp/language-reference/keywords/new.md) operátor uvnitř `Change` metoda umožňuje proměnnou `pArray` odkazovat na nové pole. Proto veškeré změny, po který nebude mít vliv na původní pole `arr`, který je vytvořen uvnitř `Main`. Ve skutečnosti dvě pole jsou vytvořené v tomto příkladu jeden uvnitř `Main` a jeden uvnitř `Change` metoda.  
  
## <a name="passing-reference-types-by-reference"></a>Typy odkazů předávání odkazem  
 Následující příklad je stejný jako předchozí příklad, vyjma toho, že `ref` – klíčové slovo se přidá do hlavičky metoda a volání. Veškeré změny, které probíhají ve metodu ovlivnit původní proměnné v volací program.  
  
 [!code-csharp[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 Všechny změny, které se uskuteční uvnitř metody ovlivnit původní pole v `Main`. Ve skutečnosti původní pole je znovu přidělit, pomocí `new` operátor. Proto po volání `Change` metody žádný odkaz na `arr` odkazuje na pole pět element, který je vytvořen v `Change` metoda.  
  
## <a name="swapping-two-strings"></a>Vzájemná záměna dva řetězce  
 Vzájemná záměna řetězce je dobrým příkladem předávání parametrů typu odkazu odkazem. V příkladu dva řetězce `str1` a `str2`, jsou inicializovány v `Main` a předána `SwapStrings` jako parametry změnit metodu `ref` – klíčové slovo. Dva řetězce jsou vzájemně zaměněny uvnitř metoda a uvnitř `Main` také.  
  
 [!code-csharp[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 V tomto příkladu potřebovat parametry k předání odkazem ovlivnit proměnné v volací program. Pokud odeberete `ref` – klíčové slovo z hlavičky metoda a volání metody žádné změny bude probíhat v volací program.  
  
 Další informace o řetězcích najdete v tématu [řetězec](../../../csharp/language-reference/keywords/string.md).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Předávání parametrů](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Předávání polí pomocí parametrů ref a out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)  
 [ref](../../../csharp/language-reference/keywords/ref.md)  
 [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)  
 [out](../../../csharp/language-reference/keywords/out.md)  
 [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)
