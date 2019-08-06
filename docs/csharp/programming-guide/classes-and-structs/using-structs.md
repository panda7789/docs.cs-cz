---
title: Používání struktur – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 5577a5042ba77e133e3c6ee7760f7c3a4cce0537
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796583"
---
# <a name="using-structs-c-programming-guide"></a>Použití struktur (Průvodce programováním v C#)
Typ je vhodný pro reprezentaci lehkých objektů `Point`, jako `Rectangle`jsou, `Color`a. `struct` I když je to tak pohodlné, aby představovala bod jako [třídu](../../../csharp/language-reference/keywords/class.md) s [automaticky implementovanými vlastnostmi](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), [Struktura](../../../csharp/language-reference/keywords/struct.md) může být v některých scénářích efektivnější. Například pokud deklarujete pole objektů 1000 `Point` , přidělíte další paměť pro odkazování na každý objekt; v tomto případě bude struktura levnější. Vzhledem k tomu, že .NET Framework obsahuje <xref:System.Drawing.Point>objekt s názvem, struktura v tomto příkladu má místo toho název "CoOrds".  
  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 Je-li definována výchozí konstruktor (bez parametrů) pro strukturu, jedná se o chybu. Je také chyba při inicializaci pole instance v těle struktury. Členy struktury s externě přístupnými lze inicializovat pouze pomocí parametrizovaného konstruktoru, implicitního konstruktoru bez parametrů, [inicializátoru objektu](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)nebo přístupem k členům jednotlivě po deklaraci struktury. Všichni privátní nebo jinak nepřístupní členové vyžadují použití konstruktorů výhradně.
  
 Když vytvoříte objekt struktury pomocí operátoru [New](../../../csharp/language-reference/operators/new-operator.md) , vytvoří se a příslušný konstruktor se zavolá podle [signatury konstruktoru](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax). Na rozdíl od tříd lze vytvořit instanci struktur bez použití `new` operátoru. V takovém případě neexistuje žádné volání konstruktoru, což zajistí efektivnější přidělení. Pole však zůstanou Nepřiřazeno a objekt nelze použít, dokud nebudou všechna pole inicializována. To zahrnuje neschopnost získat nebo nastavit hodnoty prostřednictvím vlastností.

 Pokud vytváříte instanci objektu struct pomocí výchozího konstruktoru bez parametrů, budou všichni členové přiřazeni podle jejich [výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).
  
 Při psaní konstruktoru s parametry pro strukturu musíte explicitně inicializovat všechny členy; jinak jeden nebo více členů zůstává Nepřiřazeno a strukturu nelze použít, což vyprodukuje chybu kompilátoru CS0171.  
  
 Pro struktury neexistuje žádná dědičnost, protože pro třídy existují třídy. Struktura nemůže dědit z jiné struktury nebo třídy a nemůže být základem třídy. Struktury, ale dědí ze základní třídy <xref:System.Object>. Struktura může implementovat rozhraní a funguje stejně jako třídy.  
  
 Třídu nelze deklarovat pomocí klíčového slova `struct`. V C#, třídy a struktury jsou sémanticky odlišné. Struktura je hodnotový typ, zatímco třída je odkazový typ. Další informace naleznete v tématu [typy hodnot](../../../csharp/language-reference/keywords/value-types.md).  
  
 Pokud nepotřebujete sémantiku typu reference, malá třída může být efektivnějším způsobem zpracována systémem, pokud ji deklarujete jako strukturu.  
  
## <a name="example-1"></a>Příklad 1  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje `struct` inicializaci pomocí výchozího i parametrizovaného konstruktoru.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]  
  
## <a name="example-2"></a>Příklad 2  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje funkci, která je jedinečná pro struktury. Vytvoří objekt CoOrds bez použití `new` operátoru. Pokud nahradíte slovo `struct` `class`slovem, program nebude zkompilován.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)
