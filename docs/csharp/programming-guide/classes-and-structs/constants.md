---
title: Konstanty – Průvodce programováním v C#
description: Konstanty v jazyce C# jsou hodnoty literálu v době kompilace, které se po zkompilování programu nemění. Konstanty mohou být pouze předdefinované typy jazyka C#.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: dd42dcd62bb46898c20f14cdc893b8f5801894f2
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474979"
---
# <a name="constants-c-programming-guide"></a>Konstanty (Průvodce programováním v C#)
Konstanty jsou neměnné hodnoty, které jsou známy v době kompilace a nemění se po dobu života programu. Konstanty jsou deklarovány s modifikátorem [const](../../language-reference/keywords/const.md) . Pouze [předdefinované typy](../../language-reference/builtin-types/built-in-types.md) jazyka C# (s výjimkou <xref:System.Object?displayProperty=nameWithType> ) mohou být deklarovány jako `const` . Uživatelsky definované typy, včetně tříd, struktur a polí, nemůžou být `const` . Použijte modifikátor [jen pro čtení](../../language-reference/keywords/readonly.md) k vytvoření třídy, struktury nebo pole, která je inicializována jednou za běhu (například v konstruktoru) a poté nelze změnit.  
  
 Jazyk C# nepodporuje `const` metody, vlastnosti a události.  
  
 Typ výčtu umožňuje definovat pojmenované konstanty pro integrální předdefinované typy (například,, `int` `uint` `long` a tak dále). Další informace naleznete v tématu [Enum](../../language-reference/builtin-types/enum.md).  
  
 Konstanty musí být inicializovány, jakmile jsou deklarovány. Příklad:  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 V tomto příkladu je konstanta `months` vždy 12 a nemůže být změněna ani samotnou třídou. Ve skutečnosti, když kompilátor narazí na konstantní identifikátor ve zdrojovém kódu jazyka C# (například `months` ), nahradí hodnotu literálu přímo do kódu přestupného jazyka (IL), který vytvoří. Vzhledem k tomu, že v době běhu není přiřazena žádná proměnná adresa, nelze `const` pole předat odkazem a nelze ji ve výrazu použít jako l-value.  
  
> [!NOTE]
> Buďte opatrní při odkazování na konstantní hodnoty definované v jiném kódu, jako jsou knihovny DLL. Pokud nová verze knihovny DLL definuje novou hodnotu pro konstantu, program bude stále obsahovat starou hodnotu literálu, dokud nebude znovu zkompilována s novou verzí.  
  
 Současně lze deklarovat více konstant stejného typu, například:  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 Výraz, který se používá k inicializaci konstanty, může odkazovat na jinou konstantu, pokud nevytvoří cyklický odkaz. Příklad:  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 Konstanty je možné označit jako [veřejné](../../language-reference/keywords/public.md), [privátní](../../language-reference/keywords/private.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné interní](../../language-reference/keywords/protected-internal.md) nebo [soukromé chráněné](../../language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definují způsob, jakým uživatelé třídy mají přístup k konstantě. Další informace najdete v tématu [modifikátory přístupu](./access-modifiers.md).  
  
 Konstanty jsou dostupné, jako by se jednalo o [statická](../../language-reference/keywords/static.md) pole, protože hodnota konstanty je stejná pro všechny instance daného typu. Klíčové slovo nepoužíváte `static` k jejich deklaraci. Výrazy, které nejsou ve třídě definující konstantu, musí používat název třídy, tečku a název konstanty pro přístup k konstantě. Příklad:  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Vlastnosti](./properties.md)
- [Typy](../types/index.md)
- [readonly](../../language-reference/keywords/readonly.md)
- [Neměnnosti v C# Part One: druhy neměnnosti](https://docs.microsoft.com/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability)
