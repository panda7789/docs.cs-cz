---
title: Anonymní typy – Průvodce programováním v C#
description: Anonymní typy v jazyce C# zapouzdřují sadu vlastností jen pro čtení v objektu, aniž by bylo nutné explicitně definovat typ. Kompilátor vygeneruje název.
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: ccdee1a86ab0c292721e69346cb7cedb03d4c28b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474498"
---
# <a name="anonymous-types-c-programming-guide"></a>Anonymní typy (Průvodce programováním v C#)

Anonymní typy poskytují pohodlný způsob, jak zapouzdřit sadu vlastností jen pro čtení do jednoho objektu bez nutnosti explicitně definovat typ jako první. Název typu je generován kompilátorem a není k dispozici na úrovni zdrojového kódu. Typ každé vlastnosti je odvozen kompilátorem.  
  
 Anonymní typy lze vytvořit pomocí operátoru [New](../../language-reference/operators/new-operator.md) spolu s inicializátorem objektu. Další informace o inicializátorech objektů naleznete v tématu [Inicializátory objektů a kolekcí](./object-and-collection-initializers.md).  
  
 Následující příklad ukazuje anonymní typ, který je inicializován pomocí dvou vlastností s názvem `Amount` a `Message` .  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Anonymní typy obvykle jsou používány v klauzuli [Select](../../language-reference/keywords/select-clause.md) výrazu dotazu pro vrácení podmnožiny vlastností z každého objektu ve zdrojové sekvenci. Další informace o dotazech naleznete [v tématu LINQ v jazyce C#](../../linq/index.md).  
  
 Anonymní typy obsahují jednu nebo více veřejných vlastností jen pro čtení. Žádné jiné druhy členů třídy, jako jsou metody nebo události, jsou platné. Výraz použitý k inicializaci vlastnosti nemůže být `null` , anonymní funkce nebo typu ukazatele.  
  
 Nejběžnějším scénářem je inicializace anonymního typu s vlastnostmi z jiného typu. V následujícím příkladu Předpokládejme, že existuje třída s názvem `Product` . Třída `Product` zahrnuje `Color` a `Price` vlastnosti spolu s dalšími vlastnostmi, které vás zajímají. Proměnná `products` je kolekcí `Product` objektů. Deklarace anonymního typu začíná `new` klíčovým slovem. Deklarace inicializuje nový typ, který používá pouze dvě vlastnosti `Product` . To způsobí, že se v dotazu vrátí menší množství dat.  
  
 Pokud v anonymním typu nezadáte názvy členů, kompilátor poskytne členům anonymního typu stejný název jako vlastnost, která je použita k jejich inicializaci. Je nutné zadat název vlastnosti, která je inicializována výrazem, jak je znázorněno v předchozím příkladu. V následujícím příkladu jsou názvy vlastností anonymního typu `Color` a `Price` .  
  
 [!code-csharp[csRef30Features#81](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csRef30Features/CS/csref30.cs#81)]  
  
 Obvykle při použití anonymního typu k inicializaci proměnné, deklarujete proměnnou jako implicitně typovou místní proměnnou pomocí [var](../../language-reference/keywords/var.md). V deklaraci proměnné nelze zadat název typu, protože k podkladovému názvu anonymního typu má přístup pouze kompilátor. Další informace o naleznete `var` v tématu [implicitně typované lokální proměnné](./implicitly-typed-local-variables.md).  
  
 Pole anonymně typovaného prvku lze vytvořit kombinací implicitní typové místní proměnné a implicitně typovaného pole, jak je znázorněno v následujícím příkladu.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Poznámky  
 Anonymní typy jsou typy [třídy](../../language-reference/keywords/class.md) , které jsou odvozeny přímo z [objektu](../../language-reference/builtin-types/reference-types.md)a které nelze přetypovat na libovolný typ s výjimkou [Object](../../language-reference/builtin-types/reference-types.md). Kompilátor poskytuje název pro každý anonymní typ, přestože aplikace k němu nemá přístup. Z perspektivy modulu CLR (Common Language Runtime) se anonymní typ neliší od žádného jiného typu odkazu.  
  
 Pokud dva nebo více inicializátorů anonymních objektů v sestavení určují sekvenci vlastností, které jsou ve stejném pořadí a mají stejné názvy a typy, kompilátor považuje objekty za instance stejného typu. Sdílejí stejné informace typu vygenerované kompilátorem.  
  
 Nemůžete deklarovat pole, vlastnost, událost ani návratový typ metody jako anonymní typ. Podobně nelze deklarovat formální parametr metody, vlastnosti, konstruktoru nebo indexeru jako typ, který je typu anonymní. Pro předání anonymního typu nebo kolekce, která obsahuje anonymní typy jako argument metody, lze parametr deklarovat jako objekt typu. To však vede k přepsání účelu silného typování. Pokud je nutné uložit výsledky dotazu nebo je předat mimo hranice metody, zvažte použití obyčejné pojmenované struktury nebo třídy namísto anonymního typu.  
  
 Vzhledem k <xref:System.Object.Equals%2A> tomu <xref:System.Object.GetHashCode%2A> , že metody a na anonymních typech jsou definovány s ohledem na `Equals` `GetHashCode` metody a vlastností, jsou dvě instance stejného anonymního typu stejné pouze v případě, že jsou všechny jejich vlastnosti stejné.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Inicializátory objektu a kolekce](./object-and-collection-initializers.md)
- [Začínáme s dotazy LINQ v jazyce C#](../concepts/linq/index.md)
- [LINQ v jazyku C#](../../linq/index.md)
