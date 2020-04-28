---
title: Kombinování kontejnerů a přístupů bez serveru pro cloudové nativní služby
description: Kombinování kontejnerů a Kubernetes s přístupy bez serveru
ms.date: 04/23/2020
ms.openlocfilehash: fe9e9fd5d07132971d64bc6433a762fb7bd22048
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199661"
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

Služba Azure Functions se automaticky škáluje tak, aby splňovala požadavky na základě frekvence událostí, které cílí na ni. Můžete vždycky využít AKS k hostování vašich funkcí a používat automatické škálování založené na událostech založených na Kubernetes nebo KEDA. Když se nevyskytnou žádné události, KEDA může škálovat dolů na nulové instance. [Přečtěte si další informace o škálování Azure Functions pomocí keda](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).

>[!div class="step-by-step"]
>[Předchozí](leverage-serverless-functions.md)
>[Další](deploy-containers-azure.md)
