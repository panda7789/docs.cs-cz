---
title: Async – přehled
description: Zjistěte, jak je asynchronní programování klíče techniku, která usnadňuje přehledné zpracování blokování vstupně-výstupních operací a souběžných operací na víc jader.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: b9d612186e1051644e8d4ae9476b8fafd811deb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="async-overview"></a>Async – přehled

Není to tak dávno aplikace získali rychlejší jednoduše si novější počítač nebo server a pak tento trend zastavena. Ve skutečnosti obrácený. Mobilní telefon zobrazovaly s jedním jádrem 1ghz ARM čipy a úlohy serveru přešla do virtuálních počítačů. Uživatelé stále chcete citlivé uživatelské rozhraní a vlastníci společnosti budou chtít, aby servery, které škálovat s jejich podnikání. Přechod mobilních a cloudu a připojené k Internetu naplnění > uživatelé 3B má za následek novou sadu vzory softwaru. 

* Klientské aplikace se měl stále aktivní, vždy připojené a neustále reaguje na interakce uživatele (například touch) s vysokou app store hodnocení!
* Očekává se, že služby zpracování špičky v provozu řádně škálování nahoru a dolů. 

Asynchronní programování je klíče technika, která usnadňuje přehledné zpracování blokování vstupně-výstupních operací a souběžných operací na víc jader. Rozhraní .NET poskytuje možnost pro aplikace a služby reakce a elastické s snadné použití, úroveň jazyka asynchronní programovací modely v C#, VB a F #.

## <a name="why-write-async-code"></a>Proč psát kód asynchronní?

Moderní aplikace využívají rozsáhlé vstupně-výstupní soubor a sítě. Vstupně-výstupních operací rozhraní API tradičně bloku ve výchozím nastavení, výsledkem nízký uživatelského prostředí a využití hardwaru, pokud chcete další informace a využít náročné vzory. Založený na úlohách async rozhraní API a úroveň jazyka asynchronní programovací model Invertovat tento model vytváření asynchronních provádění výchozí s několik nových konceptů Další.

Asynchronní kódu má následující vlastnosti:

* Zpracovává požadavky na další server podle je vláken zpracovat další požadavky při čekání na vstupně-výstupní požadavky vrátit.
* Umožňuje uživatelská být rychlejšího je vláken uživatelského rozhraní interakce při čekání na vstupně-výstupní požadavky a přechod pracovní dlouho běžící na jiné jader procesoru.
* Mnoho novější rozhraní API .NET je asynchronní.
* Je snadné napsat kód asynchronní v rozhraní .NET!

## <a name="whats-next"></a>Co je další?

Další informace najdete v tématu [asynchronní podrobněji](async-in-depth.md) tématu.

[Vzory asynchronního programování](/asynchronous-programming-patterns/index.md) téma obsahuje přehled ze tří asynchronní programování vzorů v rozhraní .NET podporovány:  
  
-   [Asynchronní programování modelu (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starší)  
  
-   [Na základě událostí asynchronní vzor (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starší)  
  
-   [Založený na úlohách asynchronní vzor (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (doporučeno pro nový vývoj)  

Další informace o doporučených založený na úlohách programovací model najdete v tématu [založený na úlohách asynchronní programování](parallel-programming/task-based-asynchronous-programming.md) tématu.
