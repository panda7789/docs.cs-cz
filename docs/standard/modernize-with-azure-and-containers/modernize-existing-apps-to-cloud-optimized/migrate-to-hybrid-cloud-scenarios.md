---
title: Migrace na scénáři s hybridními cloudy
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Migrace na scénáři s hybridními cloudy
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 3d6fc272854654d890559d5db032b05667627d94
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147343"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Migrace na scénáři s hybridními cloudy

Některé organizace a podniky nemůžete migrovat některé ze svých aplikací do veřejných cloudů, jako je například Microsoft Azure nebo jiného veřejného cloudu kvůli předpisy nebo vlastní zásady. Je ale pravděpodobné, že každá organizace může mít užitek z některých aplikací ve veřejném cloudu a dalších aplikací v místním prostředí s. Ale smíšeném prostředí může vést k nadměrné složitosti v prostředí kvůli různé platformy a technologie používané ve veřejných cloudech a v místních prostředích.

Společnost Microsoft poskytuje nejlepší hybridní cloudové řešení, jeden ve kterém můžete optimalizovat stávající prostředky místní a ve veřejném cloudu, zatímco zajistit konzistenci v Azure hybridního cloudu. Můžete maximalizovat stávající dovednosti a získejte flexibilní a Unifikovaný přístup k vytváření aplikací, které můžou běžet v cloudu nebo místně, díky Azure Stack (v místním prostředí) a Azure (veřejný cloud).

Při rozhodování o zabezpečení, můžete centralizovat správu a zabezpečení napříč hybridním cloudu. Můžete mít kontrolu nad všemi prostředky z vašeho datového centra do cloudu a tím, že poskytuje jednotné přihlašování k místním a cloudovým aplikacím. Můžete dosáhnout pomocí rozšíření služby Active Directory na hybridní cloud a s využitím správy identit.

Nakonec můžete distribuovat a analyzovat data bez problémů, použít stejné dotazovací jazyky pro cloudové a místní prostředky a analýz a obsáhlého learningu v Azure obohatíte vaše data bez ohledu na jeho zdroj.

## <a name="azure-stack"></a>Azure Stack

Azure Stack je hybridní Cloudová platforma, která umožňuje poskytovat služby Azure z datového centra vaší organizace. Azure Stack je navržena pro podporu nové možnosti pro moderní aplikace v klíčových scénářů, jako je edge a nepřipojené prostředí nebo specifické požadavky zabezpečení a dodržování předpisů na schůzku.

Obrázek 4 – 13 ukazuje přehled skutečně hybridní Cloudová platforma, která nabízí Microsoft.

![Hybridní Cloudová platforma Microsoftu pomocí služby Azure Stack a Azure](./media/image13.jpg)

> **Obrázek 4 – 13.** Hybridní Cloudová platforma Microsoftu pomocí služby Azure Stack a Azure

Azure Stack se nabízí ve dvou možnosti nasazení podle svých potřeb:

-   Integrované systémy pro službu Azure Stack

-   Vývojová sada pro Azure Stack

### <a name="azure-stack-integrated-systems"></a>Integrované systémy pro službu Azure Stack

Azure Stack integrované systémy jsou nabízeny Díky partnerství Microsoftu a hardwarových partnerů. Partnerství vytvoří řešení, které nabízí cloud tempem inovací vyrovnávaném pomocí jednoduchost ve správě. Protože Azure Stack se nabízí jako integrovaný systém softwaru a hardwaru, získáte úroveň flexibility a kontroly, při přijetí stále inovace v cloudu. Systémy ve službě Azure Stack integrované velikosti od 4 do 12 uzlů v rozsahu a společně podporuje hardwarových partnerů a Microsoft. Implementace nové scénáře pro vaše produkční úlohy pomocí integrované systémy Azure Stack.

### <a name="azure-stack-development-kit"></a>Vývojová sada pro Azure Stack

Microsoft Azure Stack Development Kit je jedním uzlem nasazení služby Azure Stack, který můžete použít k vyhodnocení a další informace o službě Azure Stack. Jako prostředí pro vývojáře, kde můžete při vývoji využít rozhraní API a nabízí nástroje, které jsou konzistentní s Azure můžete také použít Azure Stack Development Kit. Azure Stack Development Kit není určena pro použití jako v provozním prostředí.

### <a name="additional-resources"></a>Další zdroje

-   **Azure hybridního cloudu**

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   **Azure Stack**

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   **Účty služby Active Directory pro kontejnery Windows**

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   **Vytvořit kontejner s podporou služby Active Directory**

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   **Licencování programu Azure Hybrid Benefit**

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
>[Předchozí](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[další](../walkthroughs-technical-get-started-overview.md)