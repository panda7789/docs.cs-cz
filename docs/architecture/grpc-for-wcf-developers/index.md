---
title: ASP.NET Core gRPC pro vývojáře WCF – gRPC pro vývojáře WCF
description: Úvod k vytváření gRPC Services v ASP.NET Core 3,0 pro vývojáře WCF
ms.date: 09/02/2019
ms.openlocfilehash: 3ef513d2397b6f282591dfe6c9b25cd178372a28
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967751"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>gRPC ASP.NET Core pro vývojáře WCF

![titulní obrázek](./media/cover.png)

PUBLIKOVAL (A)

Týmy produktů Microsoft Developer divize, .NET a Visual Studio

Divize společnosti Microsoft Corporation

Jeden způsob Microsoftu

Redmond, Washington 98052-6399

Copyright © 2019 od společnosti Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.

Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora. Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.

Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené. Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.

Microsoft a ochranné známky uvedené na adrese https://www.microsoft.com na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.

Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autorizova

> **Označení Rendle** -ředitel technického důstojníka – [Visual Recode](https://visualrecode.com)
>
> **Miranda Steiner** – technický autor

Editory

> **Maira Wenzel** – vývojář obsahu SR – Microsoft

## <a name="introduction"></a>Úvod

gRPC je moderní architektura pro vytváření síťových služeb a distribuovaných aplikací. Představte si výkon vazeb NetTCP WCF s interoperabilitou pro různé platformy protokolu SOAP. gRPC vytváří na HTTP/2 a protokol pro kódování zpráv Protobuf pro zajištění vysokého výkonu a komunikace s malou šířkou pásma mezi aplikacemi a službami. Podporuje generování kódu serveru a klienta napříč nejoblíbenějšími programovacími jazyky a platformami, včetně .NET, Java, Pythonu, Node. js, C++ a dalších. Díky špičkové podpoře pro gRPC v ASP.NET Core 3,0 společně s existujícími nástroji gRPC a knihovnami pro .NET 4. x si myslíme, že se jedná o skvělou alternativu ke službě WCF pro vývojové týmy, které chtějí přijmout .NET Core ve svých organizacích.

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

Tato příručka je určená pro vývojáře, kteří pracují v .NET Framework nebo .NET Core, kteří dříve používali WCF a kteří chtějí migrovat své aplikace do moderního prostředí RPC pro .NET Core 3,0 a novější verze. Průvodce může být také obecně používán pro vývojáře, kteří upgradují nebo berou v úvahách o upgradu na rozhraní .NET Core 3,0, kteří chtějí používat integrované nástroje gRPC.

## <a name="how-you-can-use-this-guide"></a>Jak můžete použít tuto příručku

Toto je krátký úvod k sestavování služeb gRPC v ASP.NET Core 3,0 s konkrétní referencí na WCF jako podobnou platformou. Vysvětluje principy gRPC, vztahující se k jednotlivým konceptům ekvivalentních funkcí WCF a poskytuje pokyny pro migraci existující aplikace WCF na gRPC. Je to také užitečné pro vývojáře, kteří mají zkušenosti s WCF a chtějí se naučit gRPC vytvářet nové služby. Ukázkové aplikace lze použít jako šablonu nebo odkaz pro vlastní projekty a vy můžete kopírovat a znovu použít kód z knihy nebo jejích ukázek.

Nebojte se této příručky s vaším týmem, abyste se ujistili, že se tyto otázky a příležitosti budou porozumět běžným způsobem. Díky tomu, že všichni pracují se společnou sadou terminologie a základními principy, pomáhají zajistit konzistentní používání vzorů a postupů architektury.

## <a name="references"></a>Odkazy

- **Web gRPC**  
  <https://grpc.io>
- **Volba mezi .NET Core a .NET Framework pro serverové aplikace**  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Next](introduction.md)
