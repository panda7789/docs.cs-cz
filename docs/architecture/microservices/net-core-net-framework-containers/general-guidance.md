---
title: Obecné pokyny
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Obecné pokyny
ms.date: 09/11/2018
ms.openlocfilehash: 6e63d7804abc1703f17378584d58d66a933022c7
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306874"
---
# <a name="general-guidance"></a>Obecné pokyny

V této části najdete přehled, kdy zvolit rozhraní .NET Core nebo .NET Framework. Další podrobnosti o těchto volbách poskytujeme v níže uvedených částech.

Použijte .NET Core s kontejnery Linux nebo Windows pro vaši kontejnerovou aplikaci Docker, která je v těchto případech:

- Máte různé požadavky na více platforem. Například chcete použít kontejnery Linux i Windows.

- Architektura vaší aplikace je založena na mikroslužbách.

- Je potřeba začít kontejnery rychle a chtít malé nároky na kontejner, abyste dosáhli lepší hustoty nebo většího počtu kontejnerů na jednotku hardwaru za účelem snížení nákladů.

V krátké době, kdy vytváříte nové kontejnery aplikací .NET, byste měli zvážit jako výchozí volbu .NET Core. Má spoustu výhod a nejlépe vyhovuje kontejnerům filozofie a stylu práce.

Další výhodou používání .NET Core je, že pro aplikace ve stejném počítači můžete spouštět souběžné verze .NET. Tato výhoda je důležitější pro servery nebo virtuální počítače, které nepoužívají kontejnery, protože kontejnery izolují verze rozhraní .NET, které aplikace potřebuje. (Pokud jsou kompatibilní s podkladovým operačním systémem.)

Použijte .NET Framework pro svou kontejnerovou aplikaci Docker Server, když:

- Vaše aplikace aktuálně používá .NET Framework a má silné závislosti v systému Windows.

- Je nutné použít rozhraní API systému Windows, která nejsou podporována rozhraním .NET Core.

- Je nutné použít knihovny .NET nebo balíčky NuGet třetích stran, které nejsou k dispozici pro .NET Core.

Použití .NET Framework v Docker může zlepšit vaše prostředí nasazení díky minimalizaci problémů s nasazením. Tento [scénář "zvednutí a posunutí"](https://aka.ms/liftandshiftwithcontainersebook) je důležitý pro uzavření starší verze aplikací, které byly původně vyvinuty s tradičním .NET Framework, jako jsou ASP.NET WebForms, MVC Web Apps nebo WCF (Windows Communication Foundation) služby.

### <a name="additional-resources"></a>Další zdroje

- **Elektronická kniha: modernizovat stávající aplikace .NET Framework s kontejnery Azure a Windows**  
    <https://aka.ms/liftandshiftwithcontainersebook>

- **Ukázkové aplikace: moderní verze starších webových aplikací v ASP.NET pomocí kontejnerů Windows**  
    <https://aka.ms/eshopmodernizing>

>[!div class="step-by-step"]
>[Předchozí](index.md) 
> [Další](net-core-container-scenarios.md)
