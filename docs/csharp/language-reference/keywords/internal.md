---
title: internal (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 54ec003683953b53dedf8885a41350daf5338f83
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399439"
---
# <a name="internal-c-reference"></a>internal (Referenční dokumentace jazyka C#)
`internal` – Klíčové slovo je [modifikátor přístupu](../../../csharp/language-reference/keywords/access-modifiers.md) pro typy a členy typu. 
  
 > Tato stránka popisuje `internal` přístup. `internal` – Klíčové slovo je také součástí [ `protected internal` ](./protected-internal.md) modifikátor přístupu.
  
Vnitřní typy nebo členy jsou přístupné jenom v souborech ve stejném sestavení, jako v následujícím příkladu:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 Porovnání `internal` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md) a [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Další informace o sestavení, naleznete v tématu [sestavení a globální mezipaměť sestavení](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).  
  
 Běžné použití interního přístupu je ve vývoji založených na komponentách, protože umožňuje skupina součástí privátní způsobem spolupracovat bez zasahování přímo do zbytku kódu aplikace. Například může poskytovat architekturu pro tvorbu grafické uživatelské rozhraní `Control` a `Form` třídy, které spolupracují s použitím členy mají interní přístup. Vzhledem k tomu, že tyto členy jsou interní, že nejsou zveřejněné kód, který používá rozhraní.  
  
 Jedná se o chybu, chcete-li odkazovat typ nebo člen interní přístup mimo sestavení, ve kterém byl definován.  
  
## <a name="example"></a>Příklad  
 Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly1_a.cs`. První soubor obsahuje interní základní třída, `BaseClass`. V souboru druhý pokus o vytvoření instance `BaseClass` dojde k chybě.  
  
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
 V tomto příkladu použijte stejné soubory, které jste použili v příkladu 1 a změňte úroveň usnadnění `BaseClass` k `public`. Také změnit úroveň přístupnost člena `IntM` k `internal`. V takovém případě můžete vytvořit instanci třídy, ale k interní členu nelze přistupovat.  
  
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
// Compile with: /reference:Assembly2.dll  
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

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [protected](../../../csharp/language-reference/keywords/protected.md)
