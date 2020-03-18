---
title: Architektur moderních webových aplikací s ASP.NET Core a Azure
description: Průvodce, který poskytuje komplexní pokyny pro vytváření monolitických webových aplikací pomocí ASP.NET Core a Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: c19e5e90cfb96463f744cfb064abe72ee5db2e9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77449322"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure

![Obrázek obálky knihy průvodce Moderní webové aplikace Architekt.](./media/index/web-application-guide-cover-image.png)

**EDITION v3.1** - Aktualizováno na ASP.NET Jádro 3.1

PUBLIKOVAL(A)

Produktové týmy Microsoft Developer Division, .NET a Visual Studio

Divize společnosti Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Autorská práva © 2020 společností Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy nesmí být reprodukována nebo přenášena v jakékoli formě nebo jakýmkoli způsobem bez písemného souhlasu vydavatele.

Tato kniha je poskytována "tak, jak je" a vyjadřuje názory a názory autora. Názory, názory a informace vyjádřené v této knize, včetně URL a dalších odkazů na internetové stránky, se mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené. Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.

Společnost Microsoft a ochranné https://www.microsoft.com známky uvedené na webové stránce "Ochranné známky" jsou ochrannými známkami skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Logo velryby Docker je registrovaná ochranná známka společnosti Docker, Inc. Používá se svolením.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autor:

> **Steve "ardalis" Smith** - softwarový architekt a trenér - [Ardalis.com](https://ardalis.com)

Editory:

> **Maira Wenzel**

## <a name="introduction"></a>Úvod

.NET Core a ASP.NET Core nabízejí několik výhod oproti tradičnímu vývoji .NET. Jádro .NET pro serverové aplikace byste měli použít, pokud jsou pro úspěch vaší aplikace důležité některé nebo všechny následující:

- Podpora napříč platformami.

- Použití mikroslužeb.

- Použití kontejnerů Dockeru.

- Vysoké požadavky na výkon a škálovatelnost.

- Souběžná správa verzí verzí rozhraní .NET aplikací na stejném serveru.

Tradiční aplikace .NET mohou a podporují mnoho z těchto požadavků, ale ASP.NET Core a .NET Core byly optimalizovány tak, aby nabízely vylepšenou podporu pro výše uvedené scénáře.

Stále více organizací se rozhodlo hostovat své webové aplikace v cloudu pomocí služeb, jako je Microsoft Azure. Měli byste zvážit hostování aplikace v cloudu, pokud jsou pro vaši aplikaci nebo organizaci důležité následující:

- Snížení investic do nákladů datových center (hardware, software, prostor, nástroje, správa serverů atd.)

- Flexibilní ceny (platí na základě využití, ne pro nevyužitou kapacitu).

- Extrémní spolehlivost.

- Vylepšená mobilita aplikací; snadno změnit, kde a jak je vaše aplikace nasazena.

- Flexibilní kapacita; stupnice nahoru nebo dolů na základě skutečných potřeb.

Vytváření webových aplikací s ASP.NET Core, hostované v Azure, nabízí mnoho konkurenčních výhod oproti tradičním alternativám. ASP.NET Core je optimalizovaný pro moderní postupy vývoje webových aplikací a scénáře cloudového hostování. V této příručce se dozvíte, jak navrhovat ASP.NET základní aplikace, abyste tyto možnosti co nejlépe využili.

## <a name="purpose"></a>Účel

Tato příručka poskytuje komplexní pokyny pro vytváření *monolitických* webových aplikací pomocí ASP.NET Core a Azure. V tomto kontextu "monolitické" odkazuje na skutečnost, že tyto aplikace jsou nasazeny jako jeden celek, nikoli jako kolekce vzájemně propojených služeb a aplikací.

Tato příručka je doplňkem ["_.NET Microservices. Architektura pro kontejnerizované aplikace .NET_,](../microservices/index.md) která se více zaměřuje na Docker, Mikroslužby a nasazení kontejnerů pro hostování podnikových aplikací.

### <a name="net-microservices-architecture-for-containerized-net-applications"></a>Mikroslužby .NET. Architektura pro kontejnerizované aplikace .NET

- **e-kniha**  
  <https://aka.ms/MicroservicesEbook>
- **Ukázková aplikace**  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

Cílovou skupinou pro tuto příručku jsou především vývojáři, vedoucí vývoje a architekti, kteří se zajímají o vytváření moderních webových aplikací pomocí technologií a služeb společnosti Microsoft v cloudu.

Sekundární okruh uživatelů je technická rozhodovací skupina, která už zná ASP.NET nebo Azure a hledají informace o tom, jestli má smysl upgradovat na ASP.NET Core pro nové nebo stávající projekty.

## <a name="how-you-can-use-this-guide"></a>Jak můžete tuto příručku používat

Tato příručka byla zhuštěna do relativně malého dokumentu, který se zaměřuje na vytváření webových aplikací s moderními technologiemi .NET a Windows Azure. Jako takový, to může být chápána v plném rozsahu poskytnout základ pro pochopení těchto aplikací a jejich technické aspekty. Průvodce, spolu s jeho ukázkovou aplikací, může také sloužit jako výchozí bod nebo odkaz. Použijte přidruženou ukázkovou aplikaci jako šablonu pro vlastní aplikace nebo se podívejte, jak můžete uspořádat součásti aplikace. Při zvažování těchto možností pro vlastní aplikaci se vraťte k principům průvodce a pokrytí možností architektury a technologií a k úvahám o rozhodování.

Neváhejte a předat tuto příručku svému týmu, abyste zajistili společné porozumění těmto úvahám a příležitostem. To, že všichni pracují ze společného souboru terminologie a základních principů, pomáhá zajistit konzistentní uplatňování architektonických vzorů a postupů.

## <a name="references"></a>Odkazy

- **Volba mezi .NET Core a .NET Framework pro serverové aplikace**  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[Další](modern-web-applications-characteristics.md)
