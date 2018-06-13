---
title: internal (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: d2fcc19bb7bc6de373412e7728f3025647c0435d
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172669"
---
# <a name="internal-c-reference"></a>internal (Referenční dokumentace jazyka C#)
`internal` – Klíčové slovo je [– modifikátor přístupu](../../../csharp/language-reference/keywords/access-modifiers.md) pro různé typy a členy typu. 
  
 > Tato stránka popisuje `internal` přístup. `internal` – Klíčové slovo je také součástí [ `protected internal` ](./protected-internal.md) – modifikátor přístupu.
  
Vnitřní typy nebo členové jsou přístupné pouze v rámci soubory ve stejném sestavení jako v následujícím příkladu:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 Porovnání `internal` s další modifikátory přístupu, přečtěte si téma [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md) a [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Další informace o sestavení najdete v tématu [sestavení a globální mezipaměť sestavení](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).  
  
 Běžně používá interní přístupu se vývojem na základě součást, protože umožňuje skupina součástí, aby spolupracovali privátní způsobem bez zasahování přímo do zbytku kódu aplikace. Například může poskytnout architektura pro vytváření grafické uživatelské rozhraní `Control` a `Form` třídy, které spolupracují s pomocí členy s interní přístup. Vzhledem k tomu, že tito členové jsou interní, že nejsou zveřejněné kód, který používá rozhraní.  
  
 Jedná se o chybu tak, aby odkazovaly typ nebo člen s interní přístup mimo sestavení, ve kterém byl definován.  
  
## <a name="example"></a>Příklad  
 Tento příklad obsahuje dva soubory, `Assembly1.cs` a `Assembly1_a.cs`. První soubor obsahuje interní základní třída, `BaseClass`. V souboru druhý pokus o vytvoření instance `BaseClass` způsobí chybu.  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu použijte stejné soubory, které jste použili v příkladu 1 a změňte úroveň usnadnění `BaseClass` k `public`. Také změnit úroveň usnadnění člena `IntM` k `internal`. V takovém případě může vytvořit instanci třídy, ale nemůže přístup k interní členovi.  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)
