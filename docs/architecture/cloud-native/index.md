---
title: Navrhování cloudových nativních aplikací .NET pro Azure
description: Průvodce pro vytváření cloudnativních aplikací využívajících kontejnery, mikroslužby a funkce Bez serveru Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 7f14a690d0153edc43f0ce7f4e91c9e9cd2c6858
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71696778"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Navrhování cloudových nativních aplikací .NET pro Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![obrázek obálky](./media/cover.png)

PUBLIKOVAL(A)

Produktové týmy Microsoft Developer Division, .NET a Visual Studio

Divize společnosti Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Autorská práva © 2019 společností Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy nesmí být reprodukována nebo přenášena v jakékoli formě nebo jakýmkoli způsobem bez písemného souhlasu vydavatele.

Tato kniha je poskytována "tak, jak je" a vyjadřuje názory a názory autora. Názory, názory a informace vyjádřené v této knize, včetně url a dalších odkazů na internetové stránky, se mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené. Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.

Společnost Microsoft a ochranné https://www.microsoft.com známky uvedené na webové stránce "Ochranné známky" jsou ochrannými známkami skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Logo velryby Docker je registrovaná ochranná známka společnosti Docker, Inc. Používá se svolením.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autoři:

> **Steve "ardalis" Smith** - softwarový architekt a trenér - [Ardalis.com](https://ardalis.com)
>
> **Rob Vettor** - Microsoft - Hlavní architekt cloudového systému / ARCHITEKT IP - [RobVettor.com](https://robvettor.com)

Účastníci a recenzenti:

> **Cesar De la Torre**, hlavní programový manažer, .NET tým, Microsoft
>
> **Nish Anil**, Sr. Program Manager, .NET tým, Microsoft

Editory:

> **Maira Wenzel**, Sr. Content Developer, .NET tým, Microsoft

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

Okruhy uživatelů tohoto průvodce jsou především vývojáři, vedoucí vývoje a architekti, kteří se zajímají o to, jak vytvářet aplikace navržené pro cloud.

Sekundární publikum je technická rozhodnutí, kteří plánují zvolit, zda mají vytvářet své aplikace pomocí přístupu nativního pro cloud.

## <a name="how-you-can-use-this-guide"></a>Jak můžete tuto příručku používat

Tato příručka začíná definováním cloudnativní a zavedení referenční aplikace vytvořené pomocí zásad a technologií nativní pro cloud. Kromě těchto prvních dvou kapitol je zbytek knihy rozdělen na konkrétní kapitoly zaměřené na témata společná pro většinu aplikací nativních pro cloud. Můžete přejít na některou z těchto kapitol a dozvědět se o přístupech nativních pro cloud:

- Přístup k datům a datům
- Vzory komunikace
- Škálování a škálovatelnost
- Odolnost aplikace
- Monitorování a stav
- Identita a bezpečnost
- DevOps

Tato příručka je k dispozici jak ve formátu PDF, tak online. Neváhejte a předat tento dokument nebo odkazy na jeho online verzi svému týmu, abyste zajistili společné porozumění těmto tématům. Většina těchto témat těží z důsledného porozumění základním zásadám a vzorcům, jakož i kompromisům spojeným s rozhodnutími týkajícími se těchto témat. Naším cílem s tímto dokumentem je vybavit týmy a jejich vedoucí informace, které potřebují k tomu, aby se mohli informovaně rozhodovat o architektuře, vývoji a hostování svých aplikací.

>[!div class="step-by-step"]
>[Další](introduction.md)
