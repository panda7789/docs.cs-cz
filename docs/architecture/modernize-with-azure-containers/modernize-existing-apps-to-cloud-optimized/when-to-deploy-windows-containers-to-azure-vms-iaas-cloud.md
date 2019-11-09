---
title: Kdy nasadit kontejnery Windows na virtuální počítače Azure (cloud IaaS)
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Kdy nasadit kontejnery Windows na virtuální počítače Azure (IaaS Cloud)
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676898"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Kdy nasadit kontejnery Windows na virtuální počítače Azure (cloud IaaS)

Pokud vaše organizace používá virtuální počítače Azure, a to i v případě, že používáte kontejnery Windows, stále pracujete s IaaS. To znamená, že pro vysoce škálovatelné aplikace v případě potřeby nasazení na více virtuálních počítačů v infrastruktuře s vyrovnáváním zatížení se jedná o operace infrastruktury, opravy operačního systému virtuálních počítačů a složitost infrastruktury. V hlavních scénářích použití kontejnerů Windows ve virtuálním počítači Azure jsou tyto:

- **Vývojové a testovací prostředí**: virtuální počítač v cloudu je ideální pro vývoj a testování v cloudu. V závislosti na vašich potřebách můžete prostředí rychle vytvořit nebo zastavit.

- **Menší a střední požadavky na škálovatelnost**: ve scénářích, kdy budete možná potřebovat několik virtuálních počítačů pro produkční prostředí, může být Správa malého počtu virtuálních počítačů cenově dostupná, dokud se nebudete moct přesunout na pokročilejší PaaS prostředí, jako jsou orchestrace.

- **Produkční prostředí s existujícími nástroji pro nasazení**: možná budete přecházet z místního prostředí, ve kterém jste investovali do nástrojů, abyste mohli provádět složitá nasazení na virtuální počítače nebo holé servery (například Puppet nebo podobné nástroje). Pokud chcete přejít do cloudu s minimálními změnami postupů nasazení v produkčním prostředí, můžete tyto nástroje dál používat k nasazení na virtuální počítače Azure. Pro zlepšení prostředí nasazení ale budete chtít použít kontejnery Windows jako jednotku nasazení.

>[!div class="step-by-step"]
>[Předchozí](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[Další](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
