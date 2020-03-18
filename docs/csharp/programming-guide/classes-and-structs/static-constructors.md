---
title: Statické konstruktory – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 744bcacbc38299c0ef7d16e814c415ec5caf95dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170114"
---
# <a name="static-constructors-c-programming-guide"></a>Statické konstruktory (Průvodce programováním v C#)
Statický konstruktor se používá k inicializaci [všech statických](../../language-reference/keywords/static.md) dat nebo k provedení určité akce, kterou je třeba provést pouze jednou. Je volána automaticky před vytvořením první instance nebo jsou odkazovány na statické členy.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  

## <a name="remarks"></a>Poznámky
Statické konstruktory mají následující vlastnosti:  
  
- Statický konstruktor nepřijímá modifikátory přístupu nebo má parametry.  

- Třída nebo struktura může mít pouze jeden statický konstruktor.

- Statické konstruktory nelze zdědit nebo přetížené.

- Statický konstruktor nelze volat přímo a je určen pouze pro volání clr (common language runtime). Je vyvolána automaticky.

- Uživatel nemá žádnou kontrolu nad tím, kdy je statický konstruktor spuštěn v programu.
  
- Statický konstruktor je volán automaticky k inicializaci [třídy](../../language-reference/keywords/class.md) před vytvořením první instance nebo jsou odkazovány na statické členy. Statický konstruktor bude spuštěn před konstruktorem instance. Statický konstruktor typu je volán, když je vyvolána statická metoda přiřazená události nebo delegátovi, nikoli při jeho přiřazení. Pokud statické pole proměnné inicializátory jsou přítomny ve třídě statickékonstruktor, budou provedeny v textovém pořadí, ve kterém se zobrazí v deklaraci třídy bezprostředně před spuštěním statického konstruktoru.

- Pokud nezadáte statický konstruktor pro inicializaci statických polí, všechna statická pole jsou inicializována na výchozí hodnotu uvedenou v [výchozích hodnotách typů Jazyka C#](../../language-reference/builtin-types/default-values.md).
  
- Pokud statický konstruktor vyvolá výjimku, runtime ji nevyvolá podruhé a typ zůstane neinicializován po dobu životnosti domény aplikace, ve které je program spuštěn. Nejčastěji je <xref:System.TypeInitializationException> vyvolána výjimka, když statický konstruktor není schopen vytvořit instanci typu nebo pro neošetřenou výjimku, ke které dochází v rámci statického konstruktoru. Pro implicitní statické konstruktory, které nejsou explicitně definovány ve zdrojovém kódu, může řešení potíží vyžadovat kontrolu kódu zprostředkujícího jazyka (IL).

- Přítomnost statického konstruktoru zabraňuje přidání <xref:System.Reflection.TypeAttributes.BeforeFieldInit> atributu type. To omezuje optimalizaci za běhu.

- Pole deklarované jako `static readonly` může být přiřazeno pouze jako součást jeho deklarace nebo ve statickém konstruktoru. Pokud explicitní statický konstruktor není vyžadován, inicializovat statická pole na deklaraci, nikoli prostřednictvím statického konstruktoru pro lepší optimalizaci za běhu.

> [!Note]
> Ačkoli není přímo přístupné, přítomnost explicitní statický konstruktor by měl být dokumentován pomoci při řešení potíží s výjimkami inicializace.

### <a name="usage"></a>Využití

- Typické použití statických konstruktorů je, když třída používá soubor protokolu a konstruktor se používá k zápisu položek do tohoto souboru.  
- Statické konstruktory jsou také užitečné při vytváření tříd obálky pro nespravovaný kód, když konstruktor může volat metodu. `LoadLibrary`  

- Statické konstruktory jsou také vhodné místo pro vynucení kontroly za běhu na parametr typu, který nelze zkontrolovat v době kompilace pomocí omezení (Omezení parametru typu).

## <a name="example"></a>Příklad
 V tomto příkladu má třída `Bus` statický konstruktor. Při vytvoření první `Bus` instance`bus1`( ), statický konstruktor je vyvolána k inicializaci třídy. Ukázkový výstup ověří, že statický konstruktor spustí pouze jednou, `Bus` i když jsou vytvořeny dvě instance a že je spuštěn před spuštěním konstruktoru instance.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]

## <a name="c-language-specification"></a>specifikace jazyka C#
Další informace naleznete v části [Statické konstruktory](~/_csharplang/spec/classes.md#static-constructors) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Konstruktory](./constructors.md)
- [Statické třídy a jejich členové](./static-classes-and-static-class-members.md)
- [Finalizační metody](./destructors.md)
- [Pokyny pro návrh konstruktoru](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Upozornění zabezpečení - CA2121: Statické konstruktory by měly být soukromé](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
