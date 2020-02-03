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
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741734"
---
# <a name="constructor-design"></a>Návrh konstruktoru

Existují dva druhy konstruktorů: konstruktory typů a konstruktory instancí.

Konstruktory typů jsou statické a jsou spuštěny modulem CLR před použitím typu. Konstruktory instancí jsou spouštěny při vytvoření instance typu.

Konstruktory typů nemůžou mít žádné parametry. Konstruktory instancí můžou. Konstruktory instancí, které nevyužívají žádné parametry, se často nazývají konstruktory bez parametrů.

Konstruktory představují nejpřirozený způsob, jak vytvořit instance typu. Většina vývojářů hledá a pokusí se použít konstruktor předtím, než uvažují alternativní způsoby vytváření instancí (například metody výroby).

✔️ Zvažte poskytování jednoduchých, ideálních, ideálních konstruktorů.

Jednoduchý konstruktor má velmi malý počet parametrů a všechny parametry jsou primitivní nebo výčty. Takové jednoduché konstruktory zvyšují použitelnost rozhraní.

✔️ Zvažte použití statické metody Factory namísto konstruktoru, pokud sémantika požadované operace není mapována přímo na konstrukci nové instance, nebo pokud podle pokynů pro návrh konstruktoru nevidíte nepřirozeně.

✔️ použít parametry konstruktoru jako zkratky pro nastavení hlavních vlastností.

V sémantikě by neměl být žádný rozdíl mezi použitím prázdného konstruktoru následovanýho některými sadami vlastností a použitím konstruktoru s více argumenty.

✔️ použít stejný název pro parametry konstruktoru a vlastnost, pokud jsou parametry konstruktoru použity pro jednoduše nastavení vlastnosti.

Jediný rozdíl mezi takovými parametry a vlastnostmi musí být velká a malá písmena.

✔️ UDĚLAT v konstruktoru minimální práci.

Konstruktory by neměly dělat mnohem více práce než zachycení parametrů konstruktoru. Náklady na jakékoli jiné zpracování by měly být zpožděny, dokud není vyžadováno.

Pokud je to vhodné, ✔️ vyvolat výjimky z konstruktorů instance.

✔️ explicitně deklarovat veřejný konstruktor bez parametrů ve třídách, pokud je takový konstruktor požadován.

Pokud nedeklarujete explicitně žádné konstruktory typu, mnoho jazyků (například C#) bude automaticky přidávat veřejný konstruktor bez parametrů. (Abstraktní třídy získávají chráněný konstruktor.)

Přidání parametrizovaného konstruktoru do třídy znemožní kompilátoru přidat konstruktor bez parametrů. To často způsobí nechtěné změny.

❌ se vyhnout explicitnímu definování konstruktorů bez parametrů u struktur.

Díky tomu je vytvoření pole rychlejší, protože pokud konstruktor bez parametrů není definován, nemusí být spuštěn na všech slotech v poli. Všimněte si, že mnoho kompilátorů C#, včetně, neumožňuje strukturám mít z tohoto důvodu konstruktory bez parametrů.

❌ Vyhněte se volání virtuálních členů u objektu uvnitř jeho konstruktoru.

Volání virtuálního členu způsobí volání nejvíce odvozeného přepsání, a to i v případě, že konstruktor nejvíce odvozeného typu nebyl dosud zcela spuštěn.

## <a name="type-constructor-guidelines"></a>Pokyny k konstruktoru typu

✔️ UDĚLAT statické konstruktory jako soukromé.

Pro inicializaci typu se používá statický konstruktor, označovaný také jako konstruktor třídy. Modul CLR volá statický konstruktor před vytvořením první instance typu nebo se zavoláním všech statických členů tohoto typu. Uživatel nemá žádné řízení při volání statického konstruktoru. Pokud statický konstruktor není privátní, může být volán jiným kódem než CLR. V závislosti na operacích provedených v konstruktoru to může způsobit neočekávané chování. C# Kompilátor vynutí, aby statické konstruktory byly privátní.

❌ nevyvolávat výjimky ze statických konstruktorů.

Je-li výjimka vyvolána z konstruktoru typu, nelze typ použít v aktuální doméně aplikace.

✔️ Zvažte inicializaci statických polí namísto explicitního použití statických konstruktorů, protože modul runtime může optimalizovat výkon typů, které nemají explicitně definovaný statický konstruktor.

*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
