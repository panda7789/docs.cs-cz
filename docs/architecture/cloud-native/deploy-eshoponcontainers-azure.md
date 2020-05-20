---
title: Nasazení aplikace eShopOnContainers do Azure
description: Nasazení aplikace eShopOnContainers pomocí služby Azure Kubernetes, Helm a DevSpaces.
ms.date: 05/13/2020
ms.openlocfilehash: 93a2848f095d7593e1e169f4a6c6c1818a76217d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614094"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>Nasazení aplikace eShopOnContainers do Azure

Aplikace eShopOnContainers se dá nasadit na celou řadu platforem Azure. Doporučený postup je nasadit aplikaci do služby Azure Kubernetes Services (AKS). Helm, nástroj pro nasazení Kubernetes, je k dispozici, aby se snížila složitost nasazení. V případě potřeby můžou vývojáři implementovat Azure Dev Spaces pro Kubernetes, aby se zjednodušil proces vývoje.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Pro hostování eShop v AKS je prvním krokem vytvoření clusteru AKS. K tomu můžete použít Azure Portal, které vás provedou potřebnými kroky. Můžete také vytvořit cluster z Azure CLI, přičemž se ujistěte, že jste povolili Access Control na základě rolí (RBAC) a směrování aplikací. V dokumentaci k eShopOnContainers najdete postup vytvoření vlastního clusteru AKS. Po vytvoření můžete cluster otevřít a spravovat pomocí řídicího panelu Kubernetes.

Aplikaci eShop teď můžete nasadit do clusteru s využitím Helm a.

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>Nasazení do služby Azure Kubernetes pomocí Helm

Helm je nástroj Správce balíčků aplikace, který pracuje přímo s Kubernetes. Pomůže vám definovat, instalovat a upgradovat Kubernetes aplikace. I když je možné jednoduché aplikace nasadit do AKS pomocí vlastních skriptů CLI nebo jednoduchých souborů nasazení, komplexní aplikace můžou obsahovat spoustu Kubernetes objektů a využívat výhod Helm.

Pomocí Helm aplikace zahrnují konfigurační soubory založené na textu s názvem Helm grafy, které deklarativně popisují aplikaci a konfiguraci v balíčcích Helm. Grafy používají standardní soubory ve formátu YAML k popisu související sady prostředků Kubernetes. Jsou ve verzi spolu s kódem aplikace, které popisují. Grafy Helm se od jednoduchých po složité v závislosti na požadavcích instalace, které popisují.

Helm se skládá z klientského nástroje příkazového řádku, který využívá grafy Helm a spouští příkazy pro serverovou komponentu s názvem, do které končí. Do služby komunikuje s rozhraním API Kubernetes, aby bylo zajištěno správné zřizování vašich kontejnerových úloh. Helm je udržována v rámci platformy Cloud-Native Computing.

Následující soubor YAML prezentuje šablonu Helm:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.app.svc.marketing }}
  labels:
    app: {{ template "marketing-api.name" . }}
    chart: {{ template "marketing-api.chart" . }}
    release: {{ .Release.Name }}
    heritage: {{ .Release.Service }}
spec:
  type: {{ .Values.service.type }}
  ports:
    - port: {{ .Values.service.port }}
      targetPort: http
      protocol: TCP
      name: http
  selector:
    app: {{ template "marketing-api.name" . }}
    release: {{ .Release.Name }}
