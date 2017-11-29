---
title: "readonly – modifikátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords: readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b499f9fc5121afe6c2e92bcf8c5d2ac593b4c06c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="readonly-c-reference"></a>readonly – modifikátor (Referenční dokumentace jazyka C#)
`readonly` – Klíčové slovo je modifikátor, který můžete použít na pole. Pokud obsahuje deklaraci pole `readonly` modifikátor, přiřazení pole zaváděné deklaraci může dojít pouze v rámci deklarace nebo v konstruktoru ve stejné třídě.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu hodnota v poli `year` nelze změnit v metodě `ChangeYear`, i když je přiřazen hodnotu v konstruktoru třídy:  
  
 [!code-csharp[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 Můžete přiřadit hodnotu na `readonly` pouze v kontextech následující pole:  
  
-   Pokud proměnná je inicializován v deklaraci, například:  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   V konstruktorech instance třídy pro pole instance, která obsahuje deklaraci pole nebo pro statické pole na statického konstruktoru třídy, která obsahuje deklaraci pole. Existují i pouze kontexty, ve kterých je platná pro předávání `readonly` jako pole [out](../../../csharp/language-reference/keywords/out.md) nebo [ref](../../../csharp/language-reference/keywords/ref.md) parametr.  
  
> [!NOTE]
>  `readonly` – Klíčové slovo se liší od [const](../../../csharp/language-reference/keywords/const.md) – klíčové slovo. A `const` pole lze inicializovat pouze na deklaraci pole. A `readonly` pole jde inicializovat na deklaraci nebo v konstruktoru. Proto `readonly` pole může mít různé hodnoty v závislosti na konstruktoru použít. Navíc při `const` pole je argumentem konstanta kompilaci `readonly` pole lze použít pro modul runtime konstanty jako v následujícím příkladu:  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="example"></a>Příklad  
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Const](../../../csharp/language-reference/keywords/const.md)  
 [Pole](../../../csharp/programming-guide/classes-and-structs/fields.md)
