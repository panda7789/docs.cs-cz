---
title: Přehled gRPC-gRPC pro vývojáře WCF
description: Seznamte se se sadou principů, které vyvíjejí vývoj gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: a0811adadc617097d86edc5f845c42a7e90f560f
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542920"
---
# <a name="grpc-overview"></a>gRPC – přehled

Po prohlédnutí Genesis Windows Communication Foundation (WCF) a gRPC v poslední části Tato kapitola zohledňuje některé klíčové funkce gRPC a jejich porovnání s WCF.

ASP.NET Core 3,0 je první verze ASP.NET, která nativně podporuje gRPC jako občana první třídy, s týmy Microsoftu, které přispívají k oficiální implementaci rozhraní .NET gRPC. Doporučuje se pro vytváření distribuovaných aplikací s .NET, které mohou spolupracovat se všemi ostatními hlavními programovacími jazyky a architekturami.

## <a name="key-principles"></a>Hlavní principy

Jak je popsáno v kapitole 1, Google chtěla použít zavedení HTTP/2 k nahrazení Stubby, jeho interní infrastruktury RPC pro obecné účely. gRPC založené na Stubby teď můžou využít standardizaci a by rozšířily její použitelnost na Mobile Computing, Cloud a Internet věcí.

Za tímto účelem vytvořila sada [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) sadu principů, které by se řídily gRPC. V následujícím seznamu jsou uvedeny nejdůležitější ty, které se hlavně týkají maximalizace usnadnění přístupu a použitelnosti:

- **Free a Open** – všechny artefakty by měly být open source s licencováním, které nebrání vývojářům v přijímání gRPC.
- **Pokrytí a jednoduchost** – gRPC by měly být k dispozici napříč všemi oblíbenými platformami a dostatečně snadné pro sestavování na jakékoli platformě.
- **Interoperabilita a dosah** – je vhodné používat gRPC v jakékoli síti bez ohledu na šířku pásma nebo latenci pomocí široce dostupných síťových standardů.
- **Obecný účel a** výkon – rozhraní by mělo být použitelné v rámci široké škály případů použití, aniž by to ohrozilo výkon.
- **Streaming** – protokol by měl poskytovat sémantiku streamování pro velké datové sady nebo asynchronní zasílání zpráv.
- **Výměna metadat** – protokol umožňuje zpracovávat neobchodní data, jako jsou tokeny ověřování, odděleně od skutečných obchodních dat.
- **Standardizované stavové kódy** – proměnlivost chybových kódů by měla být snížena, aby se zajistilo, že se postará rozhodnutí. V případě, že je potřeba další, rozsáhlejší zpracování chyb, by měl být k dispozici mechanismus pro správu tohoto serveru v rámci výměny metadat.

>[!div class="step-by-step"]
>[Předchozí](introduction.md)
>[Další](approach.md)
