---
title: Pole – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 46d4f77a4a490b2acdb5da20b9a477f27c38d410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628238"
---
# <a name="fields-c-programming-guide"></a>Pole (Průvodce programováním v C#)

*Pole* je proměnná libovolného typu, která je deklarována přímo ve [třídě](../../language-reference/keywords/class.md) nebo [struktuře](../../language-reference/builtin-types/struct.md). Pole jsou *členy* jejich obsahující ho typu.

Třída nebo struktura může mít pole instancí, statická pole nebo obojí. Pole instance jsou specifická pro instanci typu. Pokud máte třídu T s polem instance F, můžete vytvořit dva objekty typu T a upravit hodnotu F v každém objektu bez ovlivnění hodnoty v druhém objektu. Naproti tomu statické pole patří do samotné třídy a je sdíleno mezi všemi instancemi této třídy. Ke statickému poli můžete přistupovat pouze pomocí názvu třídy. Pokud k statickému poli přistupujete podle názvu instance, zobrazí se chyba [cs0176](../../misc/cs0176.md) kompilace.

Obecně byste měli pole používat pouze pro proměnné, které mají privátní nebo chráněnou přístupnost. Data, která vaše třída zveřejňuje kódu klienta by měla být poskytnuta prostřednictvím [metod](./methods.md), [vlastností](./properties.md)a [indexerů](../indexers/index.md). Pomocí těchto konstrukcí pro nepřímý přístup k interním polím můžete chránit před neplatnými vstupními hodnotami. Soukromé pole, které ukládá data vystavená veřejnou vlastností, se nazývá *záložní úložiště* nebo *záložní pole*.

Pole obvykle ukládají data, která musí být přístupná více než jedné metodě třídy a musí být uložena po dobu delší než životnost jedné metody. Například třída, která představuje kalendářní datum, může mít tři celočíselná pole: jedno pro měsíc, jedno pro den a jedno pro rok. Proměnné, které nejsou použity mimo rozsah jedné metody by *měly* být deklarovány jako místní proměnné v rámci samotného těla metody.

Pole jsou deklarována v bloku třídy zadáním úrovně přístupu pole, následovanou typem pole následovaným názvem pole. Například:

[!code-csharp[csProgGuideObjects#61](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#61)]

Chcete-li získat přístup k poli v objektu, přidejte za název objektu tečku následovanou názvem pole, například v . `objectname.fieldname` Například:

[!code-csharp[csProgGuideObjects#62](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#62)]

Pole může být poskytnuta počáteční hodnota pomocí operátoru přiřazení při deklarace pole. Chcete-li `day` pole `"Monday"`automaticky přiřadit , byste `day` například deklarovali jako v následujícím příkladu:

[!code-csharp[csProgGuideObjects#63](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#63)]

Pole jsou inicializována bezprostředně před voláním konstruktoru pro instanci objektu. Pokud konstruktor přiřadí hodnotu pole, přepíše libovolnou hodnotu uvedenou během deklarace pole. Další informace naleznete [v tématu Using Constructors](./using-constructors.md).

> [!NOTE]
> Inicializátor pole nemůže odkazovat na jiná pole instance.

Pole mohou být označena jako [veřejná](../../language-reference/keywords/public.md), [soukromá](../../language-reference/keywords/private.md), [chráněná](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněná interní](../../language-reference/keywords/protected-internal.md)nebo [soukromá chráněná](../../language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definují, jak mohou uživatelé třídy přistupovat k polím. Další informace naleznete [v tématu Access Modifiers](./access-modifiers.md).

Pole může být volitelně prohlášeno za [statické](../../language-reference/keywords/static.md). To zpřístupňuje pole volajícím kdykoli, i v případě, že neexistuje žádná instance třídy. Další informace naleznete [v tématu Statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).

Pole lze deklarovat [pouze pro čtení](../../language-reference/keywords/readonly.md). Pole jen pro čtení lze přiřadit pouze hodnotu během inicializace nebo v konstruktoru. Pole `static readonly` je velmi podobné konstantě s tím rozdílem, že kompilátor jazyka C# nemá přístup k hodnotě statického pole jen pro čtení v době kompilace, pouze za běhu. Další informace naleznete v [tématu Konstanty](./constants.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Použití konstruktorů](./using-constructors.md)
- [Dědičnost](./inheritance.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Abstraktní a uzavřené třídy a jejich členové](./abstract-and-sealed-classes-and-class-members.md)
