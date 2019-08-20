---
title: Statické konstruktory – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 6d1a39008ebb965649104c2e74241780731911bb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596034"
---
# <a name="static-constructors-c-programming-guide"></a>Statické konstruktory (Průvodce programováním v C#)
Statický konstruktor slouží k inicializaci libovolných [statických](../../language-reference/keywords/static.md) dat nebo k provedení určité akce, kterou je třeba provést pouze jednou. Je volána automaticky před vytvořením první instance nebo odkazem na statické členy.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
 
## <a name="remarks"></a>Poznámky
Statické konstruktory mají následující vlastnosti:  
  
- Statický konstruktor nepřijímá modifikátory přístupu ani parametry.  

- Třída nebo struktura může mít pouze jeden statický konstruktor.

- Statické konstruktory nemůžou být zděděné nebo přetížené.

- Statický konstruktor nelze volat přímo a je určen pouze pro volání modulu CLR (Common Language Runtime). Je vyvoláno automaticky.

- Uživatel nemá žádné řízení při spuštění statického konstruktoru v programu.
  
- Statický konstruktor se nazývá automaticky pro inicializaci [třídy](../../language-reference/keywords/class.md) před vytvořením první instance nebo odkazováním na všechny statické členy. Statický konstruktor se spustí před konstruktorem instance. Všimněte si, že statický konstruktor typu je volán, když je vyvolána statická metoda přiřazená události nebo delegátu a nikoli při přiřazení. Pokud jsou Inicializátory proměnných statického pole přítomny ve třídě statického konstruktoru, budou spuštěny v textovém pořadí, ve kterém jsou uvedeny v deklaraci třídy bezprostředně před provedením statického konstruktoru.

- Pokud neposkytnete statický konstruktor pro inicializaci statických polí, všechna statická pole jsou inicializována na výchozí hodnotu, jak je uvedeno v [tabulce výchozí hodnoty](../../language-reference/keywords/default-values-table.md). 
  
- Pokud statický konstruktor vyvolá výjimku, modul runtime je nespustí podruhé a typ zůstane Neinicializovaný po dobu života domény aplikace, ve které je program spuštěn. Většinou je vyvolána <xref:System.TypeInitializationException> výjimka, když statický konstruktor není schopen vytvořit instanci typu nebo pro neošetřenou výjimku, ke které došlo v rámci statického konstruktoru. U implicitních statických konstruktorů, které nejsou explicitně definovány ve zdrojovém kódu, může řešení potíží vyžadovat kontrolu kódu zprostředkujícího jazyka (IL).

- Přítomnost statického konstruktoru brání přidání <xref:System.Reflection.TypeAttributes.BeforeFieldInit> atributu typu. To omezuje optimalizaci za běhu.

- Pole deklarované jako `static readonly` může být přiřazeno pouze v rámci deklarace nebo ve statickém konstruktoru. Pokud není vyžadován explicitní statický konstruktor, inicializujte statická pole v deklaraci, nikoli prostřednictvím statického konstruktoru pro lepší optimalizaci modulu runtime.

> [!Note]
> I když není přímo přístupný, měla by být popsána přítomnost explicitního statického konstruktoru, který pomáhá řešit výjimky inicializace.

### <a name="usage"></a>Použití

- Typické použití statických konstruktorů je v případě, že třída používá soubor protokolu a konstruktor je použit k zápisu položek do tohoto souboru.  
- Statické konstruktory jsou užitečné také při vytváření obálkových tříd pro nespravovaný kód, pokud konstruktor může volat `LoadLibrary` metodu.  

- Statické konstruktory jsou také vhodným místem pro vynutit kontroly za běhu u parametru typu, který nelze kontrolovat v době kompilace prostřednictvím omezení (omezení parametrů typu).

## <a name="example"></a>Příklad
 V tomto příkladu třída `Bus` má statický konstruktor. Když `Bus` je vytvořena první instance třídy (`bus1`), je vyvolán statický konstruktor pro inicializaci třídy. Ukázkový výstup ověřuje, zda je statický konstruktor spouštěn pouze jednou, i když `Bus` jsou vytvořeny dvě instance a že je spuštěn před spuštěním konstruktoru instance.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]
 
## <a name="c-language-specification"></a>specifikace jazyka C#
Další informace naleznete v části [statické konstruktory](~/_csharplang/spec/classes.md#static-constructors) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Statické třídy a jejich členové](./static-classes-and-static-class-members.md)
- [Finalizační metody](./destructors.md)
- [Pokyny pro návrh konstruktoru](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Upozornění zabezpečení – CA2121: Statické konstruktory by měly být privátní.](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
