---
title: "Návrh – konstruktor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a46bf111b76ef6d07fa99cc3b19684a0726b7062
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="constructor-design"></a>Návrh – konstruktor
Existují dva druhy konstruktory: Zadejte konstruktory a konstruktory instancí.  
  
 Konstruktory typu statické a spustit modul CLR před použitím typu. Konstruktory instancí spuštěny při vytvoření instance typu.  
  
 Konstruktory typu nelze provést žádné parametry. Konstruktory instancí můžete. Konstruktory instancí, které nechcete provést žádné parametry se často nazývají výchozí konstruktory.  
  
 Konstruktory jsou nejvíce přirozené způsob, jak vytvořit instance typu. Většina vývojářů bude hledat a pokuste se použít konstruktor před jejich zvažte alternativní způsoby vytváření instancí (například metody vytváření).  
  
 **✓ ZVAŽTE** poskytuje jednoduchý, v ideálním případě výchozí, konstruktory.  
  
 Jednoduché konstruktor má velmi malý počet parametrů a všechny parametry jsou primitiv nebo výčty. Tyto jednoduché konstruktory zvýšit použitelnost rozhraní.  
  
 **✓ ZVAŽTE** pomocí metody statické factory místo konstruktoru, pokud sémantiku požadovaná operace se nemapují přímo do vytváření nové instance, nebo pokud následující pokyny pro návrh konstruktor funguje nepřirozené.  
  
 **PROVEĎTE ✓** použít konstruktor parametry jako zástupce pro nastavení hlavní vlastností.  
  
 Měla by existovat žádný rozdíl ve smyslu sémantiky mezi pomocí prázdného konstruktoru následuje některé sady vlastností a pomocí konstruktoru více argumentů.  
  
 **PROVEĎTE ✓** používají stejný název pro konstruktor parametry a vlastnosti, pokud se parametry konstruktor používají se jednoduše nastavit vlastnost.  
  
 Jediným rozdílem mezi tyto parametry a vlastnosti by měl být velká a malá písmena.  
  
 **PROVEĎTE ✓** minimálním úsilím v konstruktoru.  
  
 Konstruktory neměli dělat spoustu práce než zachycení parametry konstruktor. Náklady na další zpracování by měl odloží až požadovaných.  
  
 **PROVEĎTE ✓** vyvolat výjimky z konstruktory instancí, podle potřeby.  
  
 **PROVEĎTE ✓** explicitně deklarovat veřejný výchozí konstruktor ve třídách, pokud je potřeba takový konstruktor.  
  
 Pokud na typ není explicitně deklarovat všechny konstruktory, mnoha jazycích (například C#) automaticky přidá výchozí veřejný konstruktor. (Abstraktní třídy získat chráněný konstruktor.)  
  
 Přidání parametrizovaného konstruktor na třídu zabrání kompilátoru přidávání výchozí konstruktor. To často způsobuje náhodných nejnovější změny.  
  
 **X nepoužívejte** explicitně na struktury definování výchozí konstruktory.  
  
 Díky tomu pole vytvoření rychlejší, protože pokud není definován výchozí konstruktor, nemá ke spuštění na každý slot v poli. Všimněte si, že mnoho kompilátory, včetně C#, Nepovolit struktury tak, aby měl bezparametrové konstruktory z tohoto důvodu.  
  
 **X nepoužívejte** volání virtuální členové objektu uvnitř jeho konstruktoru.  
  
 Volání metody člena virtuální způsobí, že nejodvozenějších přepsání, která se má volat, i když konstruktoru nejvíce odvozený typ dosud nebyla spuštěna plně.  
  
### <a name="type-constructor-guidelines"></a>Pokyny pro konstruktor typu  
 **PROVEĎTE ✓** soukromá statické konstruktory.  
  
 Statický konstruktor, označované taky jako konstruktoru třídy, se používá k chybě při inicializaci typu. Modul CLR volá statického konstruktoru dřív, než se vytvoří první instance typu nebo se nazývají všechny statické členy tohoto typu. Uživatel nemá žádnou kontrolu nad kdy se nazývá statického konstruktoru. Statický konstruktor není privátní, může být volána kódu než modulu CLR. V závislosti na operací prováděných v konstruktoru to může způsobit neočekávané chování. Kompilátor jazyka C# vynutí statické konstruktory důvěrné.  
  
 **X nesmí** generování výjimek ze statické konstruktory.  
  
 Pokud z konstruktoru typu je vyvolána výjimka, typ není v aktuální doméně aplikace.  
  
 **✓ ZVAŽTE** inicializace statického pole vloženě než explicitně pomocí statické konstruktory, protože modul runtime je schopen optimalizovat výkon typy, které nemají explicitně definovaných statického konstruktoru.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Člen pokynů pro návrh](../../../docs/standard/design-guidelines/member.md)  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)
