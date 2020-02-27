---
title: Pole – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 46d4f77a4a490b2acdb5da20b9a477f27c38d410
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628238"
---
# <a name="fields-c-programming-guide"></a>Pole (Průvodce programováním v C#)

*Pole* je proměnná libovolného typu, který je deklarován přímo ve [třídě](../../language-reference/keywords/class.md) nebo [struktuře](../../language-reference/builtin-types/struct.md). Pole jsou *členy* jejich nadřazeného typu.

Třída nebo struktura může mít pole instance, statická pole nebo obojí. Pole instance jsou specifická pro instanci typu. Máte-li třídu T s polem instance F, můžete vytvořit dva objekty typu T a upravit hodnotu F v každém objektu, aniž by to ovlivnilo hodnotu v jiném objektu. Naproti tomu statické pole patří do samotné třídy a je sdíleno mezi všemi instancemi této třídy. Ke statickému poli můžete přistupovat pouze pomocí názvu třídy. Pokud ke statickému poli přistupujete pomocí názvu instance, získáte [CS0176](../../misc/cs0176.md) chybu při kompilaci.

Obecně platí, že byste měli používat pole jenom pro proměnné, které mají privátní nebo chráněné přístupnost. Data, která vaše třída zveřejňuje klientským kódem, by měla být poskytnuta prostřednictvím [metod](./methods.md), [vlastností](./properties.md)a [indexerů](../indexers/index.md). Pomocí těchto konstrukcí pro nepřímý přístup k interním polím můžete chránit proti neplatným vstupním hodnotám. Soukromé pole, ve kterém jsou uložena data vystavená veřejnou vlastností, se nazývá *záložní úložiště* nebo *pole zálohování*.

Pole obvykle ukládají data, která musí být přístupná pro více než jednu metodu třídy a musí být uložena po dobu delší, než je doba života jakékoli jediné metody. Například třída, která představuje kalendářní datum, může mít tři celočíselná pole: jednu pro měsíc, jednu pro den a jednu pro rok. Proměnné, které se nepoužívají mimo rozsah jediné metody, by měly být deklarovány jako *lokální proměnné* v rámci samotného těla metody.

Pole jsou deklarována v bloku třídy zadáním úrovně přístupu pole následovaný typem pole následovaným názvem pole. Příklad:

[!code-csharp[csProgGuideObjects#61](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#61)]

Chcete-li získat přístup k poli v objektu, přidejte tečku za název objektu následovaný názvem pole, jak je uvedeno v `objectname.fieldname`. Příklad:

[!code-csharp[csProgGuideObjects#62](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#62)]

Poli lze předávat počáteční hodnotu pomocí operátoru přiřazení při deklaraci pole. Chcete-li automaticky přiřadit pole `day` jako `"Monday"`, například byste deklarovali `day` jako v následujícím příkladu:

[!code-csharp[csProgGuideObjects#63](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#63)]

Pole jsou inicializována bezprostředně před voláním konstruktoru pro instanci objektu. Pokud konstruktor přiřadí hodnotu pole, přepíše se jakákoli hodnota zadaná během deklarace pole. Další informace najdete v tématu [Použití konstruktorů](./using-constructors.md).

> [!NOTE]
> Inicializátor pole nemůže odkazovat na jiná pole instance.

Pole mohou být označena jako [Veřejná](../../language-reference/keywords/public.md), [soukromá](../../language-reference/keywords/private.md), [chráněná](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněná interní](../../language-reference/keywords/protected-internal.md)nebo [soukromá](../../language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definují, jak budou uživatelé třídy mít přístup k polím. Další informace najdete v tématu [modifikátory přístupu](./access-modifiers.md).

Pole může být volitelně deklarováno jako [static](../../language-reference/keywords/static.md). Tím je pole dostupné volajícím kdykoli, i když žádná instance třídy neexistuje. Další informace naleznete v tématu [statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).

Pole může být deklarované [jen pro čtení](../../language-reference/keywords/readonly.md). Poli jen pro čtení může být přiřazena hodnota pouze během inicializace nebo v konstruktoru. `static readonly` pole je velmi podobné konstantě s tím rozdílem, že C# kompilátor nemá přístup k hodnotě statického pole jen pro čtení v době kompilace, pouze v době běhu. Další informace naleznete v tématu [konstanty](./constants.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Použití konstruktorů](./using-constructors.md)
- [Dědičnost](./inheritance.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Abstraktní a uzavřené třídy a jejich členové](./abstract-and-sealed-classes-and-class-members.md)
