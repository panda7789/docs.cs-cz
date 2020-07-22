---
title: Statické konstruktory – Průvodce programováním v C#
description: Statický konstruktor v jazyce C# inicializuje statická data nebo provede akci prováděnou pouze jednou před vytvořením první instance nebo odkazováním statických členů.
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: e324b2aa968ff5fdf9c268fa3891f67e8530ff87
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863979"
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
  
- Statický konstruktor se nazývá automaticky pro inicializaci [třídy](../../language-reference/keywords/class.md) před vytvořením první instance nebo odkazováním na všechny statické členy. Statický konstruktor se spustí před konstruktorem instance. Statický konstruktor typu je volán, když je vyvolána statická metoda přiřazená události nebo delegátu a nikoli při jejím přiřazení. Pokud jsou Inicializátory proměnných statického pole přítomny ve třídě statického konstruktoru, budou spuštěny v textovém pořadí, ve kterém jsou uvedeny v deklaraci třídy bezprostředně před provedením statického konstruktoru.

- Pokud neposkytnete statický konstruktor pro inicializaci statických polí, všechna statická pole jsou inicializována na výchozí hodnotu, jak je uvedeno ve [výchozích hodnotách typů C#](../../language-reference/builtin-types/default-values.md).
  
- Pokud statický konstruktor vyvolá výjimku, modul runtime je nespustí podruhé a typ zůstane Neinicializovaný po dobu života domény aplikace, ve které je program spuštěn. Většinou <xref:System.TypeInitializationException> je vyvolána výjimka, když statický konstruktor není schopen vytvořit instanci typu nebo pro neošetřenou výjimku, ke které došlo v rámci statického konstruktoru. U implicitních statických konstruktorů, které nejsou explicitně definovány ve zdrojovém kódu, může řešení potíží vyžadovat kontrolu kódu zprostředkujícího jazyka (IL).

- Přítomnost statického konstruktoru brání přidání <xref:System.Reflection.TypeAttributes.BeforeFieldInit> atributu typu. To omezuje optimalizaci za běhu.

- Pole deklarované jako `static readonly` může být přiřazeno pouze v rámci deklarace nebo ve statickém konstruktoru. Pokud není vyžadován explicitní statický konstruktor, inicializujte statická pole v deklaraci, nikoli prostřednictvím statického konstruktoru pro lepší optimalizaci modulu runtime.

> [!Note]
> I když není přímo přístupný, měla by být popsána přítomnost explicitního statického konstruktoru, který pomáhá řešit výjimky inicializace.

### <a name="usage"></a>Využití

- Typické použití statických konstruktorů je v případě, že třída používá soubor protokolu a konstruktor je použit k zápisu položek do tohoto souboru.  
- Statické konstruktory jsou užitečné také při vytváření obálkových tříd pro nespravovaný kód, pokud konstruktor může volat `LoadLibrary` metodu.  

- Statické konstruktory jsou také pohodlným místem pro vynutit kontroly za běhu u parametru typu, který nelze kontrolovat v době kompilace prostřednictvím omezení (omezení parametrů typu).

## <a name="example"></a>Příklad
 V tomto příkladu třída `Bus` má statický konstruktor. Když je vytvořena první instance `Bus` `bus1` třídy (), je vyvolán statický konstruktor pro inicializaci třídy. Ukázkový výstup ověřuje, zda je statický konstruktor spouštěn pouze jednou, i když `Bus` jsou vytvořeny dvě instance a že je spuštěn před spuštěním konstruktoru instance.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]

## <a name="c-language-specification"></a>specifikace jazyka C#
Další informace naleznete v části [statické konstruktory](~/_csharplang/spec/classes.md#static-constructors) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Statické třídy a jejich členové](./static-classes-and-static-class-members.md)
- [Finalizační metody](./destructors.md)
- [Pokyny pro návrh konstruktoru](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Upozornění zabezpečení – CA2121: statické konstruktory by měly být privátní](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
