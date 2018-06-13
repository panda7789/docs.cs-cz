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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280150"
---
# <a name="override-c-reference"></a>override (Referenční dokumentace jazyka C#)
`override` Modifikátor je potřeba rozšířit nebo změnit abstraktní nebo virtuální implementace zděděné metoda, vlastnost, indexer nebo událostí.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Square` třída musí obsahovat přepsaného implementace `Area` protože `Area` dědí z abstraktní `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 `override` Metoda poskytuje nové implementaci člena, který je zděděn ze základní třídy. Metoda, která je přepsat `override` deklarace se označuje jako přepsaného základní metody. Přepsané základní metody musí mít stejný podpis jako `override` metoda. Informace o dědičnosti najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Nejde přepsat bez virtuální nebo statické metody. Přepsané základní metody musí být `virtual`, `abstract`, nebo `override`.  
  
 `override` Deklarace nelze změnit usnadnění přístupu `virtual` metoda. Obě `override` metoda a `virtual` metoda musí mít stejnou [úrovně – modifikátor přístupu](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Nelze použít `new`, `static`, nebo `virtual` modifikátory upravit `override` metoda.  
  
 Přepsání deklarace vlastnosti musíte zadat přesně stejný – modifikátor přístupu, typ a název jako zděděnou vlastnost a musí být vlastnost přepsaného `virtual`, `abstract`, nebo `override`.  
  
 Další informace o tom, jak používat `override` – klíčové slovo, najdete v části [Správa verzí pomocí nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad definuje základní třídu s názvem `Employee`a odvozené třídy s názvem `SalesEmployee`. `SalesEmployee` Třída obsahuje doplňující vlastnosti, `salesbonus`a přepíše metodu `CalculatePay` Chcete-li vzít v úvahu.  
  
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
