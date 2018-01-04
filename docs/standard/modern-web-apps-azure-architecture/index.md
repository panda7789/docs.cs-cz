---
title: "Architekti moderních webových aplikací pomocí ASP.NET Core a Azure"
description: "Architektury moderních webových aplikací pomocí ASP.NET Core a Azure | Úvod"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 44864274a86634c0199885b5507124f2f54ce0f6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Architekti moderních webových aplikací pomocí ASP.NET Core a Azure

.NET core a ASP.NET Core nabízí několik výhod oproti tradičním .NET – vývoj. .NET Core byste měli použít pro serverové aplikace, pokud některé nebo všechny z následujících akcí, které jsou důležité pro úspěch vaší aplikace:

-   Podpora více platforem

-   Použití mikroslužeb

-   Použití kontejnerů Docker

-   Vysoký výkon a škálovatelnost požadavky

-   Souběžně sdílená verze rozhraní .NET verze aplikace na stejném serveru

Tradiční aplikace .NET může a proveďte podporu těchto požadavků, ale jsou optimalizované ASP.NET Core a .NET Core nabízí vylepšenou podporu pro výše uvedené scénáře.

Organizace více výběru pro hostování své webové aplikace v cloudu pomocí služby, jako je Microsoft Azure. Měli byste zvážit hostování vaší aplikace v cloudu, pokud tady jsou důležité pro vaše aplikace nebo organizace:

-   Snížené investice do datového centra náklady (hardwaru, softwaru, místo, nástroje atd.)

-   Flexibilní ceny (platím na základě využití, ne pro nečinnosti kapacity)

-   Extrémně spolehlivosti

-   Vylepšené aplikace mobility; snadno změnit kde a jak vaše aplikace je nasazená

-   Flexibilní kapacity; škálování směrem nahoru nebo dolů na základě skutečné požadavky

Vytváření webových aplikací pomocí ASP.NET Core, hostované ve službě Microsoft Azure nabízí řadu výhod konkurenční přes tradiční alternativy. ASP.NET Core je optimalizovaná pro postupy vývoj moderních webových aplikací a na cloudový hosting scénáře. V tomto průvodci se dozvíte, jak do architektury aplikace ASP.NET Core nejlépe využít těchto funkcí.

## <a name="purpose"></a>Účel

Tato příručka obsahuje pokyny začátku do konce k vytváření monolitický webových aplikací pomocí ASP.NET Core a Azure.

Tato příručka je doplňkem k "*Architecting a vývoj Kontejnerizované a na základě Mikroslužbu aplikace pomocí rozhraní .NET*" která se zaměřuje další na Docker, Mikroslužeb a nasazení kontejnerů do firemní sítě hostitele aplikace.

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a>Architektury a vývoj Kontejnerizované Mikroslužbu na základě aplikací v rozhraní .NET
> - **elektronická kniha**  
> <http://aka.MS/MicroservicesEbook>
> - **Ukázkové aplikace**  
> <http://aka.MS/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Tato příručka, kdo by měl používat

Cílovou skupinu tohoto průvodce je především vývojáře, zájemců vývoj a architektům, kteří mají zájem o vytváření moderních webových aplikací pomocí Microsoft technologií a služeb v cloudu.

Sekundární cílové skupiny je technické vedoucím pracovníkům, kteří jsou již obeznámeni ASP.NET nebo Azure a hledáte informace o tom, jestli má smysl pro upgrade na ASP.NET Core pro nové nebo existující projekty.

## <a name="how-you-can-use-this-guide"></a>Použití této příručce

Tato příručka obsahuje byla vyjádřit těmito poměrně malý dokument, který se zaměřuje na tvorbu webových aplikací s moderním technologie .NET a systému Windows Azure. Jako takový ho můžete přečíst v celé jeho šíři poskytnout základní principy tyto aplikace a jejich technické aspekty. V průvodci, společně s ukázkovou aplikaci, může taky sloužit jako výchozí bod nebo odkaz. Pomocí aplikace přidružené sample jako šablona pro vaše vlastní aplikace nebo zjistit, jak můžete organizovat součásti vaší aplikace. Při odkazovat zpět v Průvodci principy a pokrytí architektura a možnosti technologií a rozhodnutí vážení tyto možnosti pro vlastní aplikaci.

Nebojte se, že předávání této příručce si s týmem k zajištění výklad tyto požadavky a možnosti. Má každý uživatel práce z společnou sadu terminologie a základních zásad vám pomůže zajistit konzistentní použití architektury vzory a postupy.

## <a name="references"></a>Odkazy
- **Volba mezi .NET Core a .NET Framework pro serverové aplikace**  
<https://docs.microsoft.com/DotNet/articles/Standard/Choosing-Core-Framework-server>

>[!div class="step-by-step"]
[Další] (moderních web aplikace characteristics.md)
