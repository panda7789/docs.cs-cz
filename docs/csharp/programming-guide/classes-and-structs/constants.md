---
title: Konstanty - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 3cfb238317e14df8d663bc96ddf46e863c7b98be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663872"
---
# <a name="constants-c-programming-guide"></a>Konstanty (Průvodce programováním v C#)
Konstanty jsou neměnné hodnoty, které jsou v době kompilace znám a nemění po celou dobu životnosti programu. Konstanty jsou deklarovány pomocí [const](../../../csharp/language-reference/keywords/const.md) modifikátor. Jenom C# předdefinovaných typů (s výjimkou <xref:System.Object?displayProperty=nameWithType>) mohou být deklarovány jako `const`. Seznam předdefinovaných typů najdete v tématu [tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md). Uživatelem definované typy, včetně třídy, struktury a pole, nemohou být `const`. Použití [jen pro čtení](../../../csharp/language-reference/keywords/readonly.md) modifikátor vytvořit třídu, strukturu nebo pole, která je inicializována jednou za běhu (například v konstruktoru) a po tomto datu se nedá změnit.  
  
 C# nepodporuje `const` metody, vlastnosti nebo události.  
  
 Typ výčtu umožňuje definovat pojmenované konstanty pro integrální předdefinovaných typů (například `int`, `uint`, `long`, a tak dále). Další informace najdete v tématu [výčtu](../../../csharp/language-reference/keywords/enum.md).  
  
 Konstanty musí být inicializován, jako jsou deklarovány. Příklad:  
  
 [!code-csharp[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]  
  
 V tomto příkladu konstanty `months` je vždy 12 a nelze ho změnit i pomocí vlastní třídy. Ve skutečnosti, když kompilátor narazí konstanty identifikátoru ve zdrojovém kódu jazyka C# (například `months`), nahradí jej přímo do kódu (IL intermediate language), který vytváří hodnotu literálu. Protože neexistuje žádné proměnné adresu přidruženou k za běhu, konstanta `const` pole nemůže být předány podle odkazu a nemůže být použit jako l hodnotou ve výrazu.  
  
> [!NOTE]
>  Buďte opatrní při odkazování na konstantní hodnoty, které jsou definovány v jiném kódu, jako je například knihovny DLL. Pokud nová verze knihovny DLL definuje novou hodnotu pro konstantu, váš program stále podržte původní hodnota literálu, dokud je znovu zkompilovat s novou verzí.  
  
 Více konstant stejného typu mohou být deklarovány ve stejnou dobu, například:  
  
 [!code-csharp[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]  
  
 Výraz, který slouží k inicializaci konstantu mohou odkazovat s jinou konstantou, pokud nedojde k vytvoření cyklického odkazu. Příklad:  
  
 [!code-csharp[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]  
  
 Konstanty může být označený jako [veřejné](../../../csharp/language-reference/keywords/public.md), [privátní](../../../csharp/language-reference/keywords/private.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [chráněné vnitřní](../../../csharp/language-reference/keywords/protected-internal.md)nebo [private, protected](../../../csharp/language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definují, jak můžete uživatelům třídy ke konstantě přistoupit. Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Konstanty jsou přístupné, jako kdyby byly [statické](../../../csharp/language-reference/keywords/static.md) pole, protože hodnota konstanty je stejný pro všechny instance daného typu. Je velmi riskantní používat `static` – klíčové slovo je deklarovat. Výrazy, které nejsou ve třídě, která definuje konstantu používaly název třídy, tečku a název konstanty ke konstantě přistoupit. Příklad:  
  
 [!code-csharp[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Typy](../../../csharp/programming-guide/types/index.md)
- [readonly](../../../csharp/language-reference/keywords/readonly.md)
- [Neměnnost v C# část 1: Druhy neměnnosti](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
