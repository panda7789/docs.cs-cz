---
title: Přehled gRPC-gRPC pro vývojáře WCF
description: Seznamte se se sadou principů, které vyvíjejí vývoj gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6980b473a6f9852a4e4f396355e98e2d3300cabe
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846648"
---
# <a name="grpc-overview"></a>gRPC – přehled

Po zobrazení genesisy WCF a gRPC v poslední kapitole bude tato kapitola brát v úvahu některé klíčové funkce gRPC a jejich porovnání s WCF.

ASP.NET Core 3,0 je první verze ASP.NET, která nativně podporuje gRPC jako občana první třídy, s týmy Microsoftu, které přispívají k oficiální implementaci rozhraní .NET gRPC. Doporučuje se jako nejlepší přístup pro vytváření distribuovaných aplikací s .NET, které mohou spolupracovat se všemi ostatními hlavními programovacími jazyky a architekturami.

## <a name="key-principles"></a>Klíčové principy

Jak je popsáno v kapitole 1, Google chtěla použít zavedení HTTP/2 k nahrazení Stubby, jeho interní infrastruktury RPC pro obecné účely. gRPC, na základě Stubby, teď můžou využít standardizaci a by rozšířila její použitelnost na Mobile Computing, Cloud a Internet věcí.

Za tímto účelem vytvořila sada [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) sadu principů, které by se řídily gRPC. V následujícím seznamu jsou uvedeny nejdůležitější ty, které se hlavně týkají maximalizace usnadnění přístupu a použitelnosti:

- **Free a Open** – všechny artefakty by měly být open source s licencováním, které nebrání vývojářům v přijímání gRPC.
- **Pokrytí a jednoduchost** – gRPC by měly být k dispozici napříč všemi oblíbenými platformami a dostatečně snadno, aby je bylo možné vytvářet na jakékoli platformě.
- **Interoperabilita a dosah** – je vhodné používat gRPC v libovolné síti, bez ohledu na šířku pásma nebo latenci, a to s využitím široce dostupných síťových standardů.
- **Obecný účel a** výkon – rozhraní by mělo být použitelné v rámci široké škály případů použití, aniž by došlo k narušení výkonu.
- **Streaming** – protokol by měl poskytovat sémantiku streamování pro velké datové sady nebo asynchronní zasílání zpráv.
- **Výměna metadat** – protokol povoluje zpracování neobchodních dat, jako jsou tokeny ověřování, odděleně od skutečných obchodních dat.
- **Standardizované stavové kódy** – proměnlivost chybových kódů by měla být snížena, aby se zajistilo, že se postará rozhodnutí o zpracování chyb a v případě nutnosti dalšího podrobnějšího zpracování chyb by měl být k dispozici mechanismus pro správu v rámci výměny metadat.

>[!div class="step-by-step"]
>[Předchozí](introduction.md)
>[Další](approach.md)
