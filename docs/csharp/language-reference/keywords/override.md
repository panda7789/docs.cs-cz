---
title: override (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 8f692dfdf8bd34ddb62623d86ec3dadd2b8dead3
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199261"
---
# <a name="override-c-reference"></a>override (Referenční dokumentace jazyka C#)
`override` Modifikátor je potřeba rozšířit nebo upravit abstraktní nebo virtuální provádění zděděné metody, vlastnosti, indexeru nebo události.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Square` třída musí poskytovat implementaci přepsané `Area` protože `Area` se dědí z abstraktní `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 `override` Metody poskytuje novou implementaci člena, který je zděděn ze základní třídy. Metoda, která je přepsána `override` prohlášení je označován jako přepsané základní metodě. Přepsané základní metoda musí mít stejný podpis jako `override` metody. Informace o dědičnosti, naleznete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Nevirtuální nebo statické metody nelze přepsat. Přepsané základní metoda musí být `virtual`, `abstract`, nebo `override`.  
  
 `override` Deklarace nemůže změnit přístupnost `virtual` metody. Obě `override` metoda a `virtual` metoda musí mít stejný [úrovně modifikátor přístupu](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Nelze použít `new`, `static`, nebo `virtual` modifikátory upravit `override` metody.  
  
 Přepsání deklarace vlastnost musíte zadat přesně stejné modifikátor přístupu, typ a název jako zděděné vlastnosti a musí být přepsané vlastnosti `virtual`, `abstract`, nebo `override`.  
  
 Další informace o tom, jak používat `override` – klíčové slovo, naleznete v tématu [Správa verzí pomocí nových klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít nová klíčová slova Override a](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad definuje základní třídu s názvem `Employee`a odvozená třída s názvem `SalesEmployee`. `SalesEmployee` Třída zahrnuje další vlastnost `salesbonus`a přepíše metodu `CalculatePay` aby vzít v úvahu.  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [Polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)
