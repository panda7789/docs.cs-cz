---
title: Vyvolání výjimek
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 47c16ac94054fff193b1f5976fe7f04f10a39ecd
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="exception-throwing"></a>Vyvolání výjimek
Pokyny pro vyvolávání výjimek popsaných v této části vyžadují dobrý definice význam selhání spuštění. Dojde k chybě provádění, vždy, když se člen nemůžete udělat, co byla navržená tak, aby se (co člena již název napovídá). Například pokud `OpenFile` metoda nemůže vrátit popisovač otevřený soubor volajícímu, může být považovaná Chyba při spuštění.  
  
 Většina vývojářů se tedy se použití výjimek pro využití chyby jako např. dělení nulou či odkazy s hodnotou null. V rozhraní Framework výjimky se používají pro všechny chybové stavy, včetně chyby spuštění.  
  
 **X nesmí** návratové kódy chyb.  
  
 Výjimky jsou primární způsob zasílání zpráv o chybách v rozhraní.  
  
 **PROVEĎTE ✓** sestavy selhání spuštění ve vyvolání výjimky.  
  
 **✓ ZVAŽTE** proces se ukončuje voláním `System.Environment.FailFast` (funkce rozhraní .NET Framework 2.0) namísto došlo k výjimce, pokud váš kód zjistí situaci, kde nezabezpečený pro další zpracování.  
  
 **X nesmí** používat výjimky pro normálního toku řízení, pokud je to možné.  
  
 S výjimkou chyby systému a operace s potenciální konflikty časování měli framework Designer navrhnout rozhraní API, uživatelé můžete napsat kód, který nevyvolá výjimku výjimky. Můžete například zadat způsob, jak zkontrolovat předběžné podmínky před voláním členem, takže uživatelé můžete napsat kód, který nevyvolá výjimku výjimky.  
  
 Člen použita ke kontrole předběžné podmínky jiného člena se často označuje jako testování a člena, který skutečně funguje se nazývá doer.  
  
 Pokud vzor Tester Doer může mít nepřijatelné zatížení existují případy. V takových případech vzoru takzvané zkuste analýzy považovat (viz [výjimky a výkonu](../../../docs/standard/design-guidelines/exceptions-and-performance.md) Další informace).  
  
 **✓ ZVAŽTE** vliv na výkon u vyvolávání výjimek. Throw sazby vyšší než 100 za sekundu se pravděpodobně výrazně ovlivnit výkon většinu aplikací.  
  
 **PROVEĎTE ✓** dokumentu všechny výjimky vyvolané veřejně s členy z důvodu narušení člena smlouvy (místo selhání systému) a je považovat za část vaše smlouvy.  
  
 Výjimky, které jsou součástí smlouvy nesmí změnit z jedné verze na další (tj, nesmí změnit typ výjimky a by neměly být přidávány nové výjimky).  
  
 **X nesmí** veřejné členy, které můžete buď throw nebo není na některé možnost základě.  
  
 **X nesmí** mají veřejné členy, které vracejí výjimky jako návratová hodnota nebo `out` parametr.  
  
 Vrácení výjimky z veřejné rozhraní API místo vyvolání je účinně chrání před řadu výhod zasílání zpráv o chybách na základě výjimky.  
  
 **✓ ZVAŽTE** pomocí metody tvůrce výjimky.  
  
 Je běžné vyvolat stejnou výjimku z různých místech. Předejdete tomu kódu použitím pomocné metody, které vytvořit výjimky a jejich vlastnosti inicializace.  
  
 Také nejsou členy, kteří throw výjimky získávání vložená. Přesunutí příkaz throw do Tvůrce, mohou povolovat člen být vložená.  
  
 **X nesmí** vyvolat výjimky z bloky filtru výjimek.  
  
 Pokud filtr výjimek vyvolá výjimku, je výjimka zachycena CLR a filtr, vrátí hodnotu false. Toto chování je lišit od filtr provádění a vrácení hodnoty false explicitně a je proto velmi obtížné ladění.  
  
 **X nepoužívejte** explicitně vyvolání výjimky z finally – bloky. Výsledkem volání metody, které vyvolají implicitně vyvolané výjimky jsou přijatelné.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)
