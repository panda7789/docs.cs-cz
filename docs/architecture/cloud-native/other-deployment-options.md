---
title: Další možnosti nasazení kontejnerů
description: Další možnosti nasazení kontejnerů pomocí Azure
ms.date: 05/13/2020
ms.openlocfilehash: acb022e3d4fd4862c592fa571894e1b8ce17f465
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613756"
---
# <a name="other-container-deployment-options"></a>Další možnosti nasazení kontejnerů

Kromě služby Azure Kubernetes Service (AKS) můžete také nasadit kontejnery pro Azure App Service kontejnerů a Azure Container Instances.

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a>Kdy má smysl nasadit do App Service pro kontejnery?

Jednoduché provozní aplikace, které nevyžadují orchestraci, jsou vhodné pro Azure App Service pro kontejnery.

## <a name="how-to-deploy-to-app-service-for-containers"></a>Postup nasazení na App Service pro kontejnery

K nasazení do [Azure App Service pro kontejnery](https://azure.microsoft.com/services/app-service/containers/)budete potřebovat instanci Azure Container Registry (ACR) a přihlašovací údaje pro přístup k ní. Nahrajte image kontejneru do úložiště ACR, aby se mohla načíst do vašeho Azure App Service. Po dokončení můžete aplikaci nakonfigurovat pro průběžné nasazování. Tím se automaticky nasadí aktualizace, kdykoli se obrázek změní v ACR.

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a>Kdy má smysl nasadit do Azure Container Instances?

[Azure Container Instances (ACI)](https://azure.microsoft.com/services/container-instances/) umožňuje spouštět kontejnery Docker ve spravovaném cloudovém prostředí bez serveru, aniž by bylo nutné nastavovat virtuální počítače nebo clustery. Jedná se o skvělé řešení pro krátkodobé spuštěné úlohy, které se dají spouštět v izolovaném kontejneru. Zvažte ACI pro jednoduché služby, testovací scénáře, automatizaci úloh a vytváření úloh. ACI se rozpíná – instance kontejneru, provede úlohu a pak se ukončí.

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a>Jak nasadit aplikaci do Azure Container Instances

K nasazení na [Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/)budete potřebovat Azure Container Registry (ACR) a přihlašovací údaje pro přístup k ní. Po nahrání image kontejneru do úložiště je k dispozici pro vložení do ACI. Můžete pracovat s ACI pomocí rozhraní příkazového řádku Azure Portal nebo. ACR zajišťuje úzkou integraci s ACI. Obrázek 3-14 ukazuje, jak odeslat jednotlivé image kontejneru do ACR.

![Instance spuštění Azure Container Registry](./media/acr-runinstance-contextmenu.png)

**Obrázek 3-14**. Instance spuštění Azure Container Registry

Vytvoření instance v ACI se dá rychle provést. Zadejte registr imagí, informace o skupině prostředků Azure, velikost paměti, která se má přidělit, a port, na kterém se má naslouchat. [V tomto rychlém startu se dozvíte, jak nasadit instanci kontejneru pro ACI pomocí Azure Portal](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal).

Jakmile se nasazení dokončí, najděte nově nasazenou IP adresu kontejneru a pomocí portu, který jste zadali, nahlaste s ním komunikaci.

Azure Container Instances nabízí nejrychlejší způsob, jak spustit jednoduché úlohy kontejneru v Azure. Nemusíte konfigurovat službu App Service, Orchestrator ani virtuální počítač. Pro scénáře, kde potřebujete úplnou orchestraci kontejnerů, zjišťování služeb, automatické škálování nebo koordinované upgrady, doporučujeme službu Azure Kubernetes Service (AKS).

## <a name="references"></a>Odkazy

- [Co je Kubernetes?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Instalace Kubernetes pomocí Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube vs Docker Desktop](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Visual Studio Tools for Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)
- [Principy studeného startu bez serveru](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [Předem zahřívání Azure Functions instance](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [Vytvoření funkce v Linuxu pomocí vlastní image](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [Spuštění Azure Functions v kontejneru Docker](https://markheath.net/post/azure-functions-docker)
- [Vytvoření funkce v Linuxu pomocí vlastní image](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [Azure Functions pomocí automatického škálování založeného na událostech Kubernetes](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)
- [Kanárské verze](https://martinfowler.com/bliki/CanaryRelease.html)
- [Azure Dev Spaces s VS Code](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore)
- [Azure Dev Spaces se sadou Visual Studio](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore-visualstudio)
- [AKS více fondů uzlů](https://docs.microsoft.com/azure/aks/use-multiple-node-pools)
- [Automatické škálování clusteru AKS](https://docs.microsoft.com/azure/aks/cluster-autoscaler)
- [Kurz: škálování aplikací v AKS](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale)
- [Hostování a škálování Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-scale)
- [Azure Container Instances docs](https://docs.microsoft.com/azure/container-instances/)
- [Nasadit instanci kontejneru z ACR](https://docs.microsoft.com/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
>[Předchozí](scale-containers-serverless.md) 
> [Další](communication-patterns.md)
