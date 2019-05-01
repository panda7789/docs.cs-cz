---
title: Kdy nasadit kontejnery Windows na virtuální počítače Azure (cloud IaaS)
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Kdy nasadit kontejnery Windows na virtuálních počítačích Azure (IaaS cloud)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 51217e2c94fd9727c8f7907e791cdebaec98f14f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011954"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Kdy nasadit kontejnery Windows na virtuální počítače Azure (cloud IaaS)

Pokud vaše organizace používá virtuální počítače Azure i v případě také použijete kontejnery Windows, budete pořád řešení IaaS. To znamená zabývajících se operace infrastrukturu, opravy operačního systému virtuálního počítače a složitosti infrastruktury pro vysoce škálovatelné aplikace. když budete chtít nasadit víc virtuálních počítačů v infrastruktuře s vyrovnáváním zatížení. Hlavní scénáře pro použití kontejnerů Windows ve Virtuálním počítači Azure jsou:

- **Prostředí pro vývoj/testování**: Virtuální počítač v cloudu je ideální pro vývoj a testování v cloudu. Můžete rychle vytvořit nebo zastavení prostředí podle svých potřeb.

- **Malé a střední škálovatelnost potřebuje**: Ve scénářích, které vyžadují několika virtuálních počítačů pro produkční prostředí Správa malé množství virtuálních počítačů může být cenově dokud nepřejdete na pokročilejší prostředí PaaS, jako je orchestrátorů.

- **Produkční prostředí se stávajícími nástroji nasazení**: Vám může přesun z v místním prostředí, ve kterém jste investovali v nástroji pro zajištění komplexních nasazení do virtuálních počítačů nebo serverů na holé počítače (jako jsou Puppet nebo podobné nástroje). Pokud chcete přesunout do cloudu s minimálními změnami na postupy nasazení produkčního prostředí, může dál používat tyto nástroje k nasazení do virtuálních počítačů Azure. Ale budete chtít používat kontejnery Windows jako jednotky nasazení vylepšit celkovou funkčnost nasazení.

>[!div class="step-by-step"]
>[Předchozí](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[další](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)