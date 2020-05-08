---
title: Kombinování kontejnerů a přístupů bez serveru pro cloudové nativní služby
description: Kombinování kontejnerů a Kubernetes s přístupy bez serveru
ms.date: 04/23/2020
ms.openlocfilehash: a6ae17543c9075ca84126a4c19f9f51887f7fe9a
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895637"
---
# <a name="combining-containers-and-serverless-approaches"></a>Kombinování kontejnerů a bezserverových přístupů

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Nativní aplikace pro Cloud obvykle implementují služby, které využívají kontejnery a orchestraci. K dispozici jsou často příležitosti k vystavování některých služeb aplikace jako Azure Functions. V případě nativní aplikace v cloudu nasazené do Kubernetes by ale bylo skvělé využít Azure Functions v rámci této stejné sady nástrojů. Naštěstí můžete zalamovat Azure Functions uvnitř kontejnerů Docker a nasazovat je pomocí stejných procesů a nástrojů jako zbytek aplikace založené na Kubernetes.

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>Kdy je vhodné používat kontejnery s bez serveru?

Vaše funkce Azure nemá žádné znalosti o platformě, na které je nasazená. V některých scénářích můžete mít specifické požadavky a potřebujete přizpůsobit prostředí, na kterém se váš kód funkce spustí. Budete potřebovat vlastní image, která podporuje závislosti nebo konfiguraci, která není podporovaná výchozím imagí. V těchto případech má smysl nasadit funkci ve vlastním kontejneru Docker.

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>Kdy byste se měli vyhnout použití kontejnerů s Azure Functions?

Pokud chcete použít účtování spotřeby, nebudete moci spustit funkci v kontejneru. I když nasadíte funkci do clusteru Kubernetes, už nebudete mít k dispozici integrované škálování, které poskytuje Azure Functions. Budete muset použít funkce škálování Kubernetes popsané dříve v této kapitole.

## <a name="how-to-combine-serverless-and-docker-containers"></a>Jak kombinovat kontejnery bez serveru a Docker

Pokud chcete zabalit funkci Azure do kontejneru Docker, nainstalujte [Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) a pak spusťte následující příkaz:

```console
func init ProjectName --worker-runtime dotnet --docker
```

Když je projekt vytvořen, bude obsahovat souboru Dockerfile a modul runtime Worker nakonfigurovaný na `dotnet`. Nyní můžete funkci vytvořit a otestovat místně. Sestavte a spusťte pomocí `docker build` příkazů `docker run` a. Podrobný postup, jak začít sestavovat Azure Functions s podporou Docker, najdete v kurzu [Vytvoření funkce na platformě Linux s využitím vlastního obrázku](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) .

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>Jak kombinovat bez serveru a Kubernetes pomocí KEDA

V této kapitole jste viděli, že Azure Functions platforma se automaticky škáluje tak, aby splňovala požadavky. Při nasazování kontejnerových funkcí do AKS se však ztratí vestavěná funkce škálování. Do záchranného rozhraní patří [Kubernetes řízená událost (keda)](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda). Umožňuje jemně odstupňované automatické škálování pro `event-driven Kubernetes workloads,` zahrnutí funkcí s funkcí Container.

KEDA poskytuje funkce škálování řízené událostmi do modulu runtime Functions v kontejneru Docker. KEDA se může škálovat z nulových instancí (Pokud k žádné události nedochází) na `n instances`základě zatížení. Umožňuje automatické škálování tím, že vystavuje vlastní metriky na Kubernetes AutoScale (vodorovně pod automatickým nástrojem pro horizontální navýšení). Pomocí kontejnerů Functions s KEDA je možné replikovat funkce bez serveru v jakémkoli clusteru Kubernetes.

Je potřeba poznamenat, že projekt KEDA je teď spravovaný službou Cloud Native Computing Foundation (CNCF).

>[!div class="step-by-step"]
>[Předchozí](leverage-serverless-functions.md)
>[Další](deploy-containers-azure.md)
