---
title: Scénáře migrace do hybridního cloudu
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Migrace do hybridních cloudových scénářů
ms.date: 04/30/2018
ms.openlocfilehash: dcbb799a45609f8bb811866c4041951abf1fda8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937365"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Scénáře migrace do hybridního cloudu

Některé organizace a podniky nemohou migrovat některé své aplikace do veřejných cloudů, jako je Microsoft Azure nebo jakýkoli jiný veřejný cloud kvůli předpisům nebo vlastním zásadám. Je však pravděpodobné, že každá organizace může mít prospěch z toho, že má některé své aplikace ve veřejném cloudu a v dalších místních aplikacích. Smíšené prostředí však může vést k nadměrné složitosti prostředí kvůli různým platformám a technologiím používaným ve veřejných cloudech oproti místním prostředím.

Microsoft poskytuje nejlepší hybridní cloudové řešení, ve kterém můžete optimalizovat stávající prostředky místně a ve veřejném cloudu a zároveň zajistit konzistenci v hybridním cloudu Azure. Díky Azure Stacku (místní) a Azure (veřejný cloud) můžete maximalizovat stávající dovednosti a získat flexibilní a jednotný přístup k vytváření aplikací, které můžou běžet v cloudu nebo místně.

Pokud jde o zabezpečení, můžete centralizovat správu a zabezpečení v celém hybridním cloudu. Můžete získat kontrolu nad všemi prostředky, z vašeho datového centra do cloudu, tím, že poskytuje jednotné přihlašování k místním a cloudovým aplikacím. Toho lze dosáhnout rozšířením služby Active Directory na hybridní cloud a pomocí správy identit.

Nakonec můžete bez problémů distribuovat a analyzovat data, používat stejné jazyky dotazů pro cloudové a místní prostředky a používat analýzy a hloubkové učení v Azure k obohacení dat bez ohledu na jejich zdroj.

## <a name="azure-stack"></a>Azure Stack

Azure Stack je hybridní cloudová platforma, která vám umožní poskytovat služby Azure z datového centra vaší organizace. Azure Stack je navržený tak, aby podporoval nové možnosti pro vaše moderní aplikace v klíčových scénářích, jako jsou hraniční a nepropojená prostředí, nebo splnění specifických požadavků na zabezpečení a dodržování předpisů.

Obrázek 4-13 ukazuje přehled skutečné hybridní cloudové platformy, kterou Microsoft nabízí.

![Diagram hybridní cloudové platformy Microsoftu s Azure Stack a Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**Obrázek 4-13.** Hybridní cloudová platforma Microsoftu s Azure Stackem a Azure

Azure Stack se nabízí ve dvou možnostech nasazení, které splní vaše potřeby:

- Integrované systémy Azure Stack

- Azure Stack Development Kit

### <a name="azure-stack-integrated-systems"></a>Integrované systémy Azure Stack

Integrované systémy Azure Stack jsou nabízeny prostřednictvím partnerství Microsoftu a hardwarových partnerů. Partnerství vytváří řešení, které nabízí inovace v cloudovém tempu, které je vyváženo jednoduchostí správy. Vzhledem k tomu, že Azure Stack je nabízen jako integrovaný systém hardwaru a softwaru, získáte správné množství flexibility a kontroly a zároveň přijímáte inovace z cloudu. Integrované systémy Azure Stack se pohybují ve velikosti od 4 do 12 uzlů a jsou společně podporovány hardwarovým partnerem a Microsoftem. Pomocí integrovaných systémů Azure Stack implementujte nové scénáře pro vaše produkční úlohy.

### <a name="azure-stack-development-kit"></a>Azure Stack Development Kit

Microsoft Azure Stack Development Kit je jednouzde nasazení Azure Stack, které můžete použít k vyhodnocení a získat informace o Azure Stack. Azure Stack Development Kit můžete také použít jako vývojářské prostředí, kde můžete vyvíjet pomocí api a nástrojů, které jsou konzistentní s Azure. Azure Stack Development Kit není určen pro použití jako produkční prostředí.

### <a name="additional-resources"></a>Další zdroje

- **Hybridní cloud Azure**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Účty služby Active Directory pro kontejnery systému Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Vytvoření kontejneru s podporou služby Active Directory**

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- **Licencování hybridních výhod Azure**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[Předchozí](life-cycle-ci-cd-pipelines-devops-tools.md)
>[další](../walkthroughs-technical-get-started-overview.md)
