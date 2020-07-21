---
title: Modifikátory přístupu – Průvodce programováním v C#
description: Všechny typy a členy typu v jazyce C# mají úroveň přístupnosti, která určuje, zda lze použít z jiného kódu. Projděte si tento seznam modifikátorů přístupu.
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 557f5d9f302b08d32896b462e86ce1d96710ff36
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474524"
---
# <a name="access-modifiers-c-programming-guide"></a>Modifikátory přístupu (Průvodce programováním v C#)

Všechny typy a členy typu mají úroveň přístupnosti. Úroveň přístupnosti řídí, zda lze použít z jiného kódu v sestavení nebo v jiných sestaveních. Použijte následující modifikátory přístupu k určení přístupnosti typu nebo člena při jeho deklaraci:

- [Public](../../language-reference/keywords/public.md): k typu nebo členu může být přistup jakýkoliv jiný kód ve stejném sestavení nebo jiném sestavení, které na něj odkazuje.
- [Private](../../language-reference/keywords/private.md): typ nebo člen může být k dispozici pouze pomocí kódu ve stejné `class` nebo `struct` .
- [Protected](../../language-reference/keywords/protected.md): typ nebo člen může být k dispozici pouze pomocí kódu ve stejné `class` nebo v, `class` který je odvozen z `class` .
- [interní](../../language-reference/keywords/internal.md): k typu nebo členu je možné přistupovat jakýmkoli kódem ve stejném sestavení, ale ne z jiného sestavení.
- [Protected Internal](../../language-reference/keywords/protected-internal.md): k typu nebo členu je možné přivodit libovolný kód v sestavení, ve kterém je deklarovaný, nebo z odvozeného `class` v jiném sestavení.
- [Private Protected](../../language-reference/keywords/private-protected.md): k typu nebo členu lze přivodit pouze v rámci deklarovaného sestavení, podle kódu ve stejném `class` nebo v typu, který je odvozen z `class` .

Následující příklady ukazují, jak zadat modifikátory přístupu pro typ a člen:

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

Ne všechny modifikátory přístupu jsou platné pro všechny typy nebo členy ve všech kontextech. V některých případech je přístupnost člena typu omezená přístupností jeho nadřazeného typu.

## <a name="class-and-struct-accessibility"></a>Přístupnost třídy a struktury  

Třídy a struktury deklarované přímo v rámci oboru názvů (jinými slovy, které nejsou vnořené v jiných třídách nebo strukturách) mohou být `public` nebo `internal` . `Internal`je výchozí, pokud není zadán modifikátor přístupu.  

Členy struktury, včetně vnořených tříd a struktur, lze deklarovat `public` , `internal` nebo `private` . Členy třídy, včetně vnořených tříd a struktur, mohou být `public` , `protected internal` ,,, `protected` `internal` `private protected` nebo `private` . Členy třídy a struktury, včetně vnořených tříd a struktur, mají `private` ve výchozím nastavení přístup. Soukromé vnořené typy nejsou přístupné z vnějšku nadřazeného typu.

Odvozené třídy nemůžou mít větší přístupnost než jejich základní typy. Nelze deklarovat veřejnou třídu `B` , která je odvozena z interní třídy `A` . Pokud je to povoleno, by mělo mít vliv na `A` veřejné, protože všichni `protected` nebo `internal` Členové `A` jsou k dispozici z odvozené třídy.

Můžete povolit konkrétní jiná sestavení pro přístup k interním typům pomocí `InternalsVisibleToAttribute` . Další informace naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).

## <a name="class-and-struct-member-accessibility"></a>Přístupnost třídy a člena struktury  

Členy třídy (včetně vnořených tříd a struktur) lze deklarovat s libovolným šesti typy přístupu. Členy struktury nejde deklarovat jako `protected` , `protected internal` nebo, `private protected` protože struktury nepodporují dědění.

V normálním případě přístupnost člena nepřekračuje přístupnost typu, který ho obsahuje. Nicméně `public` člen interní třídy může být přístupný mimo sestavení, pokud člen implementuje metody rozhraní nebo přepíše virtuální metody, které jsou definovány ve veřejné základní třídě.

Typ každého pole člena, vlastnost nebo událost musí být k dispozici alespoň jako člen samotný. Podobně musí být návratový typ a typy parametrů jakékoli metody, indexeru nebo delegáta aspoň tak přístupné jako samotný člen. Například nemůžete mít `public` metodu `M` , která vrací třídu, `C` Pokud `C` není také `public` . Podobně nemůžete mít `protected` vlastnost typu, `A` Pokud `A` je deklarován jako `private` .

Uživatelem definované operátory musí být vždy deklarovány jako `public` a `static` . Další informace naleznete v tématu [přetížení operátoru](../../language-reference/operators/operator-overloading.md).

Finalizační metody nemůžou mít modifikátory dostupnosti.

Chcete-li nastavit úroveň přístupu pro `class` `struct` člena nebo, přidejte příslušné klíčové slovo do deklarace člena, jak je znázorněno v následujícím příkladu.

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>Další typy

Rozhraní deklarovaná přímo v rámci oboru názvů mohou být `public` nebo `internal` a stejně jako třídy a struktury, výchozí pro přístup k rozhraním `internal` . Členy rozhraní jsou `public` ve výchozím nastavení, protože účelem rozhraní je povolit jiným typům přístup ke třídě nebo struktuře. Deklarace členů rozhraní můžou zahrnovat jakýkoli modifikátor přístupu. To je nejužitečnější pro statické metody pro zajištění běžných implementací, které jsou vyžadovány všemi implementátori třídy.

Členy výčtu jsou vždy `public` a nelze použít žádné modifikátory přístupu.

Delegáti se chovají jako třídy a struktury. Ve výchozím nastavení mají `internal` přístup, pokud jsou deklarovány přímo v rámci oboru názvů a `private` přístup, pokud je vnořený.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Rozhraní](../interfaces/index.md)
- [hlášen](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
- [internal](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [Deník](../../language-reference/keywords/class.md)
- [nemají](../../language-reference/builtin-types/struct.md)
- [prostředí](../../language-reference/keywords/interface.md)
