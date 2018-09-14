---
title: Obecné pokyny
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Obecné pokyny
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: e77065614423cd2e7fdb51258a8c7650280d0400
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45609847"
---
# <a name="general-guidance"></a>Obecné pokyny

Tato část obsahuje přehled kdy zvolit .NET Core nebo .NET Framework. Společnost Microsoft poskytuje další podrobnosti o těchto možnostech v následujících částech.

Pro kontejnerizované aplikace Dockeru serveru byste měli použít .NET Core s Linuxem nebo Windows kontejnery, když:

-   Máte požadavky napříč platformami. Můžete třeba používat kontejnery Windows i Linux.

-   Vaše aplikace architektura je založená na mikroslužbách.

-   Potřebujete rychle se pusťte do kontejnerů a aby bylo možné snížit náklady na mají malé náklady na kontejner k dosažení vyšší hustotu nebo více kontejnerů na jednotku hardwaru.

Stručně řečeno když vytvoříte nový kontejnerizované aplikace .NET, měli byste zvážit .NET Core jako výchozí volbu. Má mnoho výhod a nejlépe s filozofií kontejnery a stylu práce.

Další výhodou používání .NET Core je, abyste mohli spouštět souběžně verze rozhraní .NET pro aplikace ve stejném počítači. Tuto výhodu je důležitější pro servery nebo virtuální počítače, které se nepoužívá kontejnery, protože kontejnery izolovat verze rozhraní .NET, které aplikace potřebuje. (Za předpokladu, že jsou kompatibilní s podkladovému operačnímu systému.)

Rozhraní .NET Framework byste měli použít své kontejnerizované aplikace Dockeru serveru při:

-   Vaše aplikace právě používá rozhraní .NET Framework a obsahuje silné závislosti na Windows.

-   Budete muset použít rozhraní Windows API, která nepodporuje .NET Core.

-   Budete muset použít .NET knihovny třetích stran nebo balíčky NuGet, které nejsou dostupné pro .NET Core.

Pomocí rozhraní .NET Framework v Dockeru lze vylepšit prostředí pro vaše nasazení minimalizovat potíže s nasazením. To ["metodou lift and shift" scénář](https://aka.ms/liftandshiftwithcontainersebook) je důležité pro uzavření do kontejneru starších aplikací, které byly původně vyvinuta tradiční rozhraní .NET Framework, jako je webových formulářů ASP.NET, MVC, web apps nebo WCF (Windows Communication Foundation ) služby.

### <a name="additional-resources"></a>Další zdroje

-   **elektronická kniha: modernizace stávajících aplikací rozhraní .NET Framework s využitím Azure a kontejnery Windows**  
    https://aka.ms/liftandshiftwithcontainersebook

-   **Ukázkové aplikace: modernizace starší verze webových aplikací ASP.NET s využitím kontejnerů Windows**  
    https://aka.ms/eshopmodernizing


>[!div class="step-by-step"]
[Předchozí](index.md)
[další](net-core-container-scenarios.md)
