---
title: Rozhraní Definition Language – gRPC pro vývojáře WCF
description: Představujeme IDL vyrovnávací paměti protokolu.
ms.date: 09/02/2019
ms.openlocfilehash: 841f041ae350e76e648c71f9d6d113b9d39e0d3b
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543206"
---
# <a name="interface-definition-language"></a>Interface Definition Language

Pomocí Windows Communication Foundation (WCF) mohou služby vystavovat metadata popisu pomocí jazyka WSDL (Web Service Definition Language). WSDL se generuje dynamicky pomocí reflexe .NET za běhu. Vývojáři můžou tato metadata použít k vygenerování klientů pro tyto služby, případně i v jiných jazycích, pokud používají pro platformu neutrální vazbu, jako je třeba SOAP přes HTTP.

gRPC používá rozhraní IDL (Interface Definition Language) z vyrovnávacích pamětí protokolu. Zásobníky vyrovnávací paměti IDL je vlastní platforma neutrální jazyk s otevřenou specifikací. Vývojáři vytvářejí `.proto` soubory pro popis služeb, spolu se svými vstupy a výstupy. Tyto soubory `.proto` pak můžete použít k vygenerování zástupných procedur specifických pro jazyk nebo platformu pro klienty a servery, což umožňuje komunikaci více různých platforem. Pomocí sdílení `.proto` souborů můžou týmy vygenerovat kód pro použití všech ostatních služeb, aniž by museli brát v úvahu závislost kódu.

Jednou z výhod Protobuf IDL je, že jako vlastní jazyk umožňuje gRPC naprostou jazyk a platformu nezávislá a neupřednostňuje žádnou technologii přes jinou.

IDL Protobuf je také navržen pro lidi jak pro čtení, tak pro zápis, zatímco WSDL je určena jako strojově čitelný nebo zapisovatelný formát. Změna WSDL služby WCF obvykle vyžaduje změnu služby, spuštění služby a opětovné generování souboru WSDL ze serveru. Naproti tomu `.proto` soubor, změny se snadno aplikují pomocí textového editoru a automaticky se přesměrují do vygenerovaného kódu. Visual Studio 2019 sestaví `.proto` soubory na pozadí při jejich ukládání. S jinými editory, jako je například VS Code, se změny uplatní při sestavení projektu.

Ve srovnání s XML a zejména SOAP, zprávy zakódované pomocí Protobuf mají mnoho výhod. Protobuf zprávy mohou být menší než stejná data serializovaná jako SOAP XML a kódování, dekódování a přenos přes síť může být rychlejší.

Potenciální nevýhody Protobuf ve srovnání s protokolem SOAP je to, že protože tyto zprávy nejsou čitelné pro lidi, jsou pro ladění obsahu zprávy vyžadovány další nástroje.

> [!TIP]
> gRPC *podporuje* reflexi serveru pro dynamický přístup ke službám bez předem kompilovaných zástupných procedur, i když je pro obecné nástroje určené pro obecné nástroje než pro klienty pro konkrétní aplikace. Další informace najdete v tématu [protokol reflexe serveru GRPC](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) na GitHubu.

> [!NOTE]
> Binární formát služby WCF, který se používá s vazbou NetTCP, je mnohem blíže Protobuf z hlediska komprimace a výkonu. NetTCP je ale možné použít jenom mezi klienty rozhraní .NET a servery, zatímco Protobuf je řešení pro různé platformy.

>[!div class="step-by-step"]
>[Předchozí](approach.md)
>[Další](network-protocols.md)
