---
title: Statické konstruktory - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: f053a74fcb87971506b83ca8ca2076517ddddf56
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307108"
---
# <a name="static-constructors-c-programming-guide"></a>Statické konstruktory (Průvodce programováním v C#)
Statický konstruktor slouží k inicializaci žádný [statické](../../../csharp/language-reference/keywords/static.md) data, nebo k provedení konkrétní akce, kterou je potřeba provést pouze jednou. Je volána automaticky před první instance je vytvořena nebo jsou odkazovány jakékoli statické členy.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
 
## <a name="remarks"></a>Poznámky
Statické konstruktory mají následující vlastnosti:  
  
- Statický konstruktor není trvat modifikátory přístupu nebo mít parametry.  

- Třídy nebo struktury může mít pouze jeden statický konstruktor.

- Statické konstruktory nelze zděděné nebo přetížené.

- Statický konstruktor nelze volat přímo a je určená jenom k volání modulem common language runtime (CLR). Vyvolá se automaticky.

- Uživatel nemá žádnou kontrolu na při spouštění statický konstruktor se v programu.
  
- Statický konstruktor je automaticky volána k inicializaci [třídy](../../../csharp/language-reference/keywords/class.md) před první instance je vytvořena nebo jsou odkazovány jakékoli statické členy. Statický konstruktor se spustit před spuštěním konstruktoru instance. Všimněte si, že když uživatel vyvolá statickou metodu přiřazená události nebo delegáta, a ne v případě, že je přiřazen název statického konstruktoru typu. Pokud je proměnná inicializátory statické pole v třídě statický konstruktor, budou provedeny v textové pořadí, v jakém jsou uvedeny v deklaraci třídy bezprostředně před provedením statický konstruktor.

- Pokud statický konstruktor k inicializaci statických polí nezadáte, všechny statické pole jsou inicializovány na výchozí hodnoty, jak je uvedeno v [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md). 
  
- Pokud statický konstruktor vyvolá výjimku, modul runtime nebude volat podruhé a typ zůstanou neinicializované po dobu životnosti domény aplikace, ve kterém je spuštěna aplikace. Nejčastěji <xref:System.TypeInitializationException> je vyvolána výjimka, pokud statický konstruktor nemůže vytvořit instanci typu nebo pro neošetřené výjimky, ke kterým dochází v rámci statický konstruktor. Implicitní statické konstruktory, které nejsou explicitně definovány ve zdrojovém kódu řešení problémů může vyžadovat, aby kontroly kódu (IL intermediate language).

- Zabrání přidání přítomnost statického konstruktoru <xref:System.Reflection.TypeAttributes.BeforeFieldInit> atribut type. To omezuje optimalizace běhu programu.

- Pole deklarované jako `static readonly` se dá přiřadit jenom jako součást její deklarace nebo ve statickém konstruktoru. Když explicitní statický konstruktor není vyžadována, inicializujte statické pole na deklarace, nikoli statický konstruktor pro lepší optimalizace běhu programu.

> [!Note]
> I když není přímo přístupný, musí být zdokumentována přítomnost explicitní statický konstruktor pro účely pomoci s řešení potíží s výjimkami inicializace.

### <a name="usage"></a>Použití

- Typické použití statických konstruktorů je při třídu používá soubor protokolu a konstruktor se používá k zápisu položky do tohoto souboru.  
- Statické konstruktory jsou také užitečné při vytváření obálkových tříd pro nespravovaný kód, konstruktor může volat `LoadLibrary` metody.  

- Statické konstruktory jsou také vhodné místo pro vynutit kontroly za běhu na parametr typu, který nelze zaregistrovat v době kompilace prostřednictvím omezení (omezení parametru typu).

## <a name="example"></a>Příklad
 V tomto příkladu třída `Bus` má statický konstruktor. Při první instance `Bus` je vytvořen (`bus1`), je vyvolána statický konstruktor k inicializaci třídy. Ukázkový výstup ověřuje, že statický konstruktor spouští jenom jednou, i když dvě instance `Bus` jsou vytvořeny, a že běží před spuštěním konstruktoru instance.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]
 
## <a name="c-language-specification"></a>specifikace jazyka C#
Další informace najdete v tématu [statické konstruktory](~/_csharplang/spec/classes.md#static-constructors) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Statické třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [Pokyny pro návrh konstruktoru](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Upozornění zabezpečení – CA2121: Statické konstruktory by měly být privátní](https://docs.microsoft.com/en-us/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
