---
title: Návrh konstruktoru
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
author: KrzysztofCwalina
ms.openlocfilehash: a43ec815275e58f4bc6462fb4f5cb4733267de31
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972105"
---
# <a name="constructor-design"></a>Návrh konstruktoru

Existují dva druhy konstruktorů: konstruktory typů a konstruktory instancí.

Konstruktory typů jsou statické a jsou spuštěny modulem CLR před použitím typu. Konstruktory instancí jsou spouštěny při vytvoření instance typu.

Konstruktory typů nemůžou mít žádné parametry. Konstruktory instancí můžou. Konstruktory instancí, které nevyužívají žádné parametry, se často nazývají konstruktory bez parametrů.

Konstruktory představují nejpřirozený způsob, jak vytvořit instance typu. Většina vývojářů hledá a pokusí se použít konstruktor předtím, než uvažují alternativní způsoby vytváření instancí (například metody výroby).

**✓ CONSIDER** poskytuje jednoduchý, v ideálním případě výchozí, konstruktory.

Jednoduchý konstruktor má velmi malý počet parametrů a všechny parametry jsou primitivní nebo výčty. Takové jednoduché konstruktory zvyšují použitelnost rozhraní.

**✓ CONSIDER** pomocí metody statické factory místo konstruktoru, pokud sémantiku požadovaná operace se nemapují přímo do vytváření nové instance, nebo pokud následující pokyny pro návrh konstruktor funguje nepřirozené.

**✓ DO** použít konstruktor parametry jako zástupce pro nastavení hlavní vlastností.

V sémantikě by neměl být žádný rozdíl mezi použitím prázdného konstruktoru následovanýho některými sadami vlastností a použitím konstruktoru s více argumenty.

**✓ DO** používají stejný název pro konstruktor parametry a vlastnosti, pokud se parametry konstruktor používají se jednoduše nastavit vlastnost.

Jediný rozdíl mezi takovými parametry a vlastnostmi musí být velká a malá písmena.

**✓ DO** minimálním úsilím v konstruktoru.

Konstruktory by neměly dělat mnohem více práce než zachycení parametrů konstruktoru. Náklady na jakékoli jiné zpracování by měly být zpožděny, dokud není vyžadováno.

**✓ DO** vyvolat výjimky z konstruktory instancí, podle potřeby.

**✓** Explicitně deklaruje veřejný konstruktor bez parametrů ve třídách, pokud je takový konstruktor požadován.

Pokud nedeklarujete explicitně žádné konstruktory typu, mnoho jazyků (například C#) bude automaticky přidávat veřejný konstruktor bez parametrů. (Abstraktní třídy získávají chráněný konstruktor.)

Přidání parametrizovaného konstruktoru do třídy znemožní kompilátoru přidat konstruktor bez parametrů. To často způsobí nechtěné změny.

**X Vyhněte se** explicitnímu definování konstruktorů bez parametrů u struktur.

Díky tomu je vytvoření pole rychlejší, protože pokud konstruktor bez parametrů není definován, nemusí být spuštěn na všech slotech v poli. Všimněte si, že mnoho kompilátorů C#, včetně, neumožňuje strukturám mít z tohoto důvodu konstruktory bez parametrů.

**X AVOID** volání virtuální členové objektu uvnitř jeho konstruktoru.

Volání virtuálního členu způsobí volání nejvíce odvozeného přepsání, a to i v případě, že konstruktor nejvíce odvozeného typu nebyl dosud zcela spuštěn.

## <a name="type-constructor-guidelines"></a>Pokyny k konstruktoru typu

**✓ DO** soukromá statické konstruktory.

Pro inicializaci typu se používá statický konstruktor, označovaný také jako konstruktor třídy. Modul CLR volá statický konstruktor před vytvořením první instance typu nebo se zavoláním všech statických členů tohoto typu. Uživatel nemá žádné řízení při volání statického konstruktoru. Pokud statický konstruktor není privátní, může být volán jiným kódem než CLR. V závislosti na operacích provedených v konstruktoru to může způsobit neočekávané chování. C# Kompilátor vynutí, aby statické konstruktory byly privátní.

**X DO NOT** generování výjimek ze statické konstruktory.

Je-li výjimka vyvolána z konstruktoru typu, nelze typ použít v aktuální doméně aplikace.

**✓ CONSIDER** inicializace statického pole vloženě než explicitně pomocí statické konstruktory, protože modul runtime je schopen optimalizovat výkon typy, které nemají explicitně definovaných statického konstruktoru.

*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

*Přetištěno oprávněním Pearsonova vzdělávání, Inc. pomocí [pokynů pro návrh rozhraní: Konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
