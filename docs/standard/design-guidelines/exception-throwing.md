---
title: Vyvolání výjimek
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 18927d242c2ed957d2bc9f8b481beeed775a4e4e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741673"
---
# <a name="exception-throwing"></a>Vyvolání výjimek
Výjimky – pokyny pro vyvolání výjimky popsané v této části vyžadují dobrou definici významu selhání spuštění. K selhání spuštění dojde pokaždé, když člen nemůže dělat, co byl navržený tak, aby to provedl (co název členu implikuje). Například pokud metoda `OpenFile` nemůže vrátit otevřený popisovač souboru volajícímu, bude považována za chybu spuštění.

 Většina vývojářů se seznámila s používáním výjimek pro chyby použití, jako je dělení nulou nebo odkazy s hodnotou null. V rozhraní se výjimky používají pro všechny chybové stavy, včetně chyb spuštění.

 ❌ nevracet chybové kódy.

 Výjimky jsou primárními prostředky pro hlášení chyb v rozhraních.

 ✔️ provádění sestav při selhání při vyvolávání výjimek.

 ✔️ Zvažte ukončení procesu voláním `System.Environment.FailFast` (.NET Framework 2,0) namísto vyvolání výjimky, pokud váš kód narazí na situaci, kde je nebezpečný pro další spuštění.

 Pokud je to možné, ❌ nepoužívejte výjimky pro normální tok řízení.

 S výjimkou selhání systému a operací s potenciálními konflikty časování by měli návrháři architektury navrhovat rozhraní API, aby mohli uživatelé napsat kód, který nevyvolá výjimky. Například můžete zadat způsob, jak kontrolovat předběžné podmínky před voláním členu, aby mohli uživatelé napsat kód, který nevyvolá výjimky.

 Člen, který se používá ke kontrole předběžných podmínek jiného člena, se často označuje jako Tester a člen, který práci skutečně provede, se nazývá Doer.

 Existují případy, kdy test a Doer vzor může mít nepřijatelný výkon. V takových případech by se měl vzít v úvahu vzor typu try-Parse (viz [výjimky a výkon](../../../docs/standard/design-guidelines/exceptions-and-performance.md) pro další informace).

 ✔️ VZÍT v úvahu dopady na výkon při vyvolávání výjimek. Míry volání přesahující výše 100 za sekundu budou pravděpodobně výrazně ovlivňovat výkon většiny aplikací.

 ✔️ zdokumentovat všechny výjimky vyvolané veřejně vyvolanými členy z důvodu porušení členské smlouvy (spíše než selhání systému) a zacházet s nimi jako součást vaší smlouvy.

 Výjimky, které jsou součástí kontraktu, by neměly být změněny z jedné verze na další (tj. typ výjimky by se neměly měnit a nové výjimky by neměly být přidány).

 ❌ nemají veřejné členy, které mohou být na základě některé z možností buď throw, nebo nikoli.

 ❌ nemají veřejné členy, kteří vracejí výjimky jako návratovou hodnotu nebo parametr `out`.

 Vrácení výjimek z veřejných rozhraní API namísto vyvolání přináší mnoho výhod zasílání zpráv o chybách na základě výjimek.

 ✔️ Zvažte použití metod Tvůrce výjimek.

 Je běžné vyvolat stejnou výjimku z různých míst. Chcete-li se vyhnout dispozici determinističtější kódu, použijte pomocné metody, které vytvářejí výjimky a inicializujte jejich vlastnosti.

 Také členy, kteří vyvolávají výjimky, nejsou vloženy. Přesunutí příkazu throw uvnitř tvůrce může umožňovat, aby byl člen vložen.

 ❌ nevyvolávat výjimky z bloků filtru výjimky.

 Pokud filtr výjimek vyvolá výjimku, je výjimka zachycena modulem CLR a filtr vrátí hodnotu false. Toto chování je neodlišitelné od vykonání filtru a vrací hodnotu false explicitně a je proto velmi obtížné ho ladit.

 ❌ Vyhněte explicitnímu vyvolávání výjimek z bloků finally. Implicitně vyvolané výjimky, které jsou výsledkem volání metod, které vyvolává vyvolání, jsou přijatelné.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)
