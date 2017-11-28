---
title: "Když k nasazení Windows kontejnery na virtuálních počítačích Azure (IaaS cloud)"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Když k nasazení Windows kontejnery na virtuálních počítačích Azure (IaaS cloud)"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 6fa7dbde3b7dad24047b31ee708a8a0df2635f09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Když k nasazení Windows kontejnery na virtuálních počítačích Azure (IaaS cloud)

Pokud vaše organizace používá virtuálních počítačích Azure, i když používáte také Windows kontejnery, jste stále řešení IaaS. To znamená zabývajících se operace infrastruktury, oprav operačního systému virtuálního počítače a složitost infrastruktury pro vysoce škálovatelné aplikace, pokud budete potřebovat k nasazení na víc virtuálních počítačů na infrastruktuře vyrovnáváním zatížení. Hlavní scénáře pro použití kontejnerů Windows virtuální počítač Azure, jsou:

-   **Prostředí pro vývoj/testování**: je ideální pro vývoj a testování v cloudu A virtuálních počítačů v cloudu. Můžete rychle vytvořit nebo zastavit prostředím podle potřeby.

-   **Malé a střední škálovatelnost musí**: ve scénářích, kde je může být nutné si během několika virtuálních počítačů pro produkční prostředí, Správa malý počet virtuálních počítačů může být cenově dostupný dokud můžete přesunout k pokročilejším prostředí PaaS, třeba orchestrators.

-   **Produkčním prostředí se stávajícími nástroji nasazení**: vám může přechod z prostředí na místě, ve kterém můžete investovaly do nástroje pro vytváření komplexních nasazení virtuálních počítačů nebo úplné obnovení serverů (například Puppet nebo podobné nástroje). Chcete-li přesunout do cloudu s minimálními změnami postupy nasazení produkčního prostředí, může pokračovat pomocí těchto nástrojů pro nasazení na virtuálních počítačích Azure. Ale budete chtít použít Windows kontejnery jako jednotky nasazení lepší nasazení.

>[!div class="step-by-step"]
[Předchozí](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[další](when-to-deploy-windows-containers-to-service-fabric.md)
