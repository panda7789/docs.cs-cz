---
title: "static – modifikátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c47f4a19843039c27ef9f1602581d1004fb8fd76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="static-c-reference"></a>static – modifikátor (Referenční dokumentace jazyka C#)
Použití `static` modifikátor deklarovat statický člen, který patří k samotného typu, nikoli na konkrétní objekt. `static` Modifikátor lze použít s třídy, pole, metody, vlastnosti, operátory, události a konstruktory, ale nedá se použít s indexery, finalizační metody nebo jiného typu než třídy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Příklad  
 Následující třídy je deklarován jako `static` a obsahuje pouze `static` metody:  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 Konstanta nebo typ deklarace je implicitně je statický člen.  
  
 Statický člen nemůže odkazovat pomocí instance. Místo toho se odkazuje prostřednictvím název typu. Zvažte například následující třídy:  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 K odkazování na statický člen `x`, použijte plně kvalifikovaný název `MyBaseC.MyStruct.x`, pokud člen je přístupná ze stejného oboru:  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 Při instance třídy obsahuje kopii všechna pole instance třídy, existuje pouze jedna kopie každého statické pole.  
  
 Není možné použít [to](../../../csharp/language-reference/keywords/this.md) tak, aby odkazovaly statické metody nebo vlastnosti přistupující objekty.  
  
 Pokud `static` – klíčové slovo použijí na třídu, musí být statické všichni členové třídy.  
  
 Statické konstruktory mohou mít třídy a statické třídy. Statické konstruktory jsou volány v určitém okamžiku mezi při spuštění programu a vytvoření instance třídy.  
  
> [!NOTE]
>  `static` – Klíčové slovo má více omezenou používá než v jazyce C++. K porovnání s – klíčové slovo C++, najdete v části [třídy úložiště (C++)](/cpp/cpp/storage-classes-cpp#static).
  
 K předvedení statické členy, zvažte třída, která představuje zaměstnanci společnosti. Předpokládejme, že třída obsahuje metody pro počet zaměstnanci a pole slouží k uložení počet zaměstnanců. Metoda a pole nepatří do žádné instance zaměstnanců. Místo toho, které patří třída společnosti. Proto že by měl deklarované jako statické členy třídy.  
  
## <a name="example"></a>Příklad  
 Tento příklad načte název a ID nové zaměstnance, zvýší čítač zaměstnanec jedním a zobrazí informace o nové zaměstnance a nové číslo zaměstnance. Tento program pro jednoduchost, čte aktuální počet zaměstnanci z klávesnice. V reálné aplikaci musí být tyto informace čtení ze souboru.  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, že i když můžete inicializovat statické pole s použitím jiné statické pole ještě nebyla deklarována, výsledky se nedefinované dokud explicitně přiřadit hodnotu statické pole.  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Statické třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
