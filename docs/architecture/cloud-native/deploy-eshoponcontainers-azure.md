---
title: Nasazení eShopOnContainers do Azure
description: Nasazení aplikace eShopOnContainers pomocí služby Azure Kubernetes, Helm a DevSpaces.
ms.date: 06/30/2019
ms.openlocfilehash: 21033cc904dc595193c69f3452ce2522740f8ff6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183271"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>Nasazení eShopOnContainers do Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Logiku podporující aplikaci eShopOnContainers může podporovat Azure pomocí nejrůznějších služeb. Doporučený postup je využít Kubernetes pomocí služby Azure Kubernetes Service (AKS). To se dá zkombinovat s nasazením Helm, aby se zajistila jednoduchá opakovaná konfigurace infrastruktury. Vývojáři mohou volitelně využít Azure Dev Spaces Kubernetes jako součást jejich procesu vývoje. Další možností je hostování funkcí aplikace pomocí funkcí bez serveru Azure, jako jsou Azure Functions a Azure Logic Apps.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Pokud byste chtěli hostovat aplikaci eShopOnContainers ve vlastním clusteru AKS, je prvním krokem vytvoření clusteru. Můžete to provést pomocí Azure Portal, který vás provede potřebnými kroky, nebo můžete použít Azure CLI, abyste měli jistotu, že v takovém případě povolíte Access Control a směrování na základě rolí (RBAC). V dokumentaci k eShopOnContainers najdete postup, který se zabývá vytvořením vlastního clusteru AKS. Po vytvoření clusteru musíte povolit přístup k řídicímu panelu Kubernetes. v takovém případě byste měli být schopni přejít na řídicí panel Kubernetes a spravovat cluster.

Jakmile je cluster vytvořený a nakonfigurovaný, můžete do něj nasadit aplikaci pomocí Helm a pokladny.

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>Nasazení do služby Azure Kubernetes pomocí Helm

Základní nasazení na AKS můžou používat vlastní skripty rozhraní příkazového řádku nebo jednoduché soubory nasazení, ale složitější aplikace by měly používat nástroj pro správu závislostí, jako je Helm. Helm je udržována v rámci cloudové výpočetní platformy a pomáhá definovat, instalovat a upgradovat Kubernetes aplikace. Helm se skládá z klienta příkazového řádku, Helm, který používá grafy Helm, a součásti v clusteru. Grafy Helm používají standardní soubory ve formátu YAML k popisu související sady Kubernetesch prostředků a obvykle jsou společně s aplikací, které popisují. Grafy Helm se od jednoduchých po složité v závislosti na požadavcích instalace, které popisují.

Grafy eShopOnContainers Helm najdete ve složce/k8s/Helm. Obrázek 2-6 ukazuje, jak jsou různé komponenty aplikace uspořádány do struktury složek, kterou používá Helm k definování a správě nasazení.

![Obrázek architektury](./media/eshoponcontainers-helm-folder.png)
eShopOnContainers**2-6**. Složka Helm eShopOnContainers

Jednotlivé komponenty se instalují pomocí `helm install` příkazu. Tyto příkazy jsou snadno skriptované a eShopOnContainers poskytuje skript "nasadit vše", který projde různými komponentami a nainstaluje je pomocí příslušných Helm grafů. Výsledkem je opakovaný proces, ve kterém je verze aplikace ve správě zdrojového kódu, kterou může kdokoli v týmu nasadit do clusteru AKS s jedním řádkovým příkazem skriptu. Zejména v kombinaci s Azure Dev Spaces umožňuje vývojářům snadno diagnostikovat a testovat jejich jednotlivé změny v cloudových nativních aplikacích založených na mikroslužbách.

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Azure Dev Spaces pomáhá jednotlivým vývojářům hostovat během vývoje svou vlastní jedinečnou verzi clusterů AKS v Azure. To minimalizuje požadavky na místní počítače a umožňuje členům týmu rychle zjistit, jak se jejich změny chovají ve skutečném prostředí AKS. Azure Dev Spaces nabízí rozhraní příkazového řádku, které se vývojářům používá ke správě svých vývojových prostorů a k nasazení v konkrétním podřízeném prostoru pro vývoj podle potřeby. Na každý podřízený prostor pro vývoj se odkazuje pomocí jedinečné subdomény adresy URL, která umožňuje souběžné nasazení upravených clusterů, aby se jednotliví vývojáři mohli vyhnout konfliktům probíhajících vzájemně pracujících úloh. Na obrázku 2-7 vidíte, jak vývojář Susie nasadil svoji vlastní verzi mikroslužeb kol do svého vývojového prostoru. Potom je možné otestovat své změny pomocí vlastní adresy URL začínající názvem jejího místa (susie.s.dev.myapp.eus.azds.io).

![Obrázek architektury](./media/azure-devspaces-one.png)
eShopOnContainers**2-7**. Vývojář Susie nasadí svoji vlastní verzi mikroslužby bicyklů a otestuje ji.

V současné době vývojář Jan přizpůsobuje mikroslužbu rezervací a potřebuje testovat své změny. Může nasadit své změny do vlastního prostoru pro vývoj bez konfliktu se změnami Susie, jak je znázorněno na obrázku 2-8. Může otestovat své změny pomocí vlastní adresy URL, která má předponu s názvem svého místa (john.s.dev.myapp.eus.azds.io).

![Obrázek architektury](./media/azure-devspaces-two.png)
eShopOnContainers**2-8**. Vývojář Jan nasadí svoji vlastní verzi mikroslužby rezervací a otestuje ji bez konfliktu s ostatními vývojáři.

Pomocí Azure Dev Spaces můžou týmy pracovat přímo se AKS a přitom nezávisle měnit, nasazovat a testovat jejich změny. Tento přístup omezuje nutnost samostatných vyhrazených hostovaných prostředí, protože každý vývojář efektivně má své vlastní prostředí AKS. Vývojáři mohou pracovat s Azure Dev Spaces pomocí svého rozhraní příkazového řádku nebo spustit aplikaci pro Azure Dev Spaces přímo ze sady Visual Studio. [Přečtěte si další informace o tom, jak Azure Dev Spaces fungují a jsou nakonfigurované.](https://docs.microsoft.com/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Functions a Logic Apps (bez serveru)

Ukázka eShopOnContainers zahrnuje podporu pro sledování online marketingových kampaní. Funkce Azure slouží k získání podrobností o marketingové kampani pro dané ID kampaně. Místo vytváření kompletní aplikace ASP.NET Core pro tento účel je jeden koncový bod Azure Functions jednodušší a dostatečný. Azure Functions mít mnohem jednodušší model sestavování a nasazování než úplné ASP.NET Core aplikace, zejména pokud je nakonfigurované tak, aby běžely v Kubernetes. Nasazení funkce se skriptuje pomocí šablon Azure Resource Manager (ARM) a rozhraní příkazového řádku Azure CLI. Tato mikroslužba podrobností o kampani není dostupná pro zákazníka a nemá stejné požadavky jako online obchod, takže je vhodným kandidátem na Azure Functions. Funkce vyžaduje, aby některá konfigurace fungovala správně, jako jsou data připojovacího řetězce databáze a nastavení obrázku základní identifikátor URI. Azure Functions můžete nakonfigurovat na webu Azure Portal.

## <a name="references"></a>Odkazy

- [eShopOnContainers: Vytvoření clusteru Kubernetes v AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [eShopOnContainers: Azure Dev mezery](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[Předchozí](map-eshoponcontainers-azure-services.md)
>[Další](centralized-configuration.md)
