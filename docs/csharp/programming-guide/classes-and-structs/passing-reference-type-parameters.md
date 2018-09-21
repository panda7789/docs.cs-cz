---
title: Předávání parametrů typu odkazu (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: d577754e8cb686c40172abd6c0bbd00bc481f737
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46471074"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Předávání parametrů typu odkazu (Průvodce programováním v C#)
Proměnné [odkazovat na typ](../../../csharp/language-reference/keywords/reference-types.md) neobsahuje data přímo; obsahuje odkaz na svoje data. Při předávání parametrů typu odkazu podle hodnoty, je možné změnit data patřící do odkazovaný objekt, jako je například hodnota člena třídy. Nelze však změnit hodnotu referenční samotné; například nelze použít stejný odkaz k přidělení paměti pro novou třídu a jeho zachovat mimo metodu. Chcete-li to mohli udělat, předejte parametr pomocí [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) – klíčové slovo. Pro zjednodušení následující příklady používají `ref`.  
  
## <a name="passing-reference-types-by-value"></a>Typy odkazů předání hodnotou  
 Následující příklad ukazuje předávání parametrů typu odkazu, `arr`, podle hodnoty, na metodu, `Change`. Protože parametr je odkazem na `arr`, je možné ke změně hodnot prvků pole. Ale pokus o přiřazení parametr pouze na jiné paměťové místo funguje uvnitř metody a nemá vliv na původní proměnná `arr`.  
  
 [!code-csharp[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 V předchozím příkladu je pole, `arr`, což je typ odkazu, se předá metodě bez `ref` parametru. V takovém případě kopii odkaz, který odkazuje na `arr`, je předán metodě. Výstup ukazuje, že je možné pro metodu, chcete-li změnit obsah prvku pole, v tomto případě z `1` k `888`. Ale přidělování novou část paměti pomocí [nové](../../../csharp/language-reference/keywords/new.md) operátor uvnitř `Change` metoda provádí proměnné `pArray` odkazovat na nové pole. Díky tomu se změny po, která nebude mít vliv na původní pole `arr`, který je vytvořen uvnitř `Main`. Ve skutečnosti se vytvoří dvě pole v tomto příkladu ho uvnitř `Main` a jeden `Change` metoda.  
  
## <a name="passing-reference-types-by-reference"></a>Typy odkazů předávání odkazem.  
 Následující příklad je stejný jako předchozí příklad, s výjimkou, že `ref` – klíčové slovo se přidá do hlavičky metody a volání. Všechny změny, které se provedou v metodě vliv na původní proměnné ve volání programu.  
  
 [!code-csharp[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 Všechny změny, které provedou uvnitř metody vliv na původní pole v `Main`. Ve skutečnosti je původní pole nevyčerpané pomocí `new` operátor. Proto po volání `Change` metoda, všechny odkazy na `arr` odkazuje na pole pět element, který je vytvořen v `Change` metody.  
  
## <a name="swapping-two-strings"></a>Vzájemná záměna dva řetězce  
 Vzájemná záměna řetězce je dobrým příkladem předávání parametrů typu odkazu odkazem. V tomto příkladu jsou dva řetězce `str1` a `str2`, jsou inicializovány v `Main` a předat `SwapStrings` jako parametry upravil metodu `ref` – klíčové slovo. Dva řetězce jsou přehozeny uvnitř metody a uvnitř `Main` také.  
  
 [!code-csharp[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 V tomto příkladu parametry muset být předány podle odkazu, který má být ovlivněn proměnné ve volání programu. Pokud odeberete `ref` – klíčové slovo z metody záhlaví a volání metody, beze změn bude probíhat ve volání programu.  
  
 Další informace o řetězcích naleznete v tématu [řetězec](../../../csharp/language-reference/keywords/string.md).  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Předávání parametrů](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
- [ref](../../../csharp/language-reference/keywords/ref.md)  
- [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)  
- [out](../../../csharp/language-reference/keywords/out.md)  
- [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)
