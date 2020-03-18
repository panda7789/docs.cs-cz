---
title: Kdy nasadit kontejnery Windows na virtuální počítače Azure (cloud IaaS)
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Kdy nasadit kontejnery Windows do virtuálních počítačů Azure (cloud IaaS)
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676898"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Kdy nasadit kontejnery Windows na virtuální počítače Azure (cloud IaaS)

Pokud vaše organizace používá virtuální počítače Azure, i když používáte také kontejnery Windows, stále máte co do činění s IaaS. To znamená, že řešení operací infrastruktury, oprav operačních systémů virtuálních aplikací a složitosti infrastruktury pro vysoce škálovatelné aplikace, když potřebujete nasadit do více virtuálních počítačů v infrastruktuře s vyrovnáváním zatížení. Hlavní scénáře pro použití kontejnerů Windows ve virtuálním počítači Azure jsou:

- **Vývojové/testovací prostředí**: Virtuální virtuální připojení v cloudu je ideální pro vývoj a testování v cloudu. Můžete rychle vytvořit nebo zastavit prostředí v závislosti na vašich potřebách.

- **Malé a střední škálovatelnost potřebuje:** V situacích, kde budete potřebovat jen pár virtuálních počítačů pro vaše produkční prostředí, správa malý počet virtuálních počítačů může být cenově dostupné, dokud můžete přejít do pokročilejších prostředí PaaS, jako je orchestrátory.

- **Produkční prostředí s existujícími nástroji pro nasazení**: Pravděpodobně přecházíte z místního prostředí, do kterého jste investovali do nástrojů pro komplexní nasazení na virtuální počítače nebo servery s holým kovem (jako je Loutka nebo podobné nástroje). Pokud se chcete přesunout do cloudu s minimálními změnami v postupech nasazení produkčního prostředí, můžete pokračovat v používání těchto nástrojů k nasazení do virtuálních počítačů Azure. Kontejnery systému Windows však budete chtít použít jako jednotku nasazení ke zlepšení možnosti nasazení.

>[!div class="step-by-step"]
>[Předchozí](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[další](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
