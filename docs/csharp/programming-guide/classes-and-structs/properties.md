---
title: Vlastnosti (Průvodce programováním v C#)
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: 47f8e978d81b4aec94482f0a295691b830c3698c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="properties-c-programming-guide"></a>Vlastnosti (Průvodce programováním v C#)

Vlastnost je člena, který poskytuje flexibilní mechanismus pro čtení, zápisu nebo výpočtu hodnoty soukromé pole. Vlastnosti můžete použít stejně, jako jsou členy veřejná data, ale jsou ve skutečnosti speciální metody názvem *přístupové objekty*. To umožňuje data nelze snadno přistupovat a přesto pomáhá zvýšit úroveň zabezpečení a flexibility metod.  

## <a name="properties-overview"></a>Přehled vlastností  
  
- Vlastnosti Povolit třídu vystavit veřejné způsob získání a nastavení hodnoty, při skrytí kódu implementace nebo ověření.  
  
- A [získat](../../../csharp/language-reference/keywords/get.md) přistupujícího objektu vlastnosti se používá k vrácení hodnotu vlastnosti a [nastavit](../../../csharp/language-reference/keywords/set.md) přistupujícího objektu vlastnosti slouží k přiřazení nové hodnoty. Tyto přístupové objekty může mít různé úrovně přístupu. Další informace najdete v tématu [omezení přístupnosti přistupujícího objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
- [Hodnotu](../../../csharp/language-reference/keywords/value.md) – klíčové slovo se používá k definování přiřazené podle `set` přistupujícího objektu.  
- Vlastnosti mohou být *pro čtení a zápis* (mají obě `get` a `set` přistupujícího objektu), *jen pro čtení* (mají `get` přistupujícího objektu, ale ne `set` přistupujícího objektu), nebo *jen pro zápis* (mají `set` přistupujícího objektu, ale ne `get` přistupujícího objektu). Vlastnosti jen pro zápis vyskytují jen vzácně a jsou nejčastěji používá k omezení přístupu k citlivým datům.

- Jednoduché vlastnosti, které vyžadují žádný kód vlastní přistupující objekt můžete implementovat buď jako výraz text definice nebo [automaticky implementované vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).
 
## <a name="properties-with-backing-fields"></a>Vlastnosti s zálohování pole

Jeden základní vzor pro implementaci vlastnost, která využívá privátní základní pole pro nastavení nebo načtení hodnoty vlastnosti. `get` Přistupujícího objektu vrátí hodnotu pole privátní a `set` přistupující objekt může provádět některé ověření dat před přiřazením hodnoty soukromé pole. Obě přístupových objektů může také provést některé převod nebo výpočetní na data předtím, než je uložen nebo vrácena.

Následující příklad ilustruje tohoto vzoru. V tomto příkladu `TimePeriod` třída reprezentuje časový interval. Interně třída ukládá časový interval v sekundách v soukromé pole s názvem `seconds`. Čtení a zápis vlastnost s názvem `Hours` umožňuje zákazníkovi, zadejte časový interval v hodinách. Jak `get` a `set` přístupových objektů proveďte potřebné převod mezi hodiny a sekundy. Kromě toho `set` přistupujícího objektu ověří data a způsobí výjimku, <xref:System.ArgumentOutOfRangeException> Pokud počet hodin, je neplatný. 
   
 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>Výraz definice textu  

 Přístupové objekty vlastnosti často obsahovat jeden řádek příkazy, které právě přiřadit nebo vrátit výsledek výrazu. Tyto vlastnosti můžete implementovat jako výraz vozidlo členy. Výraz definice textu skládat z `=>` následuje výraz, který se přiřadit nebo načíst z vlastnosti.

 Od verze jazyka C# 6, můžete implementovat vlastnosti jen pro čtení `get` přistupujícího objektu jako výraz vozidlo člena. V takovém případě, ani `get` – klíčové slovo přistupujícího objektu ani `return` – klíčové slovo se používá. Následující příklad implementuje jen pro čtení `Name` vlastnost jako výraz vozidlo člena.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 Od verze jazyka C# 7.0, jak `get` a `set` přistupujícího objektu se dají implementovat jako výraz vozidlo členy. V takovém případě `get` a `set` klíčová slova musí být přítomen. Následující příklad ukazuje použití výraz text definice pro obě přistupující objekty. Všimněte si, že `return` – klíčové slovo se nepoužívá `get` přistupujícího objektu.
 
  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Automaticky implementované vlastnosti

V některých případech vlastnost `get` a `set` přístupové objekty právě přidělíte hodnotu nebo načtení hodnoty z pole zálohování bez zahrnutí veškeré další logiky. Pomocí automaticky implementované vlastnosti můžete zjednodušit kód přitom má transparentně zadejte pole Základní kompilátor jazyka C#. 

Pokud má vlastnost oba `get` a `set` přistupujícího objektu, musí být oba automaticky implementované. Definovat ve automaticky implementované vlastnosti pomocí `get` a `set` klíčová slova bez zadání žádnou implementaci. V následujícím příkladu se opakuje předchozímu, vyjma toho, že `Name` a `Price` jsou automaticky implementované vlastnosti. Poznámka: Tento příklad také odebere parametrizované konstruktoru, tak, aby `SaleItem` objekty jsou nyní inicializována pomocí volání výchozí konstruktor a [inicializátoru objektu](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>Související oddíly  
  
-   [Použití vlastností](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Vlastnosti rozhraní](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Porovnání mezi vlastnostmi a indexery](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Omezení přístupnosti přístupového objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [Automaticky implementované vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Použití vlastností](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Indexery](../../../csharp/programming-guide/indexers/index.md)  
 [Get – klíčové slovo](../../../csharp/language-reference/keywords/get.md)    
 [set – klíčové slovo](../../../csharp/language-reference/keywords/set.md)    
