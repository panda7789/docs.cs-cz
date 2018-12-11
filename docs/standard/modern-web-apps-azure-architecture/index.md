---
title: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure
description: Průvodce, který obsahuje pokyny k začátku do konce vytváření monolitické webových aplikací pomocí ASP.NET Core a Azure.
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: 0d59a07e01897400a53f48799383d1670a468d73
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148103"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure

![titulní obrázek](./media/cover.png)

PUBLIKOVAL(A)

Microsoft Developer Division, .NET a Visual Studio produktových týmů

Divize Microsoft Corporation.

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2018 Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy může reprodukovat nebo v libovolné formě nebo jakýmikoli prostředky bez písemného souhlasu vydavatele.

Tato kniha je k dispozici "jako-je" a vyjadřuje zobrazení autora a názory. Zobrazení, názory a informace v této knize, včetně adres URL a jiných odkazů na internetové weby, mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady jsou k dispozici pouze pro ilustraci a jsou smyšlené. Žádný skutečný vztah nebo spojení ani je určena ji vyvozovat.

Microsoft a ochranné známky uvedený na https://www.microsoft.com na webové stránce "Ochranné známky" jsou obchodní známky společností skupiny Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Velryba logo Dockeru je registrovaná ochranná známka společnosti Docker, Inc. Použít oprávnění.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autor:

> **Steve Smith (@ardalis)**, Poradce pro architekturu softwaru, [Ardalis.com](https://ardalis.com)

Editory:

> **Maira Wenzel**

## <a name="introduction"></a>Úvod

.NET core a ASP.NET Core nabízí několik výhod oproti tradičním vývoj na platformě .NET. Pokud některé nebo všechny z následujících akcí, které jsou důležité pro úspěch vaší aplikace byste měli používat .NET Core pro serverové aplikace:

- Podpora víc platforem.

- Používání mikroslužeb.

- Použití kontejnerů Dockeru.

- Vysoké požadavky na výkon a škálovatelnost.

- Správa verzí vedle sebe verzí rozhraní .NET v aplikaci na stejném serveru.

Tradiční aplikace rozhraní .NET můžete a dělat vyhovění těmto požadavkům, ale v ASP.NET Core a .NET Core byly optimalizovány a nabídnout Vylepšená podpora pro výše zmíněné situace umožnili.

Více organizací volí k hostování webových aplikací v cloudu pomocí služeb, jako je Microsoft Azure. Měli byste zvážit hostování vaší aplikace v cloudu, pokud tady jsou důležité pro vaše aplikace nebo organizace:

- Snížení investice do datového centra náklady (hardware, software, místa, nástroje atd.)

- Flexibilní ceny (placené podle používání, ne za nevyužitou kapacitu).

- Extrémní spolehlivost.

- Vylepšené aplikace mobility; snadno změnit, kde a jak je aplikace nasazená.

- Flexibilní kapacity; vertikálně navyšovat nebo snižovat podle skutečných potřeb.

Vytváření webových aplikací pomocí ASP.NET Core, hostované v Azure, nabízí mnoho konkurenční výhody oproti tradičním alternativy. ASP.NET Core je optimalizovaná pro postupy vývoje moderních webových aplikací a cloudových scénářích hostování. V této příručce se dozvíte, jak navrhovat aplikace ASP.NET Core nejlíp využít tyto možnosti.

## <a name="purpose"></a>Účel

Tato příručka obsahuje pokyny k začátku do konce vytváření monolitické webových aplikací pomocí ASP.NET Core a Azure.

Tento průvodce je pouze doplnění ["_Mikroslužby .NET. Architektura pro Kontejnerizovaných aplikací .NET_"](../microservices-architecture/index.md) který se zaměřuje další on Docker, Mikroslužby a nasazení kontejnerů pro hostování podnikových aplikací.

### <a name="net-microservices-architecture-for-containerized-net-applications"></a>Mikroslužby .NET. Architektura pro Kontejnerizované aplikace .NET

- **(elektronická kniha)**  
  <https://aka.ms/MicroservicesEbook>
- **Ukázkové aplikace**  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tohoto průvodce

Cílovou skupinu tohoto průvodce je především vývojáře, vedoucími vývoje a architektů, kteří mají zájem o vývoj moderních webových aplikací pomocí Microsoft technologie a služby v cloudu.

Sekundární skupina jsou technické pracovníky s rozhodovací pravomocí, kteří jsou již známé technologie ASP.NET nebo v Azure a hledáte informace o tom, zda má smysl pro upgrade na technologie ASP.NET Core pro nové nebo existující projekty.

## <a name="how-you-can-use-this-guide"></a>Použití tohoto průvodce

Tato příručka obsahuje byla zhušťovat do poměrně málo početnému dokumentu, který se zaměřuje na tvorbu webových aplikací s moderní technologie .NET a Windows Azure. V důsledku toho může být číst v celém rozsahu na poskytují základní principy těchto aplikací a jejich technické aspekty. V průvodci, spolu s ukázkovou aplikaci, může sloužit také jako výchozí bod nebo odkaz. Použijte související ukázkové aplikace jako šablonu pro vaše vlastní aplikace, nebo můžete zobrazit, jak můžete organizovat součásti vaší aplikace. Při odkazovat zpět v Průvodci principy a pokrytí architektury a možnosti technologií a důležité informace o rozhodnutí při vážení tyto možnosti pro svoji vlastní aplikaci.

Můžete dál v této příručce k vašemu týmu pomoct zajistit, aby tyto aspekty a příležitosti. S Vystoupením práce z společnou sadu terminologie a základní principy pomáhá zajistit konzistentní použití architektury vzory a postupy.

## <a name="references"></a>Odkazy

- **Volba mezi .NET Core a .NET Framework pro serverové aplikace**  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Next](modern-web-applications-characteristics.md)