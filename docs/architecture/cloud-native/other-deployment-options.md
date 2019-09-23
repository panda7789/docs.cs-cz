---
title: Další možnosti nasazení kontejnerů
description: Další možnosti nasazení kontejnerů pomocí Azure
ms.date: 06/30/2019
ms.openlocfilehash: 892514417cb8650c28b7491315f767758278ad6e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184881"
---
# <a name="other-container-deployment-options"></a>Další možnosti nasazení kontejnerů

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kromě nasazení na AKS můžete také nasadit kontejnery pro Azure App Service kontejnerů a Azure Container Instances.

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a>Kdy má smysl nasadit do App Service pro kontejnery?

Jednoduché provozní aplikace, které nevyžadují orchestraci, jsou vhodné pro Azure App Service pro kontejnery.

## <a name="how-to-deploy-to-app-service-for-containers"></a>Postup nasazení na App Service pro kontejnery

Aby bylo možné nasadit [Azure App Service pro kontejnery](https://azure.microsoft.com/services/app-service/containers/), je nutné nakonfigurovat Azure Container Registry (ACR) a přihlašovací údaje pro přístup k ní. Nahrajte kontejner, který máte v úmyslu hostovat do registru, aby bylo možné ho načíst do svého Azure App Service. Po vytvoření můžete aplikaci nakonfigurovat pro průběžné nasazování, která bude automaticky nasazovat aktualizace do aplikace vždy, když aktualizujete odpovídající obrázek v ACR.

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a>Kdy má smysl nasadit do Azure Container Instances?

Azure Container Instances se nejlépe používají pro testovací scénáře. Poskytují rychlý a jednoduchý způsob, jak nasadit aplikaci do instance kontejneru hostovaného v cloudu. Použijte je k testování nebo demo aplikací, pokud nepotřebujete funkce škálování a orchestrace nabízené službou Azure Kubernetes.

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a>Jak nasadit aplikaci do Azure Container Instances

K nasazení na [Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/)je nutné nakonfigurovat Azure Container Registry (ACR) a přihlašovací údaje pro přístup k ní. Je také potřeba, abyste image kontejneru vložili do registru, takže je možné je načíst do ACI. Můžete pracovat s ACI pomocí rozhraní příkazového řádku Azure nebo prostřednictvím portálu. Služby Azure Container Registry usnadňují nasazení jednotlivých instancí kontejnerů do ACI přímo v rámci registru, jak je znázorněno na obrázku 3-14.

![Instance spuštění Azure Container Registry](./media/acr-runinstance-contextmenu.png)

**Obrázek 3-14**. Instance spuštění Azure Container Registry

Vytvořením instance kontejneru z registru stačí zadat obvyklá nastavení Azure (název, předplatné, skupinu prostředků a umístění), kolik paměti se má přidělit kontejneru, a port, na kterém by měl naslouchat. [V tomto rychlém startu se dozvíte, jak nasadit instanci kontejneru pro ACI pomocí Azure Portal](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal).

Jakmile se nasazení dokončí, najděte nově nasazenou IP adresu kontejneru a pomocí portu, který jste zadali, nahlaste s ním komunikaci.

Azure Container Instances nabízí nejrychlejší a nejjednodušší způsob spouštění kontejneru v Azure. Není nutné konfigurovat službu App Service ani produkt Orchestrator ani řešit virtuální počítače. Z důvodu zjednodušení by se však ACI měl primárně použít pro účely testování. Pokud vaše aplikace vyžaduje automatickou škálovatelnost, je pro hostování vaší aplikace k dispozici více kontejnerů, které jsou nakonfigurovány tak, aby spolupracovaly, případně i jakékoli další komplexní funkce.

## <a name="references"></a>Odkazy

- [Azure Container Instances docs](https://docs.microsoft.com/azure/container-instances/)
- [Nasadit instanci kontejneru z ACR](https://docs.microsoft.com/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
>[Předchozí](scale-containers-serverless.md)
>[Další](communication-patterns.md) <!-- Next Chapter -->
