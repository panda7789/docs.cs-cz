---
title: Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft
description: Získejte podrobný přehled procesu vývoje a nasazení pro vývoj a nasazování kontejnerových aplikací s využitím Docker a platformy a nástrojů Microsoftu.
ms.date: 07/30/2020
ms.openlocfilehash: d8055315b25f73d7b0b355026ab6b2c4767f9d89
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915169"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a>Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft

![Titulní kniha](./media/devops-book-cover-large-we.png)

**Edice verze 3.1** – aktualizace na ASP.NET Core 3,1

Tato příručka je obecným přehledem pro vývoj a nasazování kontejnerových ASP.NET Core aplikací pomocí Docker s využitím platformy a nástrojů Microsoftu. Příručka obsahuje základní Úvod do Azure DevOps, implementaci kanálů CI/CD a také Azure Container Registry (ACR) a služby Azure Kubernetes Services AKS pro nasazení.

Podrobnosti o nízké úrovni, které souvisejí s vývojem, najdete v části [mikroslužby .NET: architektura pro kontejnerové aplikace .NET](https://docs.microsoft.com/dotnet/architecture/microservices/) a v referenčních aplikacích [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)souvisejících s odkazem.

## <a name="send-us-your-feedback"></a>Pošlete nám svůj názor.

Tento průvodce jsme napsali a pomohli vám pochopit architekturu kontejnerových aplikací a mikroslužeb v .NET. Bude vyvíjena příručka a související referenční aplikace, takže jsme Vítejte na vašem názoru. Pokud máte komentáře o tom, jak tento průvodce můžete zlepšit, pošlete nám svůj názor na <https://aka.ms/ebookfeedback> .

## <a name="credits"></a>Kredity

Autor:

> **Cesar de la Torre**, SR. PM, produktový tým .NET, Microsoft Corp.

Editor získání:

> **Janine**

Vývojový Editor:

> **Bob Russell**, Solutions Professional v Microsoftu
>
> [**Osmičkové publikování, Inc.**](http://www.octalpub.com/)

Redakční produkce:

> [Dianne Russell](http://www.octalpub.com/)
>
> **Osmičkové publikování, Inc.**

Copyeditor:

> **Bob Russell**, Solutions Professional v Microsoftu

Účastníci a kontroloři:

> **Nish Anil**, SR. Program Manager, .NET Team, Microsoft
>
> **Miguel Veloso**, inženýr pro vývoj softwaru v jednoduchých konceptech
>
> **Sumit Ghosh**, hlavní konzultant na Neudesic

## <a name="copyright"></a>Copyright

PUBLIKOVAL(A)

Microsoft Developer divize, .NET a Visual Studio Product teams

Divize společnosti Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright &copy; 2020 od společnosti Microsoft Corporation

All rights reserved. Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.

Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora. Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené. Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.

Microsoft a ochranné známky uvedené na <https://www.microsoft.com> webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

>[!div class="step-by-step"]
>[Další](introduction-to-containers-and-docker.md)
