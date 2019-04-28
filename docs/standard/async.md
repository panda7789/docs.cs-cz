---
title: Přehled asynchronních
description: Zjistěte, jak je asynchronní programování představuje klíčovou techniku, která umožňuje jednoduché blokování vstupně-výstupní operace a souběžné operace s více jádry.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: b9084da80ff400bf99fc8641c69bc38c805d039a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627902"
---
# <a name="async-overview"></a>Přehled asynchronních

Není to tak dávno aplikace rychleji jednoduše si koupíte novější počítač nebo server a potom tento trend se zastavilo. Ve skutečnosti obrácený. Mobilní telefony zobrazovaly s jedním jádrem frekvenci 1ghz ARM čipy a jiné úlohy serveru přešla do virtuálních počítačů. Uživatelé stále chtějí responzivní uživatelské rozhraní a vlastníkům obchodních chtít, aby servery, které se škálují podle jejich společnosti. Přechod na mobilní a cloudové a naplnění připojeného k Internetu z > uživatelé 3B má za následek novou sadu vzorů softwaru. 

* Klientské aplikace se očekává, že byly vždy na, vždy připojen a neustále responzivní na interakci uživatele (například touch) s hodnocením vysokou app storu!
* Očekává se, že služby zpracovávat řádně vertikální navýšení a snížení špičkami v provozu. 

Představuje klíčovou techniku, která umožňuje jednoduché blokování vstupně-výstupní operace a souběžné operace s více jádry je asynchronní programování. .NET poskytuje možnosti pro aplikace a služby jako responzivního a elastické se snadným ovládáním, úroveň jazyka asynchronní programovací modely v C#, VB, a F#.

## <a name="why-write-async-code"></a>Proč psát asynchronní kód?

Moderní aplikace využívat rozsáhlé vstupně-výstupní operace souboru a sítě. Vstupně-výstupní operace rozhraní API tradičně bloku ve výchozím nastavení, výsledkem je špatné uživatelských prostředí a využití hardwaru Pokud nechcete učí a používají složité vzorce. Úkolově orientovanou asynchronní rozhraní API a úrovni jazyka asynchronní programovací model Invertovat tento model, provádění asynchronní provádění výchozím nastavení se několik nových konceptů a další.

Asynchronní kód má následující vlastnosti:

* Další požadavky na server zpracovává pomocí čekajících vláken zpracovávat další požadavky při čekání na vstupně-výstupních požadavků k vrácení.
* Umožňuje UI se více přizpůsobovat čekajících vláken interakce s uživatelským rozhraním při čekání na vstupně-výstupních požadavků a přechod dlouhotrvající práci do jiné jader procesoru.
* Řadu novějších rozhraní API .NET jsou asynchronní.
* Je snadné napsat asynchronní kód v .NET!

## <a name="whats-next"></a>Co dále?

Další informace najdete v tématu [asynchronní do hloubky](async-in-depth.md) tématu.

[Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) téma poskytuje přehled o tři asynchronních programovacích vzorech podporovány v rozhraní .NET:  
  
- [Asynchronní Programovací Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starší verze)  
  
- [Událost asynchronní vzor založený (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starší verze)  
  
- [Založený na úlohách asynchronního vzoru (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (doporučeno pro vývoj nových projektů)  

Další informace o doporučených programovací model založený na úlohách najdete v článku [asynchronní programování založené na úlohách](parallel-programming/task-based-asynchronous-programming.md) tématu.
