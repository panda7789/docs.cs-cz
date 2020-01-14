---
title: Scénáře migrace do hybridního cloudu
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Scénáře migrace do hybridního cloudu
ms.date: 04/30/2018
ms.openlocfilehash: dcbb799a45609f8bb811866c4041951abf1fda8b
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937365"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Scénáře migrace do hybridního cloudu

Některé organizace a podniky nemůžou migrovat některé aplikace do veřejných cloudů, jako je Microsoft Azure nebo jiný veřejný cloud z důvodu předpisů nebo jejich vlastních zásad. Je ale pravděpodobné, že by jakákoli organizace mohla využívat některé z svých aplikací ve veřejném cloudu i v místních aplikacích. Smíšené prostředí ale může vést k nadměrné složitosti prostředí v důsledku různých platforem a technologií používaných ve veřejných cloudech i v místních prostředích.

Microsoft poskytuje nejlepší řešení hybridního cloudu, které umožňuje optimalizovat stávající prostředky místně i ve veřejném cloudu a přitom zajistit konzistenci v hybridním cloudu Azure. Můžete maximalizovat stávající dovednosti a získat flexibilní a jednotný přístup k vytváření aplikací, které můžou běžet v cloudu nebo místně, a díky tomu Azure Stack (místní) a Azure (veřejný cloud).

Pokud jde o zabezpečení, můžete spravovat správu a zabezpečení napříč hybridním cloudem. Díky jednotnému přihlašování k místním i cloudovým aplikacím můžete získat kontrolu nad všemi prostředky z vašeho datacentra do cloudu. Toho dosáhnete rozšířením služby Active Directory do hybridního cloudu a pomocí správy identit.

Nakonec můžete bez problémů distribuovat a analyzovat data, použít stejné jazyky pro cloudové a místní prostředky a pomocí analýz a hloubkového učení v Azure rozšířit vaše data bez ohledu na její zdroj.

## <a name="azure-stack"></a>Azure Stack

Azure Stack je hybridní cloudová platforma, která vám umožní poskytovat služby Azure z datového centra vaší organizace. Azure Stack je navržená tak, aby podporovala nové možnosti pro moderní aplikace ve klíčových scénářích, jako jsou Edge a nepřipojená prostředí, nebo splňuje konkrétní požadavky na zabezpečení a dodržování předpisů.

Obrázek 4-13 ukazuje přehled skutečné hybridní cloudové platformy, kterou Microsoft nabízí.

![Diagram hybridní cloudové platformy Microsoft pomocí Azure Stack a Azure](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**Obrázek 4-13.** Hybridní cloudová platforma Microsoft s Azure Stack a Azure

Azure Stack se nabízí ve dvou možnostech nasazení, které odpovídají vašim potřebám:

- Integrované systémy pro službu Azure Stack

- Vývojová sada pro Azure Stack

### <a name="azure-stack-integrated-systems"></a>Integrované systémy pro službu Azure Stack

Azure Stack integrované systémy jsou nabízeny prostřednictvím partnerství s Microsoftem a hardwarovými partnery. Partnerství vytvoří řešení, které nabízí inovace s využitím cloudu, které jsou v rámci správy vyvážené s jednoduchostí. Vzhledem k tomu, že Azure Stack se nabízí jako integrovaný systém hardwaru a softwaru, získáte správnou míru flexibility a kontroly a zároveň stále přijímáte inovace z cloudu. Azure Stack integrovaných systémů v rozsahu od 4 do 12 uzlů a jsou společně podporované hardwarovým partnerem a společností Microsoft. Pomocí Azure Stack integrovaných systémů můžete implementovat nové scénáře pro produkční úlohy.

### <a name="azure-stack-development-kit"></a>Vývojová sada pro Azure Stack

Microsoft Azure Stack Development Kit je nasazení Azure Stack s jedním uzlem, které můžete použít k vyhodnocení a získání informací o Azure Stack. Azure Stack Development Kit můžete použít také jako vývojářské prostředí, kde můžete vyvíjet pomocí rozhraní API a nástrojů, které jsou konzistentní s Azure. Azure Stack Development Kit není určeno pro použití v produkčním prostředí.

### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Hybridní cloud Azure**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Účty služby Active Directory pro kontejnery Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Vytvoření kontejneru s podporou služby Active Directory**

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- **Zvýhodněné hybridní využití Azure licencování**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[Předchozí](life-cycle-ci-cd-pipelines-devops-tools.md)
>[Další](../walkthroughs-technical-get-started-overview.md)
