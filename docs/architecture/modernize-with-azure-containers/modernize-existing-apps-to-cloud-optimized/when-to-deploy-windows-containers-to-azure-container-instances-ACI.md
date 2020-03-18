---
title: Kdy nasadit kontejnery Windows do instancí kontejnerů Azure (ACI)
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Kdy nasadit kontejnery Windows do instancí kontejnerů Azure (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676907"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Kdy nasadit kontejnery Windows do instancí kontejnerů Azure (ACI)

Azure Container Instances hlavní hodnota návrh je, že můžete okamžitě nasadit kontejnery do něj a nemusíte udržovat toto prostředí, nemusíte upgradovat/opravit základní operační systém nebo virtuální počítače, vše, co je transparentní a stačí nasadit kontejnery do připraveného k použití prostředí.

Důvody a scénáře, když byste chtěli použít ACI jsou podobné hlavní scénáře při použití virtuálních počítačích Azure s kontejnery, takže v podstatě hlavní scénáře pro použití Azure Container Instances jsou:

- **Scénáře pro vývoj a testování**
- **Automatizace úloh**
- **Ci/CD agenti**
- **Malé/zmenšené dávkové zpracování**
- **Jednoduché webové aplikace**

Jednoduchý scénář webových aplikací je spravedlivý scénář pro ACI, ale vezměte v úvahu, že vzhledem k tomu, že v ACI můžete mít pouze jednu instanci kontejneru na bitovou kopii kontejneru, nebudete mít vysokou dostupnost a máte pouze omezenou škálovatelnost.

I v případě, že aci je považován za infrastrukturu, protože poskytuje pouze jeden kontejner instance, je obrovská výhoda ve srovnání s běžnými virtuálními počítači Azure s Windows Server. S ACI, stačí nasadit kontejnery do prostředí s vlastním údržbou a stačí zaplatit za tyto kontejnery. Nemusíte udržovat/ aktualizovat/opravovat virtuální uživatele, takže je to mnohem lepší platforma pro většinu scénářů, kde můžete používat virtuální aplikace s kontejnery. Použití ACI je přímočaré, stačí nasadit kontejner, není třeba vytvářet prostředí virtuálního uživatele, které právě nasadíte kontejnery.

Hlavní výhody azure container instance (ACI) jsou:

- Spuštění kontejnerů bez správy serverů
- Zvyšte agilitu díky kontejnerům na vyžádání
- Nasazujte kontejnery do cloudu s nebývalou jednoduchostí a rychlostí – s jediným příkazem.
- Bezpečné aplikace s izolací hypervisoru

Stručně řečeno, s ACI můžete vyvíjet aplikace rychle bez správy virtuálních počítačů nebo se museli učit nové nástroje. Je to jen vaše aplikace, v kontejneru, běží v cloudu.

> [!div class="step-by-step"]
> [Předchozí](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [další](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
