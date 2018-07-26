---
title: new – modifikátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: b66cfacc2203e0e529c19b5c566abad6c676f149
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245567"
---
# <a name="new-modifier-c-reference"></a>new – modifikátor (Referenční dokumentace jazyka C#)
Při použití jako modifikátoru deklarace `new` – klíčové slovo explicitně skryje člena, který je zděděn ze základní třídy. Při skrytí zděděného člena, odvozená verze člena nahradí verzi základní třídy. Ačkoli můžete skrýt členy, bez použití `new` modifikátor, zobrazí se upozornění kompilátoru. Pokud používáte `new` pro explicitní skrytí člena, potlačí toto upozornění.  
  
 Chcete-li skrýt zděděného člena, deklarujte ho v odvozené třídě pomocí stejného názvu členu a upravte jej pomocí `new` – klíčové slovo. Příklad:  
  
 [!code-csharp[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 V tomto příkladu `BaseC.Invoke` je skryt `DerivedC.Invoke`. Pole `x` nemá vliv, protože není skryté podobným názvem.  
  
 Skrytí názvu prostřednictvím dědičnosti má jednu z následujících forem:  
  
-   Obecně konstanta, pole, vlastnost nebo typ, který se používá ve třídě nebo struktuře skryje všechny členy základní třídy, které sdílejí její název.  Existují zvláštní případy.  Například, pokud deklarujete novou položku s názvem `N` mít typ, který není nevyvolatelný a základní typ deklaruje `N` na metodu, nové pole neskryje základní deklaraci v syntaxi vyvolání.  Zobrazit [specifikace jazyka C# 5.0](https://www.microsoft.com/download/details.aspx?id=7029) podrobnosti (viz oddíl "Člen vyhledávání" v části "Expressions").  
  
-   Metody zavedené ve třídě nebo struktuře skryjí vlastnosti polí a typů, které sdílejí tento název v základní třídě. Skryje také všechny metody základní třídy, které mají stejnou signaturu.  
  
-   Indexer zavedený ve třídě nebo struktuře skryje všechny základní třídy indexerů, které mají stejnou signaturu.  
  
 Jedná se o chybu, chcete-li použít `new` a [přepsat](../../../csharp/language-reference/keywords/override.md) na stejný člen, protože dva Modifikátory mají vzájemně vylučují význam. `new` Modifikátor vytvoří nový člen se stejným názvem a způsobí, že původní člen bude skrytý. `override` Modifikátor rozšiřuje implementaci pro zděděného člena.  
  
 Použití `new` modifikátor v deklaraci, která neskryje zděděného člena, vygeneruje upozornění.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu základní třída `BaseC`a odvozená třída `DerivedC`, použijte stejný název pole `x`, který skryje hodnotu zděděného pole. Tento příklad ukazuje použití `new` modifikátor. Také ukazuje, jak přistupovat ke skrytým členům základní třídy pomocí jejich plně kvalifikovaných názvů.  
  
 [!code-csharp[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu vnořené třídy skryjí třídu, která má stejný název v základní třídě. Tento příklad ukazuje, jak používat `new` modifikátor k vyloučení upozornění a jak přistupovat ke skrytým členům třídy pomocí jejich plně kvalifikovaných názvů.  
  
 [!code-csharp[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 Pokud odeberete `new` modifikátor, program bude stále kompilace a spuštění, ale zobrazí se následující upozornění:  
  
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
