---
title: Architekt cloudových nativních aplikací .NET pro Azure
description: Příručka pro sestavování nativních aplikací cloudu využívajících kontejnery, mikroslužby a funkce bez serveru v Azure.
author: ardalis
ms.date: 05/13/2020
ms.openlocfilehash: 1607c1bbcc9bbb3c9fe19840a2827aa5ea083728
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613993"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Architekt cloudových nativních aplikací .NET pro Azure

![titulní obrázek](./media/cover.png)

**EDICE v. 1.0**

PUBLIKOVAL(A)

Týmy produktů Microsoft Developer divize, .NET a Visual Studio

Divize společnosti Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright &copy; 2020 od společnosti Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.

Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora. Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené. Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.

Microsoft a ochranné známky uvedené na https://www.microsoft.com webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autoři

> **Rob Vettor**, hlavní architekt cloudového systému/architekt IP – [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft
>
> **Steve "ardalis" Smith**, software architekt a Trainer- [Ardalis.com](https://ardalis.com)

Účastníci a kontroloři:

> **Cesar de la Torre**, Principal program Manager, .NET Team, Microsoft
>
> **Nish Anil**, vedoucí program, tým .NET, Microsoft
>
> **Jeremy Likness**, vedoucí program, tým .NET, Microsoft
>
> **Cecil Phillip**, hlavní poradce pro Cloud, Microsoft

Editory

> **Maira Wenzel**, programový manažer, tým .NET, Microsoft

## <a name="version"></a>Verze

Tato příručka se zapsala jako verze **.NET core 3,1** spolu s mnoha dalšími aktualizacemi, které se týkají stejných "Wave" technologií (tj. Azure a dalších technologií třetích stran), které se shodují v čase s verzí .net Core 3,1.

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

Cílová skupina pro tento průvodce je hlavně vývojářům, vedoucím vývoje a architektům, kteří mají zájem o vytváření aplikací určených pro Cloud.

Sekundární cílová skupina je technickým rozhodnutím, které plánuje vybrat, jestli se mají vytvářet aplikace s využitím nativního přístupu v cloudu.

## <a name="how-you-can-use-this-guide"></a>Jak můžete použít tuto příručku

Tato příručka začíná definováním cloudového nativního nasazení a představením referenční aplikace vytvořené pomocí cloudových nativních principů a technologií. Kromě těchto prvních dvou kapitol se zbytek knihy rozdělí na konkrétní kapitoly zaměřené na témata, která jsou společná pro většinu cloudových nativních aplikací. Pokud se chcete dozvědět víc o přístupech nativních ke cloudu, můžete přejít na libovolnou z těchto kapitol:

- Data a přístup k datům
- Vzory komunikace
- Škálování a škálovatelnost
- Odolnost aplikace
- Monitorování a stav
- Identita a zabezpečení
- DevOps

Tato příručka je k dispozici ve formátu PDF i v online režimu. Nebojte se, že tento dokument předáte nebo odkazuje na jeho online verzi týmu, aby se zajistilo běžné porozumění těmto tématům. Většina těchto témat přináší konzistentní porozumění základním principům a vzorům a kompromisům, které se týkají rozhodnutí souvisejících s těmito tématy. Naším cílem tohoto dokumentu je vybavit týmy a jejich vedoucími informacemi, které potřebují k rozhodování o jejich architektuře, vývoji a hostování svých aplikací.

## <a name="send-your-feedback"></a>Poslat svůj názor

Tato kniha a související ukázky se neustále vyvíjí, takže se vaše zpětná vazba vítá! Pokud máte komentáře k tomu, jak se tato kniha dá zlepšit, použijte část zpětná vazba v dolní části každé stránky založené na [problémech na GitHubu](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Další](introduction.md)
