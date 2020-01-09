---
title: Vyvolání výjimek
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 7d1b63e5fde57cbe37a1250d16b6bf74a2d5dc8e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709397"
---
# <a name="exception-throwing"></a>Vyvolání výjimek
Výjimky – pokyny pro vyvolání výjimky popsané v této části vyžadují dobrou definici významu selhání spuštění. K selhání spuštění dojde pokaždé, když člen nemůže dělat, co byl navržený tak, aby to provedl (co název členu implikuje). Například pokud metoda `OpenFile` nemůže vrátit otevřený popisovač souboru volajícímu, bude považována za chybu spuštění.  
  
 Většina vývojářů se seznámila s používáním výjimek pro chyby použití, jako je dělení nulou nebo odkazy s hodnotou null. V rozhraní se výjimky používají pro všechny chybové stavy, včetně chyb spuštění.  
  
 **X DO NOT** návratové kódy chyb.  
  
 Výjimky jsou primárními prostředky pro hlášení chyb v rozhraních.  
  
 **✓ DO** sestavy selhání spuštění ve vyvolání výjimky.  
  
 **✓ CONSIDER** proces se ukončuje voláním `System.Environment.FailFast` (funkce rozhraní .NET Framework 2.0) namísto došlo k výjimce, pokud váš kód zjistí situaci, kde nezabezpečený pro další zpracování.  
  
 **X DO NOT** používat výjimky pro normálního toku řízení, pokud je to možné.  
  
 S výjimkou selhání systému a operací s potenciálními konflikty časování by měli návrháři architektury navrhovat rozhraní API, aby mohli uživatelé napsat kód, který nevyvolá výjimky. Například můžete zadat způsob, jak kontrolovat předběžné podmínky před voláním členu, aby mohli uživatelé napsat kód, který nevyvolá výjimky.  
  
 Člen, který se používá ke kontrole předběžných podmínek jiného člena, se často označuje jako Tester a člen, který práci skutečně provede, se nazývá Doer.  
  
 Existují případy, kdy test a Doer vzor může mít nepřijatelný výkon. V takových případech by se měl vzít v úvahu vzor typu try-Parse (viz [výjimky a výkon](../../../docs/standard/design-guidelines/exceptions-and-performance.md) pro další informace).  
  
 **✓ CONSIDER** vliv na výkon u vyvolávání výjimek. Míry volání přesahující výše 100 za sekundu budou pravděpodobně výrazně ovlivňovat výkon většiny aplikací.  
  
 **✓ DO** dokumentu všechny výjimky vyvolané veřejně s členy z důvodu narušení člena smlouvy (místo selhání systému) a je považovat za část vaše smlouvy.  
  
 Výjimky, které jsou součástí kontraktu, by neměly být změněny z jedné verze na další (tj. typ výjimky by se neměly měnit a nové výjimky by neměly být přidány).  
  
 **X DO NOT** veřejné členy, které můžete buď throw nebo není na některé možnost základě.  
  
 **X DO NOT** mají veřejné členy, které vracejí výjimky jako návratová hodnota nebo `out` parametr.  
  
 Vrácení výjimek z veřejných rozhraní API namísto vyvolání přináší mnoho výhod zasílání zpráv o chybách na základě výjimek.  
  
 **✓ CONSIDER** pomocí metody tvůrce výjimky.  
  
 Je běžné vyvolat stejnou výjimku z různých míst. Chcete-li se vyhnout dispozici determinističtější kódu, použijte pomocné metody, které vytvářejí výjimky a inicializujte jejich vlastnosti.  
  
 Také členy, kteří vyvolávají výjimky, nejsou vloženy. Přesunutí příkazu throw uvnitř tvůrce může umožňovat, aby byl člen vložen.  
  
 **X DO NOT** vyvolat výjimky z bloky filtru výjimek.  
  
 Pokud filtr výjimek vyvolá výjimku, je výjimka zachycena modulem CLR a filtr vrátí hodnotu false. Toto chování je neodlišitelné od vykonání filtru a vrací hodnotu false explicitně a je proto velmi obtížné ho ladit.  
  
 **X AVOID** explicitně vyvolání výjimky z finally – bloky. Implicitně vyvolané výjimky, které jsou výsledkem volání metod, které vyvolává vyvolání, jsou přijatelné.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)
