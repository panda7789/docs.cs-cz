---
title: Migrace na hybridní cloudové scénáře
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Migrace na hybridní cloudové scénáře
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 8885ee8fce4f8c11c14ee8936f3ee0ffd89ece04
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958206"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Migrace na hybridní cloudové scénáře

Některé organizacím a podnikům umožňují nemůžete migrovat některé z aplikací a veřejných cloudů, jako je například Microsoft Azure nebo jiných veřejného cloudu z důvodu předpisy nebo vlastní zásady. Je ale pravděpodobné, že některé z organizací, mohou využít s některé jejich aplikací ve veřejném cloudu a další aplikace místně. Ale smíšeném prostředí může způsobit nadměrné složitosti v prostředích různých platforem a technologií používaných v veřejné cloudy a místními prostředími.

Společnost Microsoft poskytuje nejlepší hybridní cloudové řešení, jeden ve kterém můžete optimalizovat vaše stávající prostředky místní a ve veřejném cloudu, zatímco zajistit konzistenci Azure hybridní cloud. Můžete maximalizovat existujících dovedností a získat flexibilní, jednotný přístup k sestavení aplikace, které můžou běžet v cloudu nebo místně, díky zásobník Azure (místní) a Azure (veřejný cloud).

Pokud jde o zabezpečení, můžete centralizovat správu a zabezpečení mezi hybridní cloud. Můžete získat kontrolu nad všechny prostředky z vašeho datového centra do cloudu, tím, že poskytuje jednotné přihlašování k místnímu a cloudových aplikací. Můžete dosáhnout pomocí rozšíření služby Active Directory k hybridní cloud a pomocí správy identit.

Nakonec můžete distribuovat a bezproblémově analyzovat data, používat stejné jazyky dotazu pro cloudové a místní prostředky a použít analýzy a přímý učení v Azure a rozšíření dat, bez ohledu na její zdroj.

## <a name="azure-stack"></a>Azure zásobníku

Zásobník Azure je hybridní cloudové platformy, která umožňuje poskytovat služby Azure z vaší organizace datového centra. Azure zásobníku je navržen pro podporu nové možnosti pro moderní aplikace v klíčových scénářů, jako je okraj a prostředích bez připojení nebo konkrétní požadavky zabezpečení a dodržování předpisů na schůzku.

Obrázek 4 – 13 ukazuje přehled true hybridní Cloudová platforma, která společnost Microsoft nabízí.

![Hybridní Cloudová platforma Microsoft s zásobník Azure a Azure](./media/image13.jpg)

> **Obrázek 4 – 13.** Hybridní Cloudová platforma Microsoft s zásobník Azure a Azure

Azure zásobník je k dispozici v dvě možnosti nasazení, aby odpovídaly vašim potřebám:

-   Azure zásobníku integrované systémy

-   Azure zásobníku Development Kit

### <a name="azure-stack-integrated-systems"></a>Azure zásobníku integrované systémy

Azure zásobníku integrované systémy jsou nabízena prostřednictvím partnerství partnerů společnosti Microsoft a hardwaru. Spolupráci vytvoří řešení, které nabízí cloudu pracovníky inovací, který je vyvážit s jednoduchost ve správě. Protože zásobník Azure je poskytován jako integrovaný systém hardwaru a softwaru, zobrazí správného množství flexibilitu a řízení, při přijetí stále inovací z cloudu. Azure zásobníku integrované systémy rozsahu velikosti od 4 do 12 uzlů a společně podporuje hardwaru partnera a společnosti Microsoft. Použití Azure zásobníku integrované systémy implementovat nové scénáře pro produkční zatížení.

### <a name="azure-stack-development-kit"></a>Azure zásobníku Development Kit

Microsoft Azure zásobníku Development Kit je jedním uzlem nasazení zásobníku Azure, který můžete použít k vyhodnocení a další informace o Azure zásobníku. Můžete také použít Azure zásobníku Development Kit jako vývojářského prostředí, kde můžete vyvíjet pomocí rozhraní API a nástrojů, které jsou konzistentní s Azure. Azure Development Kit zásobníku není určena pro použití jako provozním prostředí.

### <a name="additional-resources"></a>Další zdroje

-   **Azure hybridního cloudu**

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   **Azure zásobníku**

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   **Účty služby Active Directory pro Windows kontejnery**

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   **Vytvořit kontejner s podporou služby Active Directory**

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   **Licencování Azure hybridní výhody**

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
[Předchozí](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[další](../walkthroughs-technical-get-started-overview.md)