```

Všimněte si, jak šablona popisuje dynamickou sadu párů klíč/hodnota. Při vyvolání šablony jsou hodnoty, které jsou uzavřeny ve složených závorkách, načítány z jiných konfiguračních souborů založených na YAML.

Grafy eShopOnContainers Helm najdete ve složce/k8s/Helm. Obrázek 2-6 ukazuje, jak jsou různé komponenty aplikace uspořádány do struktury složek, kterou používá Helm k definování a správě nasazení.

![Obrázek architektury eShopOnContainers ](./media/eshoponcontainers-helm-folder.png)
 **2-6**. Složka Helm eShopOnContainers

Jednotlivé komponenty se instalují pomocí `helm install` příkazu. eShop obsahuje skript "nasadit vše", který projde a nainstaluje komponenty pomocí příslušných Helm grafů. Výsledkem je opakovaný proces, ve kterém je verze aplikace ve správě zdrojového kódu, kterou může kdokoli v týmu nasadit do clusteru AKS s jedním řádkovým příkazem skriptu.

> Všimněte si, že verze 3 nástroje Helm oficiálně odstraňuje nutnost serverové komponenty pro pokladnu. Další informace o tomto vylepšení najdete [tady](https://medium.com/better-programming/why-is-tiller-missing-in-helm-3-2347c446714).

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Nativní aplikace pro Cloud můžou rychle rozšiřovat rozsáhlé a komplexní a vyžadují, aby se mohly spustit významné výpočetní prostředky. V těchto scénářích nemůže být celá aplikace hostována na vývojovém počítači (zejména notebook). Azure Dev Spaces je navržený pro řešení tohoto problému pomocí AKS. Umožňuje vývojářům pracovat s místní verzí svých služeb a současně hostovat zbytek aplikace v AKS vývojovém clusteru.

Vývojáři sdílejí běžící (vývojovou) instanci v clusteru AKS, který obsahuje celou kontejnerovou aplikaci. Ale používají osobní prostory nastavené na svém počítači k místnímu vývoji svých služeb. Po dokončení se otestuje z konce na konec v clusteru AKS – bez závislostí replikace. Azure Dev Spaces sloučí kód z místního počítače se službami v AKS. Členové týmu mohou vidět, jak se změny budou chovat ve skutečném prostředí AKS. Vývojáři můžou rychle iterovat a ladit kód přímo v Kubernetes pomocí sady Visual Studio 2017 nebo Visual Studio Code.

Na obrázku 2-7 vidíte, že vývojář Susie nasadil aktualizovanou verzi mikroslužby bicyklů do svého vývojového prostoru. Potom je možné otestovat své změny pomocí vlastní adresy URL začínající názvem jejího místa (susie.s.dev.myapp.eus.azds.io).

![Obrázek architektury eShopOnContainers ](./media/azure-devspaces-one.png)
 **2-7**. Vývojář Susie nasadí svoji vlastní verzi mikroslužby bicyklů a otestuje ji.

V současné době vývojář Jan přizpůsobuje mikroslužbu rezervací a potřebuje testovat své změny. Nasadí své změny do vlastního prostoru pro vývoj bez konfliktu se změnami Susie, jak je znázorněno na obrázku 2-8. Jan potom testuje změny pomocí vlastní adresy URL, která má předponu s názvem svého místa (john.s.dev.myapp.eus.azds.io).

![Obrázek architektury eShopOnContainers ](./media/azure-devspaces-two.png)
 **2-8**. Vývojář Jan nasadí svoji vlastní verzi mikroslužby rezervací a otestuje ji bez konfliktu s ostatními vývojáři.

Pomocí Azure Dev Spaces můžou týmy pracovat přímo se AKS a přitom nezávisle měnit, nasazovat a testovat jejich změny. Tento přístup omezuje nutnost samostatných vyhrazených hostovaných prostředí, protože každý vývojář efektivně má své vlastní prostředí AKS. Vývojáři mohou pracovat s Azure Dev Spaces pomocí svého rozhraní příkazového řádku nebo spustit aplikaci pro Azure Dev Spaces přímo ze sady Visual Studio. [Přečtěte si další informace o tom, jak Azure Dev Spaces fungují a jsou nakonfigurované.](https://docs.microsoft.com/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Functions a Logic Apps (bez serveru)

Ukázka eShopOnContainers zahrnuje podporu pro sledování online marketingových kampaní. Funkce Azure se používá ke sledování podrobností marketingové kampaně pro dané ID kampaně. Místo vytváření úplné mikroslužeb je jedna funkce Azure jednodušší a dostatečná. Azure Functions mají jednoduchý model sestavení a nasazení, zejména v případě, že je nakonfigurován tak, aby běžel v Kubernetes. Nasazení funkce se skriptuje pomocí šablon Azure Resource Manager (ARM) a rozhraní příkazového řádku Azure CLI. Tato služba kampaně není zaměřená na zákazníka a vyvolává jednu operaci, což je skvělým kandidátem na Azure Functions. Tato funkce vyžaduje minimální konfiguraci, včetně dat připojovacího řetězce databáze a nastavení Image základního identifikátoru URI. Azure Functions můžete nakonfigurovat v Azure Portal.

>[!div class="step-by-step"]
>[Předchozí](map-eshoponcontainers-azure-services.md) 
> [Další](centralized-configuration.md)
