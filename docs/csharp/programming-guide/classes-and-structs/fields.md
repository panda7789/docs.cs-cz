---
title: Pole (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 31073772fd42244167b5e68959ebb373ec759025
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314324"
---
# <a name="fields-c-programming-guide"></a>Pole (Průvodce programováním v C#)
A *pole* je proměnná typu, který je deklarován přímo v [třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md). Pole jsou *členy* jejich obsahující typu.  
  
 Třídě nebo struktuře může mít pole instance nebo statické pole. Pole instance jsou specifické pro instanci typu. Pokud máte třídu T, s poli instance F, můžete vytvořit dva objekty typu t. a upravit je hodnota F v každém objektu bez ovlivnění hodnotu v druhý objekt. Naopak statické pole patří do vlastní třídy, je sdílen mezi všechny instance této třídy. Změny provedené z instance bude viditelně okamžitě k instancím B a C Pokud budou přistupovat k poli.  
  
 Obecně platí měli byste použít pole pouze pro proměnné, které mají soukromé nebo chráněné usnadnění. Data, která vystavuje třídě kódu klienta by měl být zajišťováno prostřednictvím [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md) a [indexery](../../../csharp/programming-guide/indexers/index.md). Pomocí těchto konstrukce pro nepřímý přístup k interní pole můžete chránit před neplatné vstupní hodnoty. Je volána soukromé pole, která ukládá data vystavené veřejné vlastnosti *záložnímu úložišti* nebo *základní pole*.  
  
 Pole obvykle ukládání dat, která musí být přístupný pro více než jedna metoda třídy a musí být uložen po dobu delší než životnost žádné jedné metody. Například třída, která představuje datum kalendáře může mít tři pole celé číslo: jeden pro měsíc, jeden pro den a jeden v roce. Proměnné, které nepoužívají mimo obor jedné metody musí být deklarována jako *místní proměnné* v rámci metody body sám sebe.  
  
 Pole jsou deklarované v bloku třída zadáním úroveň přístupu tohoto pole, za nímž následuje typ pole, za nímž následuje název pole. Příklad:  
  
 [!code-csharp[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]  
  
 Chcete-li přístup k poli v objektu, přidejte dobu, po název objektu, za nímž následuje název pole, jako v `objectname.fieldname`. Příklad:  
  
 [!code-csharp[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]  
  
 Pole lze zadat počáteční hodnotu pomocí operátor přiřazení, pokud je toto pole deklarovat. Automaticky přiřadit `day` do `"Monday"`, například by deklarovat `day` jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]  
  
 Pole se inicializují bezprostředně před volání konstruktoru pro instanci objektu. Pokud konstruktoru přiřadí hodnotu pole, přepíše se hodnotou zadané během deklaraci pole. Další informace najdete v tématu [pomocí konstruktorů](../../../csharp/programming-guide/classes-and-structs/using-constructors.md).  
  
> [!NOTE]
>  Inicializátoru pole nelze odkazovat na další pole instance.  
  
 Pole může být označen jako [veřejné](../../../csharp/language-reference/keywords/public.md), [privátní](../../../csharp/language-reference/keywords/private.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [chráněné interní](../../../csharp/language-reference/keywords/protected-internal.md) nebo [privátní chráněné](../../../csharp/language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definovat třídy pro přístup uživatelů pole. Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Pole lze volitelně deklarovat [statické](../../../csharp/language-reference/keywords/static.md). Díky pole pro volající kdykoli, i v případě, že neexistuje žádná instance třídy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Pole lze deklarovat [jen pro čtení](../../../csharp/language-reference/keywords/readonly.md). Pole jen pro čtení můžete přiřadit pouze hodnotu během inicializace nebo v konstruktoru. A `static``readonly` pole je velmi podobný konstantu, s tím rozdílem, že kompilátor jazyka C# nemá přístup k hodnotě statické pole jen pro čtení v době kompilace pouze za běhu. Další informace najdete v tématu [konstanty](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Použití konstruktorů](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
 [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Abstraktní a uzavřené třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
