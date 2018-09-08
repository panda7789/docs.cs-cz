---
title: Návrh konstruktoru
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ad920c8028b102a13fdfe928d21768538e25b0f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180446"
---
# <a name="constructor-design"></a>Návrh konstruktoru
Existují dva typy konstruktorů: Zadejte konstruktory a konstruktory instancí.  
  
 Konstruktory typu jsou statické a jsou provozované CLR předtím, než se typ používá. Konstruktory instancí spustí, když je vytvořena instance typu.  
  
 Konstruktory typu nelze provést žádné parametry. Konstruktory instancí může. Konstruktory instancí, které nechcete provést žádné parametry jsou často nazývány výchozí konstruktory.  
  
 Konstruktory jsou nejvíce přirozený způsob, jak vytvořit instance typu. Většina vývojářů hledání, který se pokusí použít konstruktor před považují za alternativní způsoby vytváření instancí (například metody pro vytváření objektů).  
  
 **✓ CONSIDER** poskytuje jednoduchý, v ideálním případě výchozí, konstruktory.  
  
 Jednoduché konstruktor má velmi malý počet parametrů a všechny parametry jsou primitivních elementů nebo výčty. Tyto jednoduché konstruktory zlepšit tak použitelnost rozhraní Framework.  
  
 **✓ CONSIDER** pomocí metody statické factory místo konstruktoru, pokud sémantiku požadovaná operace se nemapují přímo do vytváření nové instance, nebo pokud následující pokyny pro návrh konstruktor funguje nepřirozené.  
  
 **✓ DO** použít konstruktor parametry jako zástupce pro nastavení hlavní vlastností.  
  
 Měla by existovat žádné rozdíly v sémantice mezi pomocí prázdného konstruktoru, za nímž následuje některé vlastnosti sady a pomocí více argumentů konstruktoru.  
  
 **✓ DO** používají stejný název pro konstruktor parametry a vlastnosti, pokud se parametry konstruktor používají se jednoduše nastavit vlastnost.  
  
 Jediným rozdílem mezi tyto parametry a vlastnosti by měla být malá a velká písmena.  
  
 **✓ DO** minimálním úsilím v konstruktoru.  
  
 Konstruktory by neměla provést mnoho práce než zachytávání parametry konstruktoru. Náklady na libovolné jiné zpracování zpoždění, dokud se vyžaduje.  
  
 **✓ DO** vyvolat výjimky z konstruktory instancí, podle potřeby.  
  
 **✓ DO** explicitně deklarovat veřejný výchozí konstruktor ve třídách, pokud je potřeba takový konstruktor.  
  
 Pokud se u typu není explicitně deklarovat žádné konstruktory, řadu jazyků (jako je C#) automaticky přidá veřejný výchozí konstruktor. (Abstraktní třídy získat chráněný konstruktor.)  
  
 Přidávání do parametrizovaného konstruktoru třídy zabrání kompilátoru přidávání výchozího konstruktoru. Často způsobuje náhodného nejnovější změny.  
  
 **X AVOID** explicitně na struktury definování výchozí konstruktory.  
  
 To umožňuje vytvoření pole rychleji, protože pokud výchozí konstruktor není definován, nemá pro spuštění na každé pozici pole. Všimněte si, že mnoho kompilátorů, včetně C#, Nepovolit struktury z tohoto důvodu mít konstruktor bez parametrů.  
  
 **X AVOID** volání virtuální členové objektu uvnitř jeho konstruktoru.  
  
 Volání virtuální člen způsobí nejodvozenějšího přepsání volat, i v případě, že nejvíc odvozený typ konstruktoru dosud nebyla spuštěna plně.  
  
### <a name="type-constructor-guidelines"></a>Pokyny pro konstruktor typu  
 **✓ DO** soukromá statické konstruktory.  
  
 Statický konstruktor, také volat konstruktor třídy slouží k inicializaci typu. CLR volá statický konstruktor před první instance typu je vytvořen nebo jakékoli statické členy tohoto typu jsou volány. Uživatel nemá žádnou kontrolu nad tím, kdy je volána statický konstruktor. Pokud statický konstruktor není soukromý, může být volán kód než CLR. V závislosti na operací provedených v konstruktoru to může způsobit neočekávané chování. Kompilátor jazyka C# vynutí statické konstruktory mají být privátní.  
  
 **X DO NOT** generování výjimek ze statické konstruktory.  
  
 Pokud je vyvolána výjimka v konstruktoru typu, typ není v aktuální doméně aplikace.  
  
 **✓ CONSIDER** inicializace statického pole vloženě než explicitně pomocí statické konstruktory, protože modul runtime je schopen optimalizovat výkon typy, které nemají explicitně definovaných statického konstruktoru.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
