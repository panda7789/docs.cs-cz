---
title: Architekt cloudových nativních aplikací .NET pro Azure
description: Příručka pro sestavování nativních aplikací cloudu využívajících kontejnery, mikroslužby a funkce bez serveru v Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 67e235b051702308d2455b2501bfb59a4317635b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214163"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Architekt cloudových nativních aplikací .NET pro Azure

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

Microsoft a ochranné známky uvedené https://www.microsoft.com na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc. Používá se oprávněním.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autoři

> **Steve "ardalis" Smith** -Software Architect a Trainer- [Ardalis.com](https://ardalis.com)
>
> **Rob Vettor** – Microsoft-Principal Cloud System architekt/IP architekt – [RobVettor.com](https://robvettor.com)

Účastníci a kontroloři:

> **Cesar de la Torre**, Principal program Manager, .NET Team, Microsoft
>
> **Nish Anil**, SR. Program Manager, .NET Team, Microsoft

Editory

> **Maira Wenzel**, SR. Content Developer, .NET Team, Microsoft

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

Cílová skupina pro tento průvodce je hlavně vývojářům, vedoucím vývoje a architektům, kteří mají zájem o vytváření aplikací určených pro Cloud.

Sekundární cílová skupina je technickým rozhodnutím, které plánuje vybrat, jestli se mají vytvářet aplikace s využitím nativního přístupu v cloudu.

## <a name="how-you-can-use-this-guide"></a>Jak můžete použít tuto příručku

Tato příručka začíná definováním cloudového nativního nasazení a představením referenční aplikace vytvořené pomocí cloudových nativních principů a technologií. Kromě těchto prvních dvou kapitol se zbytek knihy rozdělí na konkrétní kapitoly zaměřené na témata, která jsou společná pro většinu cloudových nativních aplikací. Pokud se chcete dozvědět víc o přístupech nativních ke cloudu, můžete přejít na libovolnou z těchto kapitol:

- Data a přístup k datům
- Způsoby komunikace
- Škálování a škálovatelnost
- Odolnost aplikace
- Monitorování a stav
- Identita a zabezpečení
- DevOps

Tato příručka je k dispozici ve formátu PDF i v online režimu. Nebojte se, že tento dokument předáte nebo odkazuje na jeho online verzi týmu, aby se zajistilo běžné porozumění těmto tématům. Většina těchto témat přináší konzistentní porozumění základním principům a vzorům a kompromisům, které se týkají rozhodnutí souvisejících s těmito tématy. Naším cílem tohoto dokumentu je vybavit týmy a jejich vedoucími informacemi, které potřebují k rozhodování o jejich architektuře, vývoji a hostování svých aplikací.

>[!div class="step-by-step"]
>[Next](introduction.md)
