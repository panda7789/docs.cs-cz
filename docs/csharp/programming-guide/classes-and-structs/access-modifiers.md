---
title: Modifikátory přístupu – programovací příručka jazyka C#
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 749d53344a2518966cfa5d937069ba73dfd6be8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628225"
---
# <a name="access-modifiers-c-programming-guide"></a>Modifikátory přístupu (Průvodce programováním v C#)

Všechny typy a členy typu mají úroveň usnadnění. Úroveň usnadnění řídí, zda je lze použít z jiného kódu v sestavení nebo jiných sestaveních. Pomocí následujících modifikátorů přístupu určete usnadnění přístupu typu nebo člena při deklarování:

- [Public](../../language-reference/keywords/public.md): Typ nebo člen lze přistupovat libovolný jiný kód ve stejném sestavení nebo jiné sestavení, které odkazuje na něj.
- [private](../../language-reference/keywords/private.md): Typ nebo člen lze přistupovat pouze `class` `struct`pomocí kódu ve stejném nebo .
- [chráněno](../../language-reference/keywords/protected.md): Typ nebo člen lze přistupovat `class`pouze pomocí `class` kódu ve stejném `class`nebo v a , který je odvozen od tohoto .
- [vnitřní](../../language-reference/keywords/internal.md): Typ nebo člen lze přistupovat libovolný kód ve stejném sestavení, ale ne z jiného sestavení.
- [chráněné vnitřní](../../language-reference/keywords/protected-internal.md): Typ nebo člen lze přistupovat libovolný kód v sestavení, ve kterém `class` je deklarován, nebo z v rámci odvozené v jiném sestavení.
- [privátní :](../../language-reference/keywords/private-protected.md)Typ nebo člen lze přistupovat pouze v `class` rámci jeho deklarování sestavení, kód ve stejném nebo typu, který je odvozen od tohoto `class`.

Následující příklady ukazují, jak určit modifikátory přístupu u typu a člena:

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

Ne všechny modifikátory přístupu jsou platné pro všechny typy nebo členy ve všech kontextech. V některých případech je přístupnost člena typu omezena usnadněním jeho obsahujícího typu.

## <a name="class-and-struct-accessibility"></a>Přístupnost třídy a struktury  

Třídy a struktury deklarované přímo v oboru názvů (jinými slovy, které nejsou vnořeny do jiných tříd nebo struktur) může být buď `public` nebo `internal`. `Internal`je výchozí, pokud není zadán žádný modifikátor přístupu.  

Členy struktury, včetně vnořených tříd a `public`struktur, lze deklarovat , `internal`nebo `private`. Členy třídy, včetně vnořených tříd `public` `protected internal`a `protected` `internal`struktur, mohou být , , , , `private protected`, nebo `private`. Členové třídy a struktury, včetně vnořených `private` tříd a struktur, mají ve výchozím nastavení přístup. Soukromé vnořené typy nejsou přístupné mimo obsahující typ.

Odvozené třídy nemohou mít větší přístupnost než jejich základní typy. Nelze deklarovat veřejné `B` třídy, která `A`je odvozena z vnitřní třídy . Pokud je povoleno, by to `A` mělo za `protected` `internal` následek `A` zveřejnění, protože všechny nebo členy jsou přístupné z odvozené třídy.

Můžete povolit konkrétní další sestavení pro přístup `InternalsVisibleToAttribute`k interní typy pomocí . Další informace naleznete [v tématu Friend Assemblyies](../../../standard/assembly/friend.md).

## <a name="class-and-struct-member-accessibility"></a>Usnadnění přístupu členů třídy a struktury  

Členy třídy (včetně vnořených tříd a struktur) lze deklarovat s libovolným ze šesti typů přístupu. Členy struktury nelze deklarovat `protected internal`jako `private protected` `protected`, nebo proto, že struktury nepodporují dědičnost.

Za normálních okolností přístupnost člena není větší než usnadnění typu, který jej obsahuje. `public` Člen vnitřní třídy však může být přístupný z mimo sestavení, pokud člen implementuje metody rozhraní nebo přepíše virtuální metody, které jsou definovány ve třídě veřejné základní.

Typ libovolného členského pole, vlastnosti nebo události musí být alespoň stejně přístupný jako samotný člen. Podobně návratový typ a typy parametrů libovolné metody, indexeru nebo delegáta musí být alespoň stejně přístupné jako samotný člen. Například nemůžete mít `public` metodu, `M` která vrací `C` `C` třídu, pokud není také `public`. Podobně nemůžete `protected` mít vlastnost typu, `A` pokud `A` je deklarována jako `private`.

Uživatelem definované operátory musí `public` `static`být vždy deklarovány jako a . Další informace naleznete v tématu [Operator přetížení](../../language-reference/operators/operator-overloading.md).

Finalizační metody nemohou mít modifikátory usnadnění.

Chcete-li nastavit úroveň `class` `struct` přístupu pro člena nebo, přidejte příslušné klíčové slovo do deklarace člena, jak je znázorněno v následujícím příkladu.

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>Jiné typy

Rozhraní deklarovaná přímo v `public` `internal` rámci oboru názvů mohou být nebo, stejně jako třídy a struktury, rozhraní výchozí pro `internal` přístup. Členové rozhraní `public` jsou ve výchozím nastavení, protože účelem rozhraní je umožnit jiné typy pro přístup ke třídě nebo struktuře. Deklarace členů rozhraní mohou obsahovat libovolný modifikátor přístupu. To je nejužitečnější pro statické metody poskytnout běžné implementace potřebné pro všechny implementátory třídy.

Členy výčtu `public`jsou vždy a nelze použít žádné modifikátory přístupu.

Delegáti se chovají jako třídy a struktury. Ve výchozím nastavení `internal` mají přístup při deklarované přímo v rámci oboru názvů a `private` přístup při vnoření.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Rozhraní](../interfaces/index.md)
- [Soukromé](../../language-reference/keywords/private.md)
- [Veřejné](../../language-reference/keywords/public.md)
- [Vnitřní](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [Třída](../../language-reference/keywords/class.md)
- [Struct](../../language-reference/builtin-types/struct.md)
- [Rozhraní](../../language-reference/keywords/interface.md)
