---
title: ASP.NET Core gRPC pro vývojáře WCF - gRPC pro vývojáře WCF
description: Úvod do budování služeb gRPC v ASP.NET Core 3.0 pro vývojáře WCF
ms.date: 09/02/2019
ms.openlocfilehash: 40307124c521659a00339884bacf48881fa3e048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543232"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>gRPC ASP.NET Core pro vývojáře WCF

![obrázek obálky](./media/cover.png)

PUBLIKOVAL(A)

Produktové týmy Microsoft Developer Division, .NET a Visual Studio

Divize společnosti Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Autorská práva © 2019 společností Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy nesmí být reprodukována nebo přenášena v jakékoli formě nebo jakýmkoli způsobem bez písemného souhlasu vydavatele.

Tato kniha je poskytována "tak, jak je" a vyjadřuje názory a názory autora. Názory, názory a informace vyjádřené v této knize, včetně URL a dalších odkazů na internetové stránky, se mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené. Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.

Společnost Microsoft a ochranné https://www.microsoft.com známky uvedené na webové stránce "Ochranné známky" jsou ochrannými známkami skupiny společností Microsoft.

Logo velryby Docker je registrovaná ochranná známka společnosti Docker, Inc. Používá se svolením.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autoři:

> **Mark Rendle** - Technický ředitel - [Visual Recode](https://visualrecode.com)
>
> **Miranda Steiner** - Technický autor

Editor:

> **Maira Wenzel** - Sr. Content Developer - Microsoft

## <a name="introduction"></a>Úvod

gRPC je moderní rámec pro budování síťových služeb a distribuovaných aplikací. Představte si výkon vazby NetTCP platformy Windows Communication Foundation (WCF) v kombinaci s interoperabilitou soap napříč platformami. gRPC staví na PROTOKOLU HTTP/2 a protokolu kódování zpráv Protobuf, který poskytuje vysoce výkonnou komunikaci s malou šířkou pásma mezi aplikacemi a službami. Podporuje generování systému serveru a klientského kódu napříč nejoblíbenějšími programovacími jazyky a platformami, včetně .NET, Java, Python, Node.js, Go a C++. S prvotřídní podporou gRPC v ASP.NET Core 3.0, spolu se stávajícími gRPC nástroji a knihovnami pro .NET 4.x, je to vynikající alternativa k WCF pro vývojové týmy, které chtějí přijmout .NET Core ve svých organizacích.

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

Tato příručka byla napsána pro vývojáře pracující v rozhraní .NET Framework nebo .NET Core, kteří dříve používali WCF a kteří se snaží migrovat své aplikace do moderního prostředí RPC pro .NET Core 3.0 a novější verze. Obecněji platí, že pokud upgradujete nebo zvažujete upgrade na .NET Core 3.0 a chcete použít vestavěné nástroje gRPC, je tato příručka také užitečná.

## <a name="how-you-can-use-this-guide"></a>Jak můžete tuto příručku používat

Toto je krátký úvod do budování gRPC Services v ASP.NET Core 3.0, se zvláštním odkazem na WCF jako analogická platforma. Vysvětluje principy gRPC, vztahující se ke každému konceptu ekvivalentních funkcí WCF, a nabízí pokyny pro migraci existující aplikace WCF do gRPC. Je to také užitečné pro vývojáře, kteří mají zkušenosti s WCF a chtějí se naučit gRPC vytvářet nové služby. Ukázkové aplikace můžete použít jako šablonu nebo odkaz pro vlastní projekty a můžete zkopírovat a znovu použít kód z knihy nebo jejích ukázek.

Neváhejte a předat tuto příručku svému týmu, abyste zajistili společné porozumění těmto úvahám a příležitostem. Mít všechny, kteří pracují ze společného souboru pojmů a základních principů, pomáhá zajistit konzistentní uplatňování architektonických vzorů a postupů.

## <a name="references"></a>Odkazy

- **webové stránky gRPC**
  <https://grpc.io>
- **Výběr mezi rozhraním .NET Core a rozhraním .NET Framework pro serverové aplikace**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Další](introduction.md)
