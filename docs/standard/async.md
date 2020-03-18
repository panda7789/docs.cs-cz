---
title: Přehled asynchronizací
description: Zjistěte, jak je asynchronní programování klíčovou technikou, která usnadňuje zpracování blokování vstupně-va a souběžných operací na více jádrech.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: d649bc3a92d3bb834b3bc4f7d3c1bcb0f9417375
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159725"
---
# <a name="async-overview"></a>Přehled asynchronizací

Není to tak dávno, aplikace dostal rychleji jednoduše tím, že koupí novější PC nebo server a pak se tento trend zastavil. Ve skutečnosti se to obrátilo. Mobilní telefony se objevily s jednojádrovými čipy ARM o 1ghz a serverovými úlohami převedenými na virtuální zařízení. Uživatelé stále chtějí responzivní uživatelské rozhraní a vlastníci firem chtějí servery, které se škálují podle svého podnikání. Přechod na mobilní a cloud a počet uživatelů >3B připojených k internetu vyústil v novou sadu softwarových vzorců.

- Očekává se, že klientské aplikace budou vždy zapnuté, vždy připojené a neustále reagují na interakci s uživatelem (například dotykové ovládání) s vysokým hodnocením obchodu s aplikacemi!
- Služby se očekává, že zpracování špičky v provozu řádně škálování nahoru a dolů.

Asynchronní programování je klíčová technika, která usnadňuje zpracování blokování vstupně-v a o a souběžných operací na více jádrech. Rozhraní .NET poskytuje možnost, aby aplikace a služby reagovaly a byly elastické díky snadno použitelným asynchronním programovacím modelům na jazykové úrovni v jazyce C#, Visual Basic a F#.

## <a name="why-write-async-code"></a>Proč psát asynchronní kód?

Moderní aplikace využívají rozsáhlé vstupně-to-do souboru a síťové vstupně-up. Vstupně-blouskározhraní tradičně blokují ve výchozím nastavení, což má za následek špatné uživatelské prostředí a využití hardwaru, pokud se nechcete učit a používat náročné vzory. Asynchronní rozhraní API založená na úlohách a asynchronní programovací model na úrovni jazyka invertují tento model, takže asynchronní spuštění je výchozí s několika novými koncepty, které se mají naučit.

Asynchronní kód má následující charakteristiky:

- Zpracovává další požadavky serveru tím, že poskytuje podprocesy pro zpracování více požadavků při čekání na vstupně-va požadavky na vrácení.
- Umožňuje uživatelské rozhraní, které mají být citlivější tím, že dává podprocesů interakce uživatelského rozhraní při čekání na vstupně-va požadavky a přechodem dlouhotrvající práce na jiné jádra procesoru.
- Mnoho novějších rozhraní API ROZHRANÍ .NET je asynchronních.
- Je snadné napsat asynchronní kód v rozhraní .NET!

## <a name="whats-next"></a>Co dále?

Další informace naleznete v tématu [Async in depth.](async-in-depth.md)

Téma [Asynchronní programovací vzory](asynchronous-programming-patterns/index.md) poskytuje přehled tří asynchronních programovacích vzorů podporovaných v rozhraní .NET:  
  
- [Asynchronní programovací model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starší verze)  
  
- [Asynchronní vzor založený na událostech (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starší verze)  
  
- [Asynchronní vzor založený na úlohách (TAP) (doporučeno](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) pro nový vývoj)  

Další informace o doporučeném programovacím modelu založeném na úlohách naleznete v tématu [asynchronního programování na základě úloh.](parallel-programming/task-based-asynchronous-programming.md)
