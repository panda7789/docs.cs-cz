---
title: "readonly – modifikátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 175eebf6e49e79db1ff86689599416a10827a792
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="readonly-c-reference"></a>readonly – modifikátor (Referenční dokumentace jazyka C#)
`readonly` – Klíčové slovo je modifikátor, který můžete použít na pole. Pokud obsahuje deklaraci pole `readonly` modifikátor, přiřazení pole zaváděné deklaraci může dojít pouze v rámci deklarace nebo v konstruktoru ve stejné třídě.  
  
## <a name="readonly-field-example"></a>Pole jen pro čtení, například  
 V tomto příkladu hodnota v poli `year` nelze změnit v metodě `ChangeYear`, i když je přiřazen hodnotu v konstruktoru třídy:  
  
 [!code-csharp[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 Můžete přiřadit hodnotu na `readonly` pouze v kontextech následující pole:  
  
-   Pokud proměnná je inicializován v deklaraci, například:  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   V konstruktorech instance třídy pro pole instance, která obsahuje deklaraci pole nebo pro statické pole na statického konstruktoru třídy, která obsahuje deklaraci pole. Existují i pouze kontexty, ve kterých je platná pro předávání `readonly` jako pole [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) nebo [ref](../../../csharp/language-reference/keywords/ref.md) parametr.  
  
> [!NOTE]
>  `readonly` – Klíčové slovo se liší od [const](../../../csharp/language-reference/keywords/const.md) – klíčové slovo. A `const` pole lze inicializovat pouze na deklaraci pole. A `readonly` pole jde inicializovat na deklaraci nebo v konstruktoru. Proto `readonly` pole může mít různé hodnoty v závislosti na konstruktoru použít. Navíc při `const` pole je argumentem konstanta kompilaci `readonly` pole lze použít pro modul runtime konstanty jako v následujícím příkladu:  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="comparing-readonly-and-non-readonly-instance-fields"></a>Porovnání instance pole jen pro čtení a jen pro čtení  
 [!code-csharp[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 V předchozím příkladu, pokud použijete příkaz takto:  
  
 `p2.y = 66;        // Error`  
  
 Zobrazí se chybová zpráva kompilátoru:  
  
 `The left-hand side of an assignment must be an l-value`  
  
 což je ke stejné chybě, kterou získáte, když se pokusí přiřadit hodnotu konstanty.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [const](../../../csharp/language-reference/keywords/const.md)  
 [Pole](../../../csharp/programming-guide/classes-and-structs/fields.md)
