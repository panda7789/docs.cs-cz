---
title: Asynchronní přehled
description: Přečtěte si, jak je asynchronní programování klíčovou technikou, která usnadňuje zpracování blokujících vstupně-výstupních operací a souběžných operací s více jádry.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: d649bc3a92d3bb834b3bc4f7d3c1bcb0f9417375
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159725"
---
# <a name="async-overview"></a>Asynchronní přehled

Ještě nejste tak dlouho, ale aplikace jsou rychlejší, protože si koupíte novější počítač nebo server a tento trend se zastavil. Ve skutečnosti se vrátila zpět. Mobilní telefony se zobrazily s 1GHz s jedním jádrem ARM a úlohami serveru, které jsou převedené na virtuální počítače. Uživatelé pořád chtějí reagovat na uživatelské rozhraní a obchodní vlastníci, kteří chtějí servery, které se škálují podle jejich podnikání. Přechod do mobilního a cloudu a naplnění Internetu připojeného k Internetu z >ch verzí 3B uživatelů má za následek novou sadu vzorů softwaru.

- Očekává se, že klientské aplikace budou vždycky zapnuté, vždy se připojí a nepřetržitě reagují na interakci s uživatelem (například dotykové ovládání) s vysokým hodnocením v obchodě s aplikacemi.
- U služeb se očekává, že budou zpracovávat špičky v provozu díky řádnému škálování směrem nahoru a dolů.

Asynchronní programování je klíčovou technikou, která usnadňuje zpracování blokujících vstupně-výstupních operací a souběžných operací s více jádry. Rozhraní .NET poskytuje možnosti pro aplikace a služby, které je možné reagovat a elastický pomocí snadno použitelných a prostředí asynchronních programovacích modelů C#na úrovni jazyka v F#, Visual Basic a.

## <a name="why-write-async-code"></a>Proč psát asynchronní kód?

Moderní aplikace využívají v/v rozsáhlé soubory a síťové operace. I/O rozhraní API tradičně standardně blokují, což má za následek špatné uživatelské prostředí a využití hardwaru, pokud se nechcete naučit a používat náročné vzory. Asynchronní rozhraní API založené na úlohách a jejich modul asynchronního programování na úrovni jazyka invertují tento model, což provádí asynchronní spouštění ve výchozím nastavení s několika novými koncepty pro učení.

Asynchronní kód má následující vlastnosti:

- Zpracovává více požadavků serveru tím, že vrací vlákna pro zpracování více požadavků při čekání na vrácení vstupně-výstupních požadavků.
- Umožňuje, aby uživatelská rozhraní lépe reagovaly tím, že při čekání na požadavky na vstupně-výstupní operace vychází z vlákna na interakci uživatelského rozhraní a přechodem dlouhotrvající práce na jiné jádra procesoru.
- Mnohé z novějších rozhraní API .NET jsou asynchronní.
- Psaní asynchronního kódu v rozhraní .NET je snadné.

## <a name="whats-next"></a>Co dále?

Další informace naleznete [v tématu Async v rámci hloubky](async-in-depth.md) .

Téma o [asynchronních programovacích vzorcích](asynchronous-programming-patterns/index.md) poskytuje přehled tří asynchronních programovacích vzorů podporovaných v rozhraní .NET:  
  
- [Asynchronní programovací model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starší verze)  
  
- [Asynchronní vzor založený na událostech (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starší verze)  
  
- [Asynchronní vzor založený na úlohách (klepněte na)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (doporučeno pro nový vývoj)  

Další informace o doporučeném programovacím modelu založeném na úlohách naleznete v tématu věnovaném [asynchronnímu programování založenému](parallel-programming/task-based-asynchronous-programming.md) na úlohách.
