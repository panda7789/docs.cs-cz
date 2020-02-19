---
title: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure
description: Příručka, která poskytuje kompletní pokyny k vytváření monolitické webových aplikací pomocí ASP.NET Core a Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: c19e5e90cfb96463f744cfb064abe72ee5db2e9f
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449322"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure

![Titulní obrázek knihy Průvodce moderními webovými aplikacemi architektury](./media/index/web-application-guide-cover-image.png)

**Edice verze 3.1** – aktualizace na ASP.NET Core 3,1

PUBLIKOVAL (A)

Týmy produktů Microsoft Developer divize, .NET a Visual Studio

Divize společnosti Microsoft Corporation

Jeden způsob Microsoftu

Redmond, Washington 98052-6399

Copyright © 2020 od společnosti Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.

Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora. Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.

Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené. Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.

Microsoft a ochranné známky uvedené na adrese https://www.microsoft.com na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autor:

> **Steve "ardalis" Smith** -Software Architect a Trainer- [Ardalis.com](https://ardalis.com)

Editory

> **Maira Wenzel**

## <a name="introduction"></a>Úvod

.NET Core a ASP.NET Core nabízí několik výhod oproti tradičnímu vývoji pro .NET. Pro své serverové aplikace byste měli použít .NET Core, pokud jsou některé nebo všechny následující důležité pro úspěch vaší aplikace:

- Podpora pro různé platformy.

- Použití mikroslužeb.

- Použití kontejnerů Docker.

- Vysoký výkon a požadavky na škálovatelnost.

- Souběžná Správa verzí rozhraní .NET podle aplikace na stejném serveru.

Tradiční aplikace .NET můžou a podporují mnoho těchto požadavků, ale ASP.NET Core a .NET Core jsou optimalizované tak, aby nabízely vylepšenou podporu pro výše uvedené scénáře.

Další a více organizací se volí pro hostování webových aplikací v cloudu pomocí služeb, jako je Microsoft Azure. Měli byste zvážit hostování aplikace v cloudu, pokud jsou pro vaši aplikaci nebo organizaci důležité následující:

- Snížená investice do nákladů datového centra (hardware, software, prostor, nástroje, Správa serveru atd.)

- Flexibilní ceny (placené na základě využití, ne pro nečinné kapacity).

- Extrémní spolehlivost.

- Vylepšená mobilita aplikací; Snadná změna místa a způsobu nasazení aplikace

- Flexibilní kapacita; horizontální navýšení nebo snížení kapacity podle skutečných potřeb

Vytváření webových aplikací pomocí ASP.NET Core hostovaných v Azure nabízí řadu konkurenčních výhod oproti tradičním alternativám. ASP.NET Core je optimalizovaná pro moderní postupy pro vývoj webových aplikací a hostování cloudu. V této příručce se dozvíte, jak navrhovat aplikace ASP.NET Core, abyste mohli nejlépe využít tyto možnosti.

## <a name="purpose"></a>Účel

Tato příručka poskytuje kompletní pokyny k vytváření *monolitické* webových aplikací pomocí ASP.NET Core a Azure. V tomto kontextu odkazuje "monolitické" na skutečnost, že tyto aplikace jsou nasazeny jako jediná jednotka, nikoli jako kolekce interaktivních služeb a aplikací.

Tato příručka je doplňkem k ["_mikroslužbám .NET". Architektura pro kontejnerové aplikace .NET_](../microservices/index.md) , která se zaměřuje na Další informace o Docker, mikroslužbách a nasazení kontejnerů pro hostování podnikových aplikací.

### <a name="net-microservices-architecture-for-containerized-net-applications"></a>Mikroslužby .NET. Architektura pro kontejnerizované aplikace .NET

- **Elektronická kniha**  
  <https://aka.ms/MicroservicesEbook>
- **Ukázková aplikace**  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

Cílová skupina pro tento průvodce je hlavně vývojářům, vedoucím vývoje a architektům, kteří mají zájem o vytváření moderních webových aplikací s využitím technologií a služeb Microsoftu v cloudu.

Sekundární cílová skupina je technickým autorem rozhodnutí, kteří už znají ASP.NET nebo Azure a hledají informace o tom, jestli má smysl upgradovat na ASP.NET Core pro nové nebo existující projekty.

## <a name="how-you-can-use-this-guide"></a>Jak můžete použít tuto příručku

Tato příručka je zhuštěná do relativně malého dokumentu, který se zaměřuje na sestavování webových aplikací s využitím moderních technologií .NET a Windows Azure. V takovém případě je lze přečíst v celém rozsahu a poskytnout základ pro porozumění takovým aplikacím a jejich technickým hlediskům. Průvodce společně s jeho ukázkovou aplikací může sloužit také jako výchozí bod nebo odkaz. Použijte přidruženou ukázkovou aplikaci jako šablonu pro vlastní aplikace nebo k zobrazení, jak můžete uspořádat součásti komponenty aplikace. Přečtěte si téma zásady a pokrytí možností architektury a technologie a rozhodnutí o rozhodování, pokud chcete zvážit, jaké možnosti máte k dispozici pro vlastní aplikaci.

Nebojte se této příručky s vaším týmem, abyste se ujistili, že se tyto otázky a příležitosti budou porozumět běžným způsobem. Díky tomu, že všichni pracují se společnou sadou terminologie a základními principy, pomáhají zajistit konzistentní používání vzorů a postupů architektury.

## <a name="references"></a>Odkazy

- **Volba mezi .NET Core a .NET Framework pro serverové aplikace**  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[Next](modern-web-applications-characteristics.md)
