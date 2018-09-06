---
title: Pole (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 708bd4e768e795397624bcac6e5bc2594bff93f5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43804739"
---
# <a name="fields-c-programming-guide"></a>Pole (Průvodce programováním v C#)
A *pole* je proměnná typu, který je deklarován přímo v [třídy](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md). Pole jsou *členy* z jeho nadřazeného typu.  
  
 Třídy nebo struktury může mít pole instance nebo statické pole nebo obojí. Pole instancí jsou specifická pro instanci typu. Máte-li třída T, s poli instance F, můžete vytvořit dva objekty typu T a hodnotu F jednotlivých objektů změnit, aniž by to ovlivnilo hodnoty v jiných objektu. Statické pole naopak patří k samotné třídě a je sdílena mezi všemi instancemi třídy. Změny provedené v instance se okamžitě viditelně k instancím B a C Pokud budou přistupovat k poli.  
  
 Obecně platí by měl použít pole pouze pro proměnné, které mají soukromé nebo chráněné usnadnění. Data, která poskytuje třídu pro klientský kód by měl být zajišťována [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md) a [indexery](../../../csharp/programming-guide/indexers/index.md). Pomocí těchto konstruktorů pro nepřímý přístup k interní pole je pomáhalo chránit před neplatné vstupní hodnoty. Je volána soukromé pole, která ukládá data vystavená prostřednictvím veřejné vlastnosti *záložní úložiště* nebo *pomocné pole*.  
  
 Pole jsou obvykle ukládá data, která musí být přístupný pro více než jednu metodu třídy a musíte uložit na déle než životnost libovolné jedinou metodu. Například třída, která představuje datum kalendáře může mít tři pole typu integer: jeden pro měsíc, jeden pro den a jeden rok. Proměnné, které se používá mimo obor jedné metody by měly být deklarovány jako *lokální proměnné* v metodě samotného textu.  
  
 Pole jsou deklarovány v bloku třídy tak, že zadáte úroveň přístupu pole, za nímž následuje typ pole, za nímž následuje název pole. Příklad:  
  
 [!code-csharp[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]  
  
 Chcete-li přístup k poli v objektu, přidejte tečku za názvem objektu zadán spolu s názvem pole, stejně jako v `objectname.fieldname`. Příklad:  
  
 [!code-csharp[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]  
  
 Pole může dostat počáteční hodnotu použitím operátoru přiřazení při deklaraci pole. Automaticky přiřadit `day` pole `"Monday"`, například by deklarovat `day` jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]  
  
 Pole jsou inicializována bezprostředně před volání konstruktoru pro instanci objektu. Pokud konstruktor přiřadí hodnotu pole, přepíše libovolný zadaný při deklaraci pole. Další informace najdete v tématu [pomocí konstruktorů](../../../csharp/programming-guide/classes-and-structs/using-constructors.md).  
  
> [!NOTE]
>  Inicializátor pole nemůže odkazovat na jiné pole instance.  
  
 Pole může být označený jako [veřejné](../../../csharp/language-reference/keywords/public.md), [privátní](../../../csharp/language-reference/keywords/private.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [interní chráněné](../../../csharp/language-reference/keywords/protected-internal.md) nebo [private, protected](../../../csharp/language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definují, jak třídy mohou uživatelé pole. Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Pole lze deklarovat volitelně [statické](../../../csharp/language-reference/keywords/static.md). Díky tomu pole k dispozici pro volající kdykoli, i v případě, že neexistuje žádná instance třídy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Pole mohou být deklarovány [jen pro čtení](../../../csharp/language-reference/keywords/readonly.md). Pole jen pro čtení je možné přiřadit pouze hodnotu během inicializace nebo v konstruktoru. A `static readonly` pole je velmi podobný konstantu, s tím rozdílem, že kompilátor jazyka C# nemá přístup k hodnotě statické pole jen pro čtení v době kompilace, pouze v době běhu. Další informace najdete v tématu [konstanty](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Použití konstruktorů](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
- [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
- [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [Abstraktní a uzavřené třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
