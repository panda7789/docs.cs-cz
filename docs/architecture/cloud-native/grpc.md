---
title: gRPC
description: Přečtěte si o gRPC, její roli v cloudových nativních aplikacích a o tom, jak se liší od komunikace HTTP RESTful.
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: f34b267d7f5c6b4e593841c80df44d1ccbde95ae
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614042"
---
# <a name="grpc"></a>gRPC

V této knize jsme se zaměřili na komunikaci na [bázi REST](https://docs.microsoft.com/azure/architecture/best-practices/api-design) . Viděli jsme, že REST je flexibilní styl architektury, který definuje operace na základě CRUD u prostředků entity. Klienti komunikují s prostředky přes protokol HTTP pomocí komunikačního modelu požadavků a odpovědí. I když je REST široce implementováno, novější komunikační technologie, gRPC, získala obrovský potenciál v rámci cloudové nativní komunity.

## <a name="what-is-grpc"></a>Co je gRPC?

gRPC je moderní, vysoce výkonné rozhraní, které vyvíjí stáří protokolu [RPC (Remote Procedure Call)](https://en.wikipedia.org/wiki/Remote_procedure_call) . Na úrovni aplikace gRPC zjednodušuje zasílání zpráv mezi klienty a back-endové služby. Pocházející z Google, gRPC je open source a součástí ekosystému [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) pro nativní nabídky cloudu. CNCF se považuje za gRPC na [inkubaci projektu](https://github.com/cncf/toc/blob/master/process/graduation_criteria.adoc). Inkubace znamená, že koncoví uživatelé používají technologii v produkčních aplikacích a projekt má dobrý počet přispěvatelů.

Typická klientská aplikace gRPC bude vystavovat místní, vnitroprocesově funkci, která implementuje obchodní operaci. V rámci pokrývá tato místní funkce vyvolá jinou funkci na vzdáleném počítači. To, co se jeví jako místní volání, se v podstatě stal transparentním nezpracovaným voláním vzdálené služby. Instalace rozhraní příkazového informačního protokolu RPC vyabstrakce síťovou komunikaci, serializaci a spouštění mezi počítači.

V cloudových nativních aplikacích vývojáři často pracují v různých programovacích jazycích, architekturách a technologiích. Tato *interoperabilita* ztěžuje kontrakty zpráv a domovníing potřebnou pro komunikaci mezi platformami.  gRPC poskytuje "jednotnou vodorovnou vrstvu", která tyto otázky vyabstrakcí. Vývojářům kód v jejich nativní platformě se zaměřuje na obchodní funkce, zatímco gRPC zpracovává komunikaci při komunikaci.

gRPC nabízí komplexní podporu napříč nejoblíbenějšími vývojovými zásobníky, včetně jazyků Java, JavaScript, C#, cestách, SWIFT a NodeJS.

## <a name="grpc-benefits"></a>Výhody gRPC

gRPC používá pro svůj transportní protokol HTTP/2. I když je kompatibilní s HTTP 1,1, funkce HTTP/2 nabízí mnoho pokročilých možností:

- Binární protokol pro přenos dat na rozdíl od HTTP 1,1, který odesílá data jako nešifrovaný text.
- Podpora multiplexování pro posílání více paralelních požadavků přes stejné připojení – HTTP 1,1 omezuje zpracování na jednu zprávu požadavku nebo odpovědi.
- Obousměrná plně duplexní komunikace pro posílání požadavků klientů a odpovědí serveru současně.
- Integrované streamování umožňující požadavky a odpovědi na asynchronní streamování velkých datových sad.

gRPC je odlehčená a vysoce výkonná. Může to být až 8x rychlejší než serializace JSON se zprávami menšími 60-80%. Ve službě Microsoft [Windows Communication Foundation (WCF)](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) agilním výkon gRPC překračuje rychlost a efektivitu vysoce optimalizovaných [vazeb NetTcp](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8). Na rozdíl od NetTCP, který upřednostňuje Microsoft Stack, gRPC je mezi platformami.

## <a name="protocol-buffers"></a>Vyrovnávací paměti protokolů

gRPC zahrnuje Open Source technologie označované jako [vyrovnávací paměti protokolu](https://developers.google.com/protocol-buffers/docs/overview). Poskytují vysoce efektivní a neutrální formát serializace pro serializaci strukturovaných zpráv, které služby odesílají vzájemně. Pomocí jazyka IDL (Interface Definition Language) pro různé platformy, vývojáři definují kontrakt služby pro jednotlivé mikroslužby. Kontrakt implementovaný jako textový `.proto` soubor, popisuje metody, vstupy a výstupy pro každou službu. Stejný soubor kontraktu se dá použít pro gRPC klienty a služby postavené na různých vývojových platformách.

Pomocí souboru. kompilátor Protobuf `protoc` vygeneruje kód klienta i služby pro vaši cílovou platformu. Kód zahrnuje následující součásti:

- Silně typované objekty, které sdílí klient a služba, které reprezentují operace služby a datové prvky pro zprávu.
- Základní třída se silnými typy s požadovanou síťovou síťovou instalací, kterou služba vzdálené gRPC může zdědit a rozšiřuje.
- Klientský kód klienta, který obsahuje požadované instalace k vyvolání vzdálené služby gRPC.

Za běhu je každá zpráva serializována jako standardní reprezentace Protobuf a vyměněna mezi klientem a vzdálenou službou. Na rozdíl od JSON nebo XML jsou zprávy Protobuf serializovány jako zkompilované binární bajty.

Kniha [gRPC pro vývojáře WCF](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/), která je dostupná na webu architektury Microsoftu, poskytuje podrobné pokrytí mezipamětí GRPC a protokolů.

## <a name="grpc-support-in-net"></a>Podpora gRPC v .NET

gRPC je integrovaný do sady .NET Core 3,0 SDK a novější. Následující nástroje ji podporují:

- Visual Studio 2019, verze 16,3 nebo novější, s nainstalovanou úlohou vývoj webu.
- Visual Studio Code
- rozhraní příkazového řádku dotnet

Sada SDK obsahuje nástroje pro směrování koncových bodů, integrované IoC a protokolování. Open source webový server Kestrel podporuje připojení HTTP/2. Obrázek 4-20 ukazuje šablonu sady Visual Studio 2019, která vygeneruje kostru projektu pro službu gRPC. Všimněte si, jak .NET Core plně podporuje Windows, Linux a macOS.

![Podpora gRPC v aplikaci Visual Studio 2019](./media/visual-studio-2019-grpc-template.png)

**Obrázek 4-20**. Podpora gRPC v aplikaci Visual Studio 2019
  
Obrázek 4-21 ukazuje kostru služby gRPC vygenerovanou z integrovaného generování uživatelského rozhraní, které je součástí sady Visual Studio 2019.  

![projekt gRPC v aplikaci Visual Studio 2019](./media/grpc-project.png  )

**Obrázek 4-21**. projekt gRPC v aplikaci Visual Studio 2019

Na předchozím obrázku si poznamenejte soubor s popisem a kód služby. Jak vidíte v krátké době, Visual Studio vygeneruje další konfiguraci jak ve třídě po spuštění, tak i v podkladovém souboru projektu.

## <a name="grpc-usage"></a>využití gRPC

Upřednostnit gRPC pro následující scénáře:

- Synchronní back-end přenosná služba proti mikroslužbám, kde je pro pokračování v zpracování nutná okamžitá odpověď.
- Polyglot prostředí, která vyžadují podporu smíšených programovacích platforem.
- Nízká latence a komunikace s vysokou propustností, kde je výkon kritický.
- Komunikace Point-to-Point – gRPC může nabízet zprávy v reálném čase bez cyklického dotazování a má vynikající podporu pro obousměrné streamování.
- Omezená prostředí sítě – binární zprávy gRPC jsou vždycky menší než ekvivalentní textová zpráva JSON.

V době psaní tohoto zápisu se gRPC primárně používá pro back-end služby. Většina moderních prohlížečů nemůže poskytnout úroveň ovládacího prvku HTTP/2, která je nutná k podpoře klienta front-endu gRPC. V takovém případě je k dispozici [první iniciativa](https://devblogs.microsoft.com/aspnet/grpc-web-experiment/) , která umožňuje gRPC komunikaci z aplikací založených na prohlížeči vytvořených pomocí technologie JavaScript nebo Blazor WebAssembly. [GRPC-web pro .NET](https://github.com/grpc/grpc/blob/master/doc/PROTOCOL-WEB.md) umožňuje aplikaci ASP.NET Core gRPC podporovat funkce gRPC v prohlížečových aplikacích:

- Klienti se silným typem kódu
- Kompaktní zprávy Protobuf
- Streamování serveru

## <a name="grpc-implementation"></a>implementace gRPC

Referenční architektura mikroslužeb, [eshop na kontejnerech](https://github.com/dotnet-architecture/eShopOnContainers), od Microsoftu, ukazuje, jak implementovat služby gRPC v aplikacích .NET Core. Obrázek 4-22 prezentuje architekturu back-endu.

![Architektura back-endu pro eShop na kontejnerech](./media/eshop-with-aggregators.png)

**Obrázek 4-22**. Architektura back-endu pro eShop na kontejnerech

Na předchozím obrázku si všimněte, jak eShop zahrnuje [back-end pro model front-endu](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) (BFF) vystavení více bran rozhraní API. Probrali jsme vzor BFF dříve v této kapitole. Věnujte pozornost špičkové mikroslužbě Agregátoru (v šedé), která je umístěná mezi webovými a koncovými mikroslužbami rozhraní API pro web a back-end. Agregátor obdrží jeden požadavek od klienta, odešle ho do různých mikroslužeb, agreguje výsledky a pošle je zpět žádajícímu klientovi. Tyto operace obvykle vyžadují synchronní komunikaci, aby se vytvořila Okamžitá odezva. V eShop volání back-endu z Agregátoru se provádí pomocí gRPC, jak je znázorněno na obrázku 4-23.

![gRPC v eShop na kontejnerech](./media/grpc-implementation.png)

**Obrázek 4-23**. gRPC v eShop na kontejnerech

gRPC komunikace vyžaduje součásti klienta i serveru. Na předchozím obrázku si všimněte, jak nákupní agregátor implementuje klienta gRPC. Klient provádí synchronní volání gRPC (červeně) na mikroslužby back-end, z nichž každá implementuje Server gRPC. Klient i server využívají integrované gRPC domovní instalace z .NET Core SDK. Zástupné *procedury* na straně klienta poskytují k vyvolání vzdálených volání gRPC k dispozici instalace. Komponenty na straně serveru poskytují gRPC domovníing, které vlastní třídy služeb můžou dědit a spotřebovat.

Mikroslužby, které zveřejňují RESTful API a gRPC komunikaci, vyžadují ke správě provozu několik koncových bodů. Otevřeli jste koncový bod, který naslouchá přenosu HTTP pro volání RESTful a další pro volání gRPC. Koncový bod gRPC musí být konfigurován pro protokol HTTP/2, který je požadován pro komunikaci gRPC.

I když se snažíme oddělit mikroslužby pomocí asynchronních komunikačních vzorů, některé operace vyžadují přímé volání. gRPC by měla být primární volbou pro přímou synchronní komunikaci mezi mikroslužbami. Svůj vysoce výkonný komunikační protokol založený na protokolech HTTP/2 a vyrovnávacích pamětí protokolu se dá perfektní volbou.

## <a name="looking-ahead"></a>Pohled dopředu

GRPC se bude i nadále používat pro cloudové nativní systémy. Výhody výkonu a jednoduchost vývoje jsou přesvědčivé. Klid však bude pravděpodobně přibližně delší dobu trvat. IT Excelu pro veřejně vystavená rozhraní API a z důvodů zpětné kompatibility.

>[!div class="step-by-step"]
>[Předchozí](service-to-service-communication.md) 
> [Další](service-mesh-communication-infrastructure.md)
