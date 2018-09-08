---
title: Vyvolání výjimek
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fbbe84811e3fa096b9e13c459143311bb75a198
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44132635"
---
# <a name="exception-throwing"></a>Vyvolání výjimek
Vyvolání výjimek pokynů popsaných v této části vyžadují správné definice význam selhání spuštění. Chyba při spuštění vyvolá se při každém člena nelze provést, který byl navržený tak, aby se (co člen již název napovídá). Například pokud `OpenFile` metoda popisovač otevřený soubor nemůže vracet volajícímu, může být považován Chyba při spuštění.  
  
 Většina vývojářů se staly umíte pracovat se použití výjimek pro využití chyby jako např. dělení nulou či odkazy s hodnotou null. V rámci výjimky se používají pro všechny chybové stavy, včetně zpracování chyb.  
  
 **X DO NOT** návratové kódy chyb.  
  
 Výjimky jsou primární prostředky zpráv o chybách v rozhraní.  
  
 **✓ DO** sestavy selhání spuštění ve vyvolání výjimky.  
  
 **✓ CONSIDER** proces se ukončuje voláním `System.Environment.FailFast` (funkce rozhraní .NET Framework 2.0) namísto došlo k výjimce, pokud váš kód zjistí situaci, kde nezabezpečený pro další zpracování.  
  
 **X DO NOT** používat výjimky pro normálního toku řízení, pokud je to možné.  
  
 S výjimkou chyby systému a operace s potenciální konflikty časování by měl framework návrháři navrhovat rozhraní API, tak uživatelům můžete napsat kód, který nevrací výjimky. Můžete například poskytnout způsob, jak zkontrolovat předpoklady před voláním člen tak uživatelům můžete napsat kód, který nevrací výjimky.  
  
 Člen sloužící ke kontrole předběžné podmínky jiného člena se často označuje jako tester a člena, který ve skutečnosti funguje se volá doer.  
  
 Existují případy, kdy vzor Tester Doer může mít nároky na výkon nepřijatelný. V takových případech takzvané vzor analýzy zkuste by měl být (viz [výjimek a výkonu](../../../docs/standard/design-guidelines/exceptions-and-performance.md) Další informace).  
  
 **✓ CONSIDER** vliv na výkon u vyvolávání výjimek. Sazby za throw nad 100 za sekundu se pravděpodobně výrazně ovlivnit výkon většinu aplikací.  
  
 **✓ DO** dokumentu všechny výjimky vyvolané veřejně s členy z důvodu narušení člena smlouvy (místo selhání systému) a je považovat za část vaše smlouvy.  
  
 Výjimky, které jsou součástí smlouvy nesmí změnit z jedné verze na další (tj, by neměly měnit typ výjimky a neměl by se přidávat nové výjimky).  
  
 **X DO NOT** veřejné členy, které můžete buď throw nebo není na některé možnost základě.  
  
 **X DO NOT** mají veřejné členy, které vracejí výjimky jako návratová hodnota nebo `out` parametr.  
  
 Vrácení výjimky z veřejných rozhraní API namísto vyvolání jejich poráží mnohé z výhod hlášení chyb na základě výjimky.  
  
 **✓ CONSIDER** pomocí metody tvůrce výjimky.  
  
 Je běžné vyvolat stejnou výjimku z různých míst. Aby se zabránilo jejímu narůstání kódu, použijte pomocné metody vytvoření výjimky a inicializaci jejich vlastností.  
  
 Navíc nejsou členy, které vyvolají výjimky získávání vložená. Přesunutí příkaz throw do Tvůrce může umožnit člen se nedá vložit.  
  
 **X DO NOT** vyvolat výjimky z bloky filtru výjimek.  
  
 Když filtru výjimky vyvolá výjimku, výjimka se zachycuje prostřednictvím modulu CLR a filtr vrátí hodnotu false. Toto chování je nerozeznatelná od tohoto filtru, provádění a vrácení hodnoty false explicitně a proto je velmi obtížné ladit.  
  
 **X AVOID** explicitně vyvolání výjimky z finally – bloky. Implicitně vyvolané výjimky vyplývající z volání metod, které vyvolají jsou přijatelné.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)
