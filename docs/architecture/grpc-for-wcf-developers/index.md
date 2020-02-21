---
title: ASP.NET Core gRPC pro vývojáře WCF – gRPC pro vývojáře WCF
description: Úvod k vytváření gRPC Services v ASP.NET Core 3,0 pro vývojáře WCF
ms.date: 09/02/2019
ms.openlocfilehash: 40307124c521659a00339884bacf48881fa3e048
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543232"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>gRPC ASP.NET Core pro vývojáře WCF

![titulní obrázek](./media/cover.png)

PUBLIKOVAL (A)

Týmy produktů Microsoft Developer divize, .NET a Visual Studio

Divize společnosti Microsoft Corporation

Jeden způsob Microsoftu

Redmond, Washington 98052-6399

Copyright © 2019 by Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.

Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora. Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.

Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené. Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.

Microsoft a ochranné známky uvedené na adrese https://www.microsoft.com na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.

Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autoři:

> **Označení Rendle** -ředitel technického důstojníka – [Visual Recode](https://visualrecode.com)
>
> **Miranda Steiner** – technický autor

Redaktor:

> **Maira Wenzel** – SR. Content – vývojář – Microsoft

## <a name="introduction"></a>Úvod

gRPC je moderní architektura pro vytváření síťových služeb a distribuovaných aplikací. Představte si Windows Communication Foundation výkon NetTCPch vazeb WCF (WCF) v kombinaci s interoperabilitou pro různé platformy protokolu SOAP. gRPC vytváří na HTTP/2 a protokol pro kódování zpráv Protobuf pro zajištění vysokého výkonu a komunikace s malou šířkou pásma mezi aplikacemi a službami. Podporuje generování kódu serveru a klienta napříč nejoblíbenějšími programovacími jazyky a platformami, jako jsou .NET, Java, Python, Node. js, přejít C++a. Díky špičkové podpoře pro gRPC v ASP.NET Core 3,0 společně s existujícími nástroji gRPC a knihovnami pro .NET 4. x je to vynikající alternativou WCF pro vývojové týmy, které chtějí přijmout .NET Core ve svých organizacích.

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

Tato příručka je určená pro vývojáře, kteří pracují v .NET Framework nebo .NET Core, kteří dříve používali WCF a kteří chtějí migrovat své aplikace do moderního prostředí RPC pro .NET Core 3,0 a novější verze. Obecně platí, že pokud upgradujete nebo zvažujete upgrade, na .NET Core 3,0 a chcete použít integrované nástroje gRPC, je tato příručka také užitečná.

## <a name="how-you-can-use-this-guide"></a>Jak můžete použít tuto příručku

Toto je krátký úvod k sestavování služeb gRPC v ASP.NET Core 3,0, se specifickou referencí na WCF jako s obdobnou platformou. Vysvětluje principy gRPC, vztahující se k jednotlivým konceptům ekvivalentních funkcí WCF a poskytuje pokyny pro migraci existující aplikace WCF na gRPC. Je to také užitečné pro vývojáře, kteří mají zkušenosti s WCF a chtějí se naučit gRPC vytvářet nové služby. Ukázkové aplikace můžete použít jako šablonu nebo odkaz pro vlastní projekty a vy můžete zkopírovat a znovu použít kód z knihy nebo jejích ukázek.

Nebojte se této příručky s vaším týmem, abyste se ujistili, že se tyto otázky a příležitosti budou porozumět běžným způsobem. Díky tomu, že všichni pracují se společnou sadou podmínek a základními principy, pomáhají zajistit konzistentní používání vzorů a postupů architektury.

## <a name="references"></a>Odkazy

- **Web gRPC**
  <https://grpc.io>
- **Výběr mezi .NET Core a .NET Framework pro serverové aplikace**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Next](introduction.md)
