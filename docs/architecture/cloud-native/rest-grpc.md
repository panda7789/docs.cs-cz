---
title: REST a gRPC
description: Přečtěte si o gRPC, její roli v cloudových nativních aplikacích a o tom, jak se liší od protokolu HTTP REST.
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: 4c829407d494a3529d1fb9953cd3f56f73e90636
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711633"
---
# <a name="rest-and-grpc"></a>REST a gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V této knize jsme se zaměřili na komunikaci na [bázi REST](https://docs.microsoft.com/azure/architecture/best-practices/api-design) . REST je styl architektury, který podporuje interoperabilitu mezi distribuovanými počítačovým systémem. Používá model požadavků a odpovědí, ve kterém každá odpověď ze serveru na požadavek od klienta. V širokém oblíbeným se KLIDně nehodí pro všechny problémy. Novější komunikační technologie, která je oprávněná gRPC, rychle získává oblíbenou a dává se způsobem do cloudového nativního světa.

## <a name="grpc"></a>gRPC

gRPC je open source komunikace pocházející z Google. Je postavená na modelu [vzdáleného volání procedur (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) , který je oblíbený v distribuovaném výpočetním prostředí. Po provedení tohoto modelu zveřejňuje místní klientský program metodu, která provádí operaci. Na pozadí se toto volání vyvolá v rámci distribuované sítě mimo proces. Vývojář kód operace jako místní volání procedury. Základní platforma vyabstrakce síťovou komunikaci, serializaci a spuštění sítě Point-to-Point.

gRPC je moderní architektura RPC, která je odlehčená a vysoce výkonná. Pro svůj transportní protokol používá protokol HTTP/2. I když je kompatibilní s HTTP 1,1, funkce HTTP/2 nabízí mnoho pokročilých možností:

- I když HTTP 1,1 posílá data jako nešifrovaný text, HTTP/2 je binární protokol. Analyzuje data rychleji pomocí méně paměti, snižuje latenci sítě se souvisejícími vylepšeními rychlosti a efektivněji spravuje síťové prostředky.
- I když je protokol HTTP 1,1 omezený na zpracování jednoho požadavku nebo odpovědi na operaci round-trip v čase, protokol HTTP/2 podporuje multiplexování nebo více paralelních požadavků přes stejné připojení.
- HTTP/2 podporuje plně duplexní nebo obousměrnou komunikaci, kdy klient i server můžou komunikovat současně. Klient může odesílat data žádosti současně se serverem, který odesílá data odpovědi zpět.
- Streamování je integrované do HTTP/2, což znamená, že požadavky i odpovědi můžou asynchronně streamovat velké datové sady.
- V kombinaci gRPC a HTTP/2 se výrazně zvyšuje výkon. V [Windows Communication Foundation (WCF)](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) agilním výkon gRPC a překračuje rychlost a efektivitu [vazeb NetTcp](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8). Ale na rozdíl od NetTCP se gRPC neomezuje na jazyky Microsoftu, jako je C# nebo Visual Basic.

gRPC se podporuje na nejoblíbenějších platformách, včetně jazyků C#Java,, golang a NodeJS.

## <a name="protocol-buffers"></a>Vyrovnávací paměti protokolů

gRPC zahrnuje další Open Source technologii s názvem [vyrovnávací paměti protokolu](https://developers.google.com/protocol-buffers/docs/overview) nebo zprávy Protobuf pro odesílání a příjem dat. Podobně jako u [kontraktu dat WCF](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-data-contracts)Protobuf serializovat strukturovaná data pro systémy ke čtení a zápisu. Snižuje režijní náklady, které uživatelsky čitelné formáty, jako je například XML nebo JSON.

Mnoho technik serializace objektů odráží napříč strukturou datových objektů v době běhu. Protobuf vyžaduje, abyste definovali strukturu předem s jazykem nezávislá (jazyk vyrovnávací paměti protokolu). Každá definice je uložená v souboru. proto. Pak pomocí kompilátoru Protobuf "Proton" vygenerujete kód klienta a serveru pro libovolnou z podporovaných platforem. Vygenerovaný kód je optimalizován pro rychlou serializaci/deserializaci dat. V době běhu jsou jednotlivé zprávy zabaleny do kontraktu služby silného typu a serializovány ve standardní reprezentaci Protobuf.

## <a name="grpc-support-in-net"></a>Podpora gRPC v .NET

Rozhraní Microsoft .NET Core Framework 3,0 zahrnuje nástroje a nativní podporu pro gRPC. Obrázek 4-20 ukazuje šablonu sady Visual Studio 2019, která generuje gRPC projekt kostry pro službu gRPC. Všimněte si, jak .NET Core podporuje platformy Windows, Linux a macOS.

![Podpora gRPC v aplikaci Visual Studio 2019](./media/visual-studio-2019-grpc-template.png)

**Obrázek 4-20**. Podpora gRPC v aplikaci Visual Studio 2019

.NET Core 3,0 bez problémů integruje gRPC do své architektury, včetně směrování koncových bodů, integrované podpory IoC a protokolování. Open source webový server Kestrel plně podporuje připojení HTTP/2.

Obrázek 4-21 ukazuje strukturu služby gRPC ve Visual Studiu 2019. Všimněte si, jak struktura složek zahrnuje složky pro soubory a kód služby.

![projekt gRPC v aplikaci Visual Studio 2019](./media/grpc-project.png  )

**Obrázek 4-21**. projekt gRPC v aplikaci Visual Studio 2019

## <a name="grpc-usage"></a>Využití gRPC

gRPC je vhodný pro následující scénáře:

- Nízká latence a komunikace s vysokou propustností. gRPC je ideální pro odlehčené mikroslužby, kde je efektivita nejdůležitější.
- Komunikace v reálném čase Point-to-Point. gRPC má skvělou podporu pro obousměrné streamování. služby gRPC mohou nabízet zprávy v reálném čase bez cyklického dotazování.
- Polyglot prostředí – Nástroj pro gRPC podporuje většinu oblíbených vývojových jazyků, takže pro prostředí s více jazyky je vhodná volba.
- Omezená prostředí sítě – zprávy gRPC jsou serializovány pomocí Protobuf, což je odlehčený formát zprávy. Zpráva gRPC je vždy menší než ekvivalentní zpráva JSON.

V době psaní této knihy mají většina prohlížečů omezené podpory pro gRPC. gRPC intenzivně používá funkce HTTP/2 a bez prohlížeče poskytuje úroveň řízení požadovaná pro webové požadavky na podporu klienta gRPC. gRPC se obvykle používá pro interní mikroslužby pro komunikaci mikroslužeb. Obrázek 4-22 ukazuje jednoduchý, ale běžný vzor použití.

![Vzorce používání gRPC](./media/grpc-usage.png)

**Obrázek 4-22**. vzorce používání gRPC

Všimněte si, že předchozí obrázek je vyvolán front-end přenosem pomocí protokolu HTTP, zatímco mikroslužba back-end používá gRPC.

GRPC se může hrát významnou roli v dethroning dominantnímu postavení REST pro nativní cloudové systémy. Výhody výkonu a snadné vývoje jsou příliš dobré. Bez jakýchkoli chyb však bude klid stále delší dobu trvat. Stále jsou v Excelu pro veřejně vystavená rozhraní API a z důvodů zpětné kompatibility.

>[!div class="step-by-step"]
>[Předchozí](service-to-service-communication.md)
>[Další](service-mesh-communication-infrastructure.md)
