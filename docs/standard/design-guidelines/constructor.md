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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400601"
---
# <a name="constructor-design"></a>Návrh konstruktoru

Existují dva druhy konstruktorů: typ konstruktory a instance konstruktory.

Typ konstruktory jsou statické a jsou spuštěny CLR před použitím typu. Konstruktory instancí jsou spuštěny při vytvoření instance typu.

Typ konstruktory nemůže trvat žádné parametry. Instance konstruktory mohou. Instance konstruktory, které neberou žádné parametry se často nazývají konstruktory bez parametrů.

Konstruktory jsou nejpřirozenější způsob, jak vytvořit instance typu. Většina vývojářů bude hledat a pokusí se použít konstruktor před tím, než zváží alternativní způsoby vytváření instancí (například metody výroby).

✔️ zvažte poskytnutí jednoduchých, ideálně výchozích konstruktorů.

Jednoduchý konstruktor má velmi malý počet parametrů a všechny parametry jsou primitiva nebo výčty. Takové jednoduché konstruktory zvyšují použitelnost rámce.

✔️ zvažte použití statické tovární metody namísto konstruktoru, pokud sémantiku požadované operace nemapují přímo na konstrukci nové instance, nebo pokud se následující pokyny pro návrh konstruktoru cítí nepřirozeně.

✔️ DO použít parametry konstruktoru jako zkratky pro nastavení hlavních vlastností.

By měl být žádný rozdíl v sémantice mezi pomocí prázdný konstruktor následuje některé sady vlastností a pomocí konstruktoru s více argumenty.

✔️ DO použít stejný název pro parametry konstruktoru a vlastnost, pokud parametry konstruktoru se používají k jednoduchému nastavení vlastnosti.

Jediným rozdílem mezi těmito parametry a vlastnostmi by měla být písmena.

✔️ provést minimální práci v konstruktoru.

Konstruktory by neměly dělat mnoho práce než zachytit parametry konstruktoru. Náklady na jakékoli jiné zpracování by měly být zpožděny, dokud nebude vyžadováno.

✔️ DO vyvolat výjimky z konstruktorů instancí, pokud je to vhodné.

✔️ DO explicitně deklarovat veřejné konstruktoru bez parametrů ve třídách, pokud je takový konstruktor požadován.

Pokud explicitně nedeklarujete žádné konstruktory na typu, mnoho jazyků (například C#) automaticky přidá veřejný konstruktor bez parametrů. (Abstraktní třídy získat chráněný konstruktor.)

Přidání parametrizovaného konstruktoru do třídy zabrání kompilátoru v přidání konstruktoru bez parametrů. To často způsobuje náhodné změny porušení.

❌Vyhněte se explicitně definovat konstruktory bez parametrů na strukturách.

To zrychluje vytváření pole, protože pokud není definován konstruktor bez parametrů, nemusí být spuštěn na každém slotu v poli. Všimněte si, že mnoho kompilátorů, včetně C#, neumožňují struktury mít konstruktory bez parametrů z tohoto důvodu.

❌Vyhněte se volání virtuálních členů na objekt uvnitř jeho konstruktoru.

Volání virtuálního člena způsobí, že nejvíce odvozené přepsání bude voláno, i když konstruktor nejvíce odvozeného typu ještě nebyl plně spuštěn.

## <a name="type-constructor-guidelines"></a>Pokyny konstruktoru typu

✔️ do, aby statické konstruktory soukromé.

Statický konstruktor, nazývaný také konstruktor třídy, se používá k inicializaci typu. CLR volá statický konstruktor před vytvořením první instance typu nebo jsou volány všechny statické členy tohoto typu. Uživatel nemá žádnou kontrolu nad při volání statického konstruktoru. Pokud statický konstruktor není soukromý, může být volán jiným kódem než CLR. V závislosti na operacích prováděných v konstruktoru to může způsobit neočekávané chování. Kompilátor Jazyka C# vynutí, aby statické konstruktory byly soukromé.

❌NEVYVOLÁVAT výjimky ze statických konstruktorů.

Pokud je vyvolána výjimka z konstruktoru typu, typ není použitelný v aktuální doméně aplikace.

✔️ zvážit inicializaci statických polí vřadit spíše než explicitně pomocí statických konstruktorů, protože runtime je schopen optimalizovat výkon typů, které nemají explicitně definovaný statický konstruktor.

*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

*Přetištěno se svolením Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
