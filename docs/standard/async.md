---
title: Asynchronní přehled
description: Přečtěte si, jak je asynchronní programování klíčovou technikou, která usnadňuje zpracování blokujících vstupně-výstupních operací a souběžných operací s více jádry.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: 2f76eb7d2b769b59809bec81aefacb7cec90a450
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106691"
---
# <a name="async-overview"></a>Asynchronní přehled

Ještě nejste tak dlouho, ale aplikace jsou rychlejší, protože si koupíte novější počítač nebo server a tento trend se zastavil. Ve skutečnosti se vrátila zpět. Mobilní telefony se zobrazily s 1GHz s jedním jádrem ARM a úlohami serveru, které jsou převedené na virtuální počítače. Uživatelé pořád chtějí reagovat na uživatelské rozhraní a obchodní vlastníci, kteří chtějí servery, které se škálují podle jejich podnikání. Přechod do mobilního a cloudu a naplnění Internetu připojeného k Internetu z >ch verzí 3B uživatelů má za následek novou sadu vzorů softwaru. 

- Očekává se, že klientské aplikace budou vždycky zapnuté, vždy se připojí a nepřetržitě reagují na interakci s uživatelem (například dotykové ovládání) s vysokým hodnocením v obchodě s aplikacemi.
- U služeb se očekává, že budou zpracovávat špičky v provozu díky řádnému škálování směrem nahoru a dolů. 

Asynchronní programování je klíčovou technikou, která usnadňuje zpracování blokujících vstupně-výstupních operací a souběžných operací s více jádry. .NET poskytuje možnosti pro aplikace a služby, které je možné reagovat a elastický pomocí snadno použitelných, asynchronních programovacích modelů na úrovni C#jazyka v jazycích, F#VB a.

## <a name="why-write-async-code"></a>Proč psát asynchronní kód?

Moderní aplikace využívají v/v rozsáhlé soubory a síťové operace. I/O rozhraní API tradičně standardně blokují, což má za následek špatné uživatelské prostředí a využití hardwaru, pokud se nechcete naučit a používat náročné vzory. Asynchronní rozhraní API založené na úlohách a jejich modul asynchronního programování na úrovni jazyka invertují tento model, což provádí asynchronní spouštění ve výchozím nastavení s několika novými koncepty pro učení.

Asynchronní kód má následující vlastnosti:

- Zpracovává více požadavků serveru tím, že vrací vlákna pro zpracování více požadavků při čekání na vrácení vstupně-výstupních požadavků.
- Umožňuje, aby uživatelská rozhraní lépe reagovaly tím, že při čekání na požadavky na vstupně-výstupní operace vychází z vlákna na interakci uživatelského rozhraní a přechodem dlouhotrvající práce na jiné jádra procesoru.
- Mnohé z novějších rozhraní API .NET jsou asynchronní.
- Psaní asynchronního kódu v rozhraní .NET je snadné.

## <a name="whats-next"></a>Co dále?

Další informace naleznete [v tématu Async v](async-in-depth.md) rámci hloubky.

Téma o [asynchronních programovacích vzorcích](asynchronous-programming-patterns/index.md) poskytuje přehled tří asynchronních programovacích vzorů podporovaných v rozhraní .NET:  
  
- [Asynchronní programovací model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) dřívější  
  
- [Asynchronní vzor založený na událostech (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) dřívější  
  
- [Asynchronní vzor založený na úlohách (klepnutím)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (doporučuje se pro nový vývoj)  

Další informace o doporučeném programovacím modelu založeném na úlohách naleznete v tématu věnovaném [asynchronnímu programování založenému](parallel-programming/task-based-asynchronous-programming.md) na úlohách.
