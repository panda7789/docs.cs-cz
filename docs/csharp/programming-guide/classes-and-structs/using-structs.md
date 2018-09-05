---
title: Použití struktur (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: ed21bf44ebcc84a20bb228f9ba152e7348abc015
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521434"
---
# <a name="using-structs-c-programming-guide"></a>Použití struktur (Průvodce programováním v C#)
`struct` Typ je vhodný pro zjednodušené objekty, jako představující `Point`, `Rectangle`, a `Color`. I když je každopádně pohodlné představuje bod jako [třídy](../../../csharp/language-reference/keywords/class.md) s [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), [struktura](../../../csharp/language-reference/keywords/struct.md) může být efektivnější v některých scénářích. Například, pokud deklarujete pole 1000 `Point` objekty, přidělí paměť navíc pro odkazování na každý objekt; v takovém, struktura bude méně nákladné. Vzhledem k tomu, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] obsahuje objektu s názvem <xref:System.Drawing.Point>, struktura v tomto příkladu má název "CoOrds" místo.  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 Jedná se o chybu, chcete-li definovat výchozí (bezparametrový) konstruktor pro struktury. Je také k chybě inicializace pole instance v těle struktury. Členy struktury zvenku přístupný lze inicializovat pouze pomocí konstruktoru s parametry, implicitní výchozí konstruktor [objektu inicializátoru](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md), nebo díky přístupu členů jednotlivě po tato struktura deklarována. Žádné soukromé nebo jinak nedostupná členy výhradně vyžadují použití konstruktory.
  
 Když vytvoříte pomocí objektu struktury [nové](../../../csharp/language-reference/keywords/new.md) operátoru, se vytvoří a odpovídající konstruktor se nazývá podle [podpis konstruktoru](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax). Na rozdíl od tříd, struktur dá vytvořit instance bez použití `new` operátor. V takovém případě není žádná volání konstruktoru, díky přidělení efektivnější. Však zůstanou nepřiřazené pole a objektu nelze použít, dokud všechna pole jsou inicializovány. To zahrnuje neschopnost získání nebo nastavení hodnoty pomocí automaticky implementovaných vlastností.
 
 Pokud vytvoříte instanci objektu struktury pomocí výchozí, konstruktor bez parametrů, všichni členové jsou přiřazeny podle jejich [výchozí hodnoty](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md).
  
 Při zápisu konstruktor s parametry pro strukturu, je nutné explicitně inicializovat všechny členy. jinak zůstanou nepřiřazené jednoho nebo více členů a struktury nelze použít, vytváření Chyba kompilátoru CS0171.  
  
 Není žádná dědičnost struktur, protože není pro třídy. Struktura nemůže dědit z jiné třídy nebo struktury a nemůže být základní třídy. Struktury, ale dědit ze základní třídy <xref:System.Object>. Struktury můžou implementovat rozhraní, a udělá to přesně stejně jako třídy.  
  
 Nelze deklarovat třídu pomocí klíčového slova `struct`. V jazyce C# třídy a struktury jsou sémanticky rozdílné. Struktura je typ hodnoty, zatímco třída je typem odkazu. Další informace najdete v tématu [hodnotách](../../../csharp/language-reference/keywords/value-types.md).  
  
 Pokud potřebujete sémantiky typu odkazu, malé třída může efektivněji ošetřit systému Pokud se deklaruje jako struktury místo.  
  
## <a name="example-1"></a>Příklad 1  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje `struct` inicializace pomocí výchozí a konstruktor s parametry.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]  
  
## <a name="example-2"></a>Příklad 2  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje funkce, která je jedinečné pro struktury. Vytvoří objekt CoOrds bez použití `new` operátor. Pokud vyměňujete slovo `struct` slovo `class`, nebude kompilovat program.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)
