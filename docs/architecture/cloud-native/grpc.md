---
title: gRPC
description: Další informace o gRPC, jeho roli v cloud-nativní aplikace, a jak se liší od HTTP RESTful komunikace.
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 28a07ad5ec105d3fc5b65e4cf0ac0cd85eb16627
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80524171"
---
# <a name="grpc"></a>gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Zatím jsme se v této knize zaměřili na komunikaci [založenou na REST.](https://docs.microsoft.com/azure/architecture/best-practices/api-design) Viděli jsme, že REST je flexibilní architektonický styl, který definuje operace založené na CRUD proti prostředkům entity. Klienti interagují s prostředky v rámci protokolu HTTP pomocí modelu komunikace požadavku a odpovědi. Zatímco REST je široce implementována, novější komunikační technologie, gRPC, získala obrovskou dynamiku v celé komunitě nativní pro cloud.

## <a name="what-is-grpc"></a>Co je gRPC?

gRPC je moderní, vysoce výkonný rámec, který vyvíjí starý [protokol vzdáleného volání procedur (RPC).](https://en.wikipedia.org/wiki/Remote_procedure_call) Na úrovni aplikace gRPC zjednodušuje zasílání zpráv mezi klienty a back-endové služby. GRPC, pocházející z Googlu, je open source a je součástí ekosystému [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) nativních cloudových nabídek. CNCF považuje gRPC za [inkubační projekt](https://github.com/cncf/toc/blob/master/process/graduation_criteria.adoc). Inkubace znamená, že koncoví uživatelé používají technologii ve výrobních aplikacích a projekt má zdravý počet přispěvatelů.

Typická klientská aplikace gRPC zpřístupní místní v procesu, která implementuje obchodní operaci. Pod kryty, že místní funkce vyvolá jinou funkci na vzdáleném počítači. Co se zdá být místní volání v podstatě stane transparentní mimoprocesvolání vzdálené služby. Instalace vzdáleného volání procedur abstrahuje komunikaci, serializaci a provádění sítí typu point-to-point mezi počítači.

V aplikacích nativních pro cloud vývojáři často pracují napříč programovacími jazyky, architekturami a technologiemi. Tato *interoperabilita* komplikuje smlouvy o smenít a instalatérské práce potřebné pro komunikaci mezi platformami.  gRPC poskytuje "jednotnou vodorovnou vrstvu", která tyto obavy abstrahuje. Vývojáři kód v jejich nativní platformě zaměřené na obchodní funkce, zatímco gRPC zpracovává komunikaci instalatérské práce.

gRPC nabízí komplexní podporu napříč nejoblíbenějšími vývojovými zásobníky, včetně Java, JavaScriptu, C#, Go, Swiftu a NodeJS.

## <a name="grpc-benefits"></a>gRPC Výhody

gRPC používá HTTP/2 pro svůj transportní protokol. Zatímco je kompatibilní s HTTP 1.1, HTTP/2 nabízí mnoho pokročilých funkcí:

- Binární protokol pro přenos dat - na rozdíl od HTTP 1.1, který odesílá data jako jasný text.
- Podpora multiplexování pro odesílání více paralelních požadavků přes stejné připojení - HTTP 1.1 omezuje zpracování na jednu zprávu požadavku a odpovědi najednou.
- Obousměrná plně duplexní komunikace pro současné odesílání požadavků klientů i odpovědí serveru.
- Integrované streamování umožňující požadavky a odpovědi na asynchronně streamovat velké datové sady.

gRPC je lehký a vysoce výkonný. Může být až 8x rychlejší než serializace JSON se zprávami o 60-80% menšími. V jazyce [WCF (Microsoft Windows Communication Foundation)](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) překračuje výkon gRPC rychlost a efektivitu vysoce optimalizovaných [vazeb NetTCP](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8). Na rozdíl od NetTCP, který upřednostňuje microsoft zásobníku, gRPC je cross-platformní.

## <a name="protocol-buffers"></a>Vyrovnávací paměti protokolů

gRPC zahrnuje technologii s otevřeným zdrojovým kódem nazvanou [Protocol Buffers](https://developers.google.com/protocol-buffers/docs/overview). Poskytují vysoce efektivní a neutrální serializační formát pro serializaci strukturovaných zpráv, které si služby vzájemně odesílají. Pomocí jazyka IDL (Interface Definition Language) napříč platformami definují vývojáři smlouvu o poskytování služeb pro každou mikroslužbu. Kontrakt, implementovaný jako textový `.proto` soubor, popisuje metody, vstupy a výstupy pro každou službu. Stejný soubor smlouvy lze použít pro klienty gRPC a služby postavené na různých vývojových platformách.

Pomocí proto souboru kompilátor Protobuf , `protoc`generuje kód klienta i služby pro cílovou platformu. Kód obsahuje následující součásti:

- Objekty silného typu sdílené klientem a službou, které představují operace služby a datové prvky pro zprávu.
- Základní třída silného typu s požadovanou síťovou inmisací, kterou může vzdálená služba gRPC dědit a rozšiřovat.
- Se zakázaným inzerováním klienta, který obsahuje požadované instalace k vyvolání vzdálené služby gRPC.

Za běhu je každá zpráva serializována jako standardní reprezentace Protobuf a vyměňována mezi klientem a vzdálenou službou. Na rozdíl od JSON nebo XML protobuf zprávy jsou serializovány jako kompilované binární bajty.

Kniha [gRPC pro vývojáře WCF](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/), která je k dispozici na webu Microsoft Architecture, poskytuje podrobné pokrytí vyrovnávacích pamětí gRPC a protokolu.

## <a name="grpc-support-in-net"></a>podpora gRPC v rozhraní .NET

gRPC je integrován do sady .NET Core 3.0 SDK nebo novější. Podporují následující nástroje:

- Visual Studio 2019, verze 16.3 nebo novější, s nainstalovanou úlohou pro vývoj webu.
- Visual Studio Code
- rozhraní SE kontinu pro dotnet

Sada SDK obsahuje nástroje pro směrování koncových bodů, integrované ioc a protokolování. Open source webový server Kestrel podporuje připojení HTTP/2. Obrázek 4-20 znázorňuje šablonu Visual Studia 2019, která veleše kostru projektu pro službu gRPC. Všimněte si, jak rozhraní .NET Core plně podporuje Windows, Linux a macOS.

![podpora gRPC ve Visual Studiu 2019](./media/visual-studio-2019-grpc-template.png)

**Obrázek 4-20**. podpora gRPC ve Visual Studiu 2019
  
Obrázek 4-21 znázorňuje službu kostry gRPC vygenerovanou z integrovaného lešení, které je součástí sady Visual Studio 2019.  

![projekt gRPC v Sadě Visual Studio 2019](./media/grpc-project.png  )

**Obrázek 4-21**. projekt gRPC v Sadě Visual Studio 2019

Na předchozím obrázku si poznamenejte soubor popisu proto a kód služby. Jak uvidíte v nejbližší době, Visual Studio generuje další konfiguraci v spouštěcí třídě i základní soubor projektu.

## <a name="grpc-usage"></a>gRPC použití

Favor gRPC pro následující scénáře:

- Synchronní back-endmikroslužeb mikroslužeb, kde je nutná okamžitá odpověď pokračovat ve zpracování.
- Polyglot prostředí, které potřebují k podpoře smíšené programovací platformy.
- Nízká latence a vysoká propustnost komunikace, kde je rozhodující výkon.
- Komunikace v reálném čase point-to-point - gRPC může tlačit zprávy v reálném čase bez dotazování a má vynikající podporu obousměrného streamování.
- Síťově omezená prostředí – binární gRPC zprávy jsou vždy menší než ekvivalentní textová zpráva JSON.

V té době, tohoto psaní, gRPC se používá především s back-endové služby. Většina moderních prohlížečů nemůže poskytnout úroveň ovládacího prvku HTTP/2 potřebnou pro podporu front-endového gRPC klienta. To znamená, že je tu [brzy iniciativa,](https://devblogs.microsoft.com/aspnet/grpc-web-experiment/) která umožňuje gRPC komunikaci z prohlížeče-založené aplikace postavené s JavaScript nebo Blazor WebAssembly technologií. [GRPC-Web pro rozhraní .NET](https://github.com/grpc/grpc/blob/master/doc/PROTOCOL-WEB.md) umožňuje aplikaci ASP.NET Core gRPC podporovat funkce gRPC v aplikacích prohlížeče:

- Klienti generovaný kódem silného typu
- Kompaktní zprávy Protobuf
- Serverové vysílání

## <a name="grpc-implementation"></a>gRPC implementace

Referenční architektura mikroslužeb, [eShop na kontejnerech od Microsoftu,](https://github.com/dotnet-architecture/eShopOnContainers)ukazuje, jak implementovat služby gRPC v aplikacích .NET Core. Obrázek 4-22 představuje back-end architekturu.

![Backendová architektura pro eShop na kontejnerech](./media/eshop-with-aggregators.png)

**Obrázek 4-22**. Backendová architektura pro eShop na kontejnerech

Na předchozím obrázku si všimněte, jak eShop zahrnuje [back-end pro frontendy vzoru](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) (BFF) tím, že vystavuje více bran rozhraní API. Diskutovali jsme o vzoru BFF dříve v této kapitole. Věnujte velkou pozornost mikroslužbě Agregátor (šedě), která je na místě mezi bránou rozhraní API web-shopping a back-endem nákupních mikroslužeb. Agregátor obdrží jeden požadavek od klienta, odešle jej do různých mikroslužeb, agreguje výsledky a odešle je zpět žádajícímu klientovi. Tyto operace obvykle vyžadují synchronní komunikaci, aby vznikla okamžitá odpověď. V eShopu se back-endové hovory z agregátoru provádějí pomocí gRPC, jak je znázorněno na obrázku 4-23.

![gRPC v eShopu na kontejnerech](./media/grpc-implementation.png)

**Obrázek 4-23**. gRPC v eShopu na kontejnerech

gRPC komunikace vyžaduje klientské i serverové komponenty. Na předchozím obrázku si všimněte, jak agregátor nákupů implementuje klienta gRPC. Klient provádí synchronní volání gRPC (červeně) pro back-endové mikroslužby, z nichž každý implementuje server gRPC. Klient i server využívají integrované instalace gRPC ze sady .NET Core 3.0 SDK. *Zástupné procedury* na straně klienta poskytují instalace pro vyvolání vzdálených volání gRPC. Součásti na straně serveru poskytují gRPC instalatérství, které mohou dědit a využívat vlastní třídy služeb.

Mikroslužby, které zveřejňují rozhraní RESTful API a gRPC komunikace vyžadují více koncových bodů pro správu provozu. Byste otevřít koncový bod, který naslouchá pro přenosy HTTP pro volání RESTful a další pro volání gRPC. Koncový bod gRPC musí být nakonfigurován pro protokol HTTP/2, který je vyžadován pro komunikaci gRPC.

Zatímco se snažíme oddělit mikroslužby s vzory asynchronní komunikace, některé operace vyžadují přímé volání. gRPC by měla být primární volbou pro přímou synchronní komunikaci mezi mikroslužbami. Jeho vysoce výkonný komunikační protokol založený na HTTP/2 a vyrovnávacích pamětí protokolu z něj činí ideální volbu.

## <a name="looking-ahead"></a>Výhled do budoucna

Při pohledu do budoucna bude gRPC i nadále získávat trakci pro cloud-nativní systémy. Výhody výkonu a snadný rozvoj jsou přesvědčivé. Nicméně, REST bude pravděpodobně asi na dlouhou dobu. Vyniká pro veřejně exponovaná řešení API a z důvodů zpětné kompatibility.

>[!div class="step-by-step"]
>[Předchozí](service-to-service-communication.md)
>[další](service-mesh-communication-infrastructure.md)
