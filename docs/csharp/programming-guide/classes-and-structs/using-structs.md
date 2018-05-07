---
title: Použití struktur (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 553a6d1d2e922d1683cb5dbe2fa0b525c9b1e37a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-structs-c-programming-guide"></a>Použití struktur (Průvodce programováním v C#)
`struct` Typ je vhodný pro zjednodušené objekty, jako představující `Point`, `Rectangle`, a `Color`. I když je jenom pohodlný představuje bod jako [třída](../../../csharp/language-reference/keywords/class.md) s [Auto-Implemented vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), [struktura](../../../csharp/language-reference/keywords/struct.md) může být v některých scénářích efektivnější. Například, pokud je deklarovat pole 1000 `Point` objekty, pro odkazování na každém objektu; v tomto případě se bude přidělit další paměť, bude levnější struktury. Protože [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] obsahuje objektu s názvem <xref:System.Drawing.Point>, struktura v tomto příkladu je s názvem "CoOrds" místo.  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 Jedná se o chybu definovat výchozí konstruktor pro struktury (bez parametrů). Je také k chybě inicializace poli instance v struktura textu. Externě dostupný struktura členy můžete inicializovat pouze pomocí parametrizované konstruktor, implicitní, výchozí konstruktor, [inicializátoru objektu](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md), nebo přímým přístupem členy jednotlivě po struct je deklarován. Žádné členy privátní nebo jinak nedostupná výhradně vyžadují použití konstruktory.
  
 Při vytváření objektu struktura pomocí [nové](../../../csharp/language-reference/keywords/new.md) operátor, se vytvoří a vhodný konstruktor se nazývá podle [podpis konstruktoru](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax). Na rozdíl od třídy, struktury se dá vytvořit instance bez použití `new` operátor. V takovém případě není žádný konstruktor volání, které umožňuje efektivnější přidělení. Ale zůstane nepřiřazené pole a objektu nelze použít, dokud se neinicializuje všechna pole. To zahrnuje nemožnost získání nebo nastavení hodnoty prostřednictvím automaticky implementované vlastnosti.
 
 Pokud vytvoříte instanci objektu struktura pomocí výchozí, konstruktor bez parametrů, všichni členové jsou přiřazené podle jejich [výchozí hodnoty](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md).
  
 Při zápisu konstruktor s parametry, struktury, je třeba explicitně inicializovat všichni členové; jinak zůstanou nepřiřazené jednoho nebo více členů a struct nelze použít, který vytvořil Chyba kompilátoru CS0171.  
  
 Není žádná dědičnost pro struktury, protože se pro třídy. Struktury nemůže Zdědit z jiné třídy nebo struktury a nesmí být základní třídy. Struktury, ale dědění ze základní třídy <xref:System.Object>. Struktury můžete implementovat rozhraní, a tak činí přesně stejně jako třídy.  
  
 Nelze deklarovat třídy pomocí klíčového slova `struct`. V jazyce C# jsou sémanticky různých tříd a struktur. Struktury je typ hodnoty, zatímco třída je typu odkazu. Další informace najdete v tématu [typy hodnot](../../../csharp/language-reference/keywords/value-types.md).  
  
 Pokud potřebujete Sémantika typu odkazu, třídu malé může efektivněji zpracovávat systému deklarujete ho jako struktury místo.  
  
## <a name="example-1"></a>Příklad 1  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje `struct` inicializace pomocí výchozí a parametrizované konstruktory.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]  
  
## <a name="example-2"></a>Příklad 2  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje funkce, které jsou jedinečné pro struktury. Vytvoří objekt CoOrds bez použití `new` operátor. Pokud nahradíte slovo `struct` slovem `class`, nebude kompilace programu.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)
