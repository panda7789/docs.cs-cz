---
title: Rozhraní Definition Language – gRPC pro vývojáře WCF
description: Představujeme IDL vyrovnávací paměti protokolu.
ms.date: 09/02/2019
ms.openlocfilehash: 1f304502bd0091f753a3d2f7854298f4bbf983f1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967631"
---
# <a name="interface-definition-language"></a>Interface Definition Language

Pomocí WCF mohou služby vystavovat popisná metadata pomocí jazyka WSDL (Web Service Definition Language), který je generován dynamicky pomocí reflexe rozhraní .NET za běhu. Vývojáři můžou tato metadata použít k vygenerování klientů pro tyto služby, případně i v jiných jazycích, pokud se používá vazba neutrální na platformě, jako je třeba SOAP přes HTTP.

gRPC používá rozhraní IDL (Interface Definition Language) z vyrovnávacích pamětí protokolu. Zásobníky vyrovnávací paměti IDL je vlastní platforma neutrální jazyk s otevřenou specifikací. Vývojáři dovážejí `.proto` soubory pro popis služeb společně s jejich vstupy a výstupy. Tyto soubory `.proto` pak můžete použít k vygenerování zástupných procedur specifických pro jazyk nebo platformu pro klienty a servery, což umožňuje komunikaci více různých platforem. Díky sdílení `.proto` souborů můžou týmy vygenerovat kód pro použití všech ostatních služeb, aniž by museli převzít závislost kódu.

Jednou z výhod Protobuf IDL je, že jako vlastní jazyk umožňuje gRPC naprostou jazyk a platformu nezávislá a neupřednostňuje žádnou technologii přes jinou.

IDL Protobuf je také navržen pro lidi jak pro čtení, tak pro zápis, zatímco WSDL je určena jako strojově čitelný nebo zapisovatelný formát. Změna WSDL služby WCF obvykle vyžaduje, aby se prováděly změny samotného kódu služby, spustila službu a znovu vygenerovala soubor WSDL ze serveru. Naproti tomu `.proto` soubor, změny se snadno aplikují pomocí textového editoru a automaticky se přesměrují do vygenerovaného kódu. Visual Studio 2019 sestaví `.proto` soubory na pozadí při jejich ukládání; Při použití jiných editorů, jako je VS Code, se změny použijí při sestavení projektu.

Ve srovnání s XML a zejména SOAP, zprávy kódované pomocí Protobuf mají mnoho výhod. Protobuf zprávy mohou být menší než stejná data serializovaná jako SOAP XML a kódování, dekódování a jejich přenos přes síť může být rychlejší.

Potenciální nevýhody Protobuf ve srovnání s protokolem SOAP je to, že vzhledem k tomu, že zprávy nejsou čitelné pro čtení, jsou pro ladění obsahu zprávy vyžadovány další nástroje.

> [!TIP]
> gRPC *podporuje* reflexi serveru pro dynamický přístup ke službám bez předem kompilovaných zástupných procedur, i když je pro obecné nástroje určené pro obecné nástroje než pro klienty pro konkrétní aplikace. Další informace o reflexi serveru gRPC najdete v tématu [gRPC/gRPC](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) úložiště na GitHubu.

> [!NOTE]
> Binární formát služby WCF, který se používá s vazbou NetTCP, je mnohem větší než Protobuf z hlediska komprimace a výkonu, ale NetTCP se dá použít jenom mezi klienty a servery .NET, zatímco Protobuf je řešení pro různé platformy.

>[!div class="step-by-step"]
>[Předchozí](approach.md)
>[Další](network-protocols.md)
