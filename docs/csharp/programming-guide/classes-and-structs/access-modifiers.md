---
title: Modifikátory přístupu – C# Průvodce programováním
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 749d53344a2518966cfa5d937069ba73dfd6be8f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628225"
---
# <a name="access-modifiers-c-programming-guide"></a>Modifikátory přístupu (Průvodce programováním v C#)

Všechny typy a členy typu mají úroveň přístupnosti. Úroveň přístupnosti řídí, zda lze použít z jiného kódu v sestavení nebo v jiných sestaveních. Použijte následující modifikátory přístupu k určení přístupnosti typu nebo člena při jeho deklaraci:

- [Public](../../language-reference/keywords/public.md): k typu nebo členu může být přistup jakýkoliv jiný kód ve stejném sestavení nebo jiném sestavení, které na něj odkazuje.
- [Private](../../language-reference/keywords/private.md): k typu nebo členu lze použít pouze kód ve stejném `class` nebo `struct`.
- [Protected](../../language-reference/keywords/protected.md): k typu nebo členu lze použít pouze kód ve stejném `class`nebo v `class`, který je odvozen z tohoto `class`.
- [interní](../../language-reference/keywords/internal.md): k typu nebo členu je možné přistupovat jakýmkoli kódem ve stejném sestavení, ale ne z jiného sestavení.
- [Protected Internal](../../language-reference/keywords/protected-internal.md): k typu nebo členu je možné přistupovat jakýmkoli kódem v sestavení, ve kterém je deklarováno, nebo z odvozené `class` v jiném sestavení.
- [Private Protected](../../language-reference/keywords/private-protected.md): k typu nebo členu lze v rámci deklarovaného sestavení použít pouze kód ve stejném `class` nebo v typu, který je odvozen z tohoto `class`.

Následující příklady ukazují, jak zadat modifikátory přístupu pro typ a člen:

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

Ne všechny modifikátory přístupu jsou platné pro všechny typy nebo členy ve všech kontextech. V některých případech je přístupnost člena typu omezená přístupností jeho nadřazeného typu.

## <a name="class-and-struct-accessibility"></a>Přístupnost třídy a struktury  

Třídy a struktury deklarované přímo v rámci oboru názvů (jinými slovy, které nejsou vnořené v jiných třídách nebo strukturách) mohou být buď `public`, nebo `internal`. Pokud není zadán modifikátor přístupu, `Internal` výchozí hodnota.  

Členy struktury, včetně vnořených tříd a struktur, lze deklarovat `public`, `internal`nebo `private`. Členy třídy, včetně vnořených tříd a struktur, mohou být `public`, `protected internal`, `protected`, `internal`, `private protected`nebo `private`. Členy třídy a struktury, včetně vnořených tříd a struktur, mají ve výchozím nastavení přístup `private`. Soukromé vnořené typy nejsou přístupné z vnějšku nadřazeného typu.

Odvozené třídy nemůžou mít větší přístupnost než jejich základní typy. Nelze deklarovat `B` veřejné třídy, které jsou odvozeny z vnitřní `A`třídy. Pokud je to povoleno, bude mít účinek `A` veřejné, protože všechny `protected` nebo `internal` členové `A` jsou přístupné z odvozené třídy.

Pro přístup k interním typům pomocí `InternalsVisibleToAttribute`lze povolit konkrétní další sestavení. Další informace naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).

## <a name="class-and-struct-member-accessibility"></a>Přístupnost třídy a člena struktury  

Členy třídy (včetně vnořených tříd a struktur) lze deklarovat s libovolným šesti typy přístupu. Členy struktury nejde deklarovat jako `protected`, `protected internal`nebo `private protected`, protože struktury nepodporují dědění.

V normálním případě přístupnost člena nepřekračuje přístupnost typu, který ho obsahuje. `public` člen interní třídy však může být přístupný mimo sestavení, pokud člen implementuje metody rozhraní nebo přepíše virtuální metody, které jsou definovány ve veřejné základní třídě.

Typ každého pole člena, vlastnost nebo událost musí být k dispozici alespoň jako člen samotný. Podobně musí být návratový typ a typy parametrů jakékoli metody, indexeru nebo delegáta aspoň tak přístupné jako samotný člen. Například nemůžete mít metodu `public` `M`, která vrací `C` třídy, pokud `C` ani `public`. Podobně nemůžete mít vlastnost `protected` typu `A`, pokud je `A` deklarována jako `private`.

Uživatelem definované operátory musí být vždy deklarovány jako `public` a `static`. Další informace naleznete v tématu [přetížení operátoru](../../language-reference/operators/operator-overloading.md).

Finalizační metody nemůžou mít modifikátory dostupnosti.

Chcete-li nastavit úroveň přístupu pro člena `class` nebo `struct`, přidejte příslušné klíčové slovo do deklarace člena, jak je znázorněno v následujícím příkladu.

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>Další typy

Rozhraní deklarovaná přímo v rámci oboru názvů mohou být `public` nebo `internal` a stejně jako třídy a struktury, výchozí nastavení rozhraní `internal` přístupu. Členy rozhraní jsou ve výchozím nastavení `public`, protože účelem rozhraní je povolit jiným typům přístup ke třídě nebo struktuře. Deklarace členů rozhraní můžou zahrnovat jakýkoli modifikátor přístupu. To je nejužitečnější pro statické metody pro zajištění běžných implementací, které jsou vyžadovány všemi implementátori třídy.

Členy výčtu jsou vždy `public`a nelze použít žádné modifikátory přístupu.

Delegáti se chovají jako třídy a struktury. Ve výchozím nastavení mají přístup `internal`, pokud jsou deklarovány přímo v rámci oboru názvů a `private` přístup, pokud je vnořený.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Rozhraní](../interfaces/index.md)
- [private](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
- [internal](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/builtin-types/struct.md)
- [interface](../../language-reference/keywords/interface.md)
