---
title: new – modifikátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: b66cfacc2203e0e529c19b5c566abad6c676f149
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273965"
---
# <a name="new-modifier-c-reference"></a>new – modifikátor (Referenční dokumentace jazyka C#)
Když se použije jako modifikátor deklarace, `new` – klíčové slovo explicitně skryje člena, který je zděděn ze základní třídy. Skrytí zděděného členu odvozenou verzí člena nahradí verzi základní třídy. I když můžete skrýt členy, bez použití `new` modifikátor, zobrazí se upozornění kompilátoru. Pokud používáte `new` explicitně skrýt členem, potlačí toto upozornění.  
  
 Skrýt zděděného členu, deklarovat v odvozené třídě za použití stejného názvu člen a upravit ho pomocí `new` – klíčové slovo. Příklad:  
  
 [!code-csharp[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 V tomto příkladu `BaseC.Invoke` je skrytý na základě `DerivedC.Invoke`. Pole `x` nemá vliv, protože není skryt podobným jménem.  
  
 Název skrytí prostřednictvím dědičnosti má jednu z následujících podob:  
  
-   Obecně platí konstanta, pole, vlastnost nebo typ, který byl představen v třídě nebo struktuře skryje všechny členy základní třídy, které jeho název sdílené složky.  Existují zvláštní případy.  Například, pokud je deklarovat nové pole s názvem `N` mít typ, který není invocable a základní typ deklaruje `N` jako metodu nové pole není skrýt základní deklaraci v syntaxi volání.  Najdete v článku [specifikace jazyka C# 5.0](https://www.microsoft.com/download/details.aspx?id=7029) podrobnosti (viz část "Člen vyhledávání" v části "Výrazy").  
  
-   Metoda byla zavedená v třídě nebo struktuře skryje vlastnosti, pole a typy, které sdílejí tento název v základní třídě. Skryje také všechny metody třídy base, které mají stejným podpisem.  
  
-   Indexer byla zavedená v třídě nebo struktuře skryje všechny základní třídy indexery, které mají stejným podpisem.  
  
 Jedná se o chybu použití `new` a [přepsat](../../../csharp/language-reference/keywords/override.md) na stejného člena, protože mají dva modifikátory vzájemně se vylučuje významy. `new` Modifikátor vytvoří nový člen se stejným názvem a způsobí, že původní člen stát skryté. `override` Modifikátor rozšiřuje implementaci pro zděděného členu.  
  
 Pomocí `new` modifikátor v deklaraci, která není skrýt zděděného členu vygeneruje upozornění.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu základní třídu, `BaseC`a odvozené třídy `DerivedC`, použijte stejný název pole `x`, která skryje hodnotu zděděné pole. Příklad ukazuje použití `new` modifikátor. Také ukazuje, jak skrytý členy základní třídy přistupovat pomocí jejich plně kvalifikované názvy.  
  
 [!code-csharp[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu vnořené třídy skryje třídu, která má stejný název v základní třídě. Příklad ukazuje, jak používat `new` modifikátor eliminovat upozornění a přístupu k členům skrytá třídy pomocí jejich plně kvalifikované názvy.  
  
 [!code-csharp[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 Pokud odeberete `new` modifikátor, program stále zkompilování a spuštění, ale zobrazí se následující upozornění:  
  
```  
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.  
```  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Správa verzí pomocí klíčových slov override a new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [Znalost, kdy použít klíčová slova override a new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
