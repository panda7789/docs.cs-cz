---
title: Kombinování kontejnerů a bezserverových přístupů
description: Kombinování kontejnerů a Kubernetes s přístupy bez serveru
ms.date: 06/30/2019
ms.openlocfilehash: 58aff43adbdd2e629370cc685f32c7b61c25f85e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183432"
---
# <a name="combining-containers-and-serverless-approaches"></a>Kombinování kontejnerů a bezserverových přístupů

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikace založené na mikroslužbách se často spoléhají na kontejnery, orchestraci a předávání zpráv mezi uzly. Toto zasílání zpráv je ideálním úkolem pro Azure Functions, ale s ostatními aplikacemi nakonfigurovanými a nasazenými pomocí Kubernetes a souvisejících nástrojů by bylo skvělé, že by bylo možné využít Azure Functions v rámci této stejné sady nástrojů. Naštěstí můžete zalamovat Azure Functions v kontejnerech Docker a nasazovat je pomocí stejných procesů a nástrojů jako zbytek aplikace založené na Kubernetes.

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>Kdy je vhodné používat kontejnery s bez serveru?

Ve výchozím nastavení nemají vaše funkce bez serveru žádné znalosti o platformě, na které se budou spouštět. V některých případech však můžete mít specifické požadavky, které je důležité pro přizpůsobení image kontejneru, ve které se váš kód spustí. Můžete chtít použít vlastní image, protože vaše funkce závisí na konkrétní jazykové verzi nebo obsahuje závislosti nebo požadavky na konfiguraci, které nejsou podporovány výchozím imagí. V těchto případech může být vhodné přizpůsobit vlastní kontejner a nasadit funkci do vlastního kontejneru Docker.

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>Kdy byste se měli vyhnout použití kontejnerů s Azure Functions?

Pokud očekáváte, že se vám budou účtovat výhody plánu spotřeby pro vaši funkci, nebudete je moct dělat, pokud používáte vlastní kontejner. A co víc, pokud překročíte jenom pomocí kontejneru Docker a nasadíte své funkce do vlastního clusteru Kubernetes, už nebudete mít k dispozici integrované škálování, které poskytuje Azure Functions. Budete muset použít funkce škálování Kubernetes popsané níže.

## <a name="how-to-combine-serverless-and-docker-containers"></a>Jak kombinovat kontejnery bez serveru a Docker

Pokud chcete zabalit funkci Azure do kontejneru Docker, nainstalujte Azure Functions Core Tools a pak spusťte následující příkaz:

```console
func init ProjectName --docker
```

Vyberte, který modul runtime pracovního procesu chcete, z následujících možností:

- `dotnet` (C#)
- `node` (JavaScript)
- `python`

Když je projekt vytvořen, bude obsahovat souboru Dockerfile. Nyní můžete funkci vytvořit a otestovat místně. Sestavte a spusťte pomocí příkazů `docker build` a `docker run`. Podrobný postup, jak začít sestavovat Azure Functions s podporou Docker, najdete v kurzu [Vytvoření funkce na platformě Linux s využitím vlastního obrázku](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) .

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>Jak kombinovat bez serveru a Kubernetes pomocí KEDA

Služba Azure Functions se automaticky škáluje tak, aby splňovala požadavky na základě frekvence událostí, které cílí na danou funkci. Navíc můžete využít Kubernetes k hostování vašich funkcí a používat automatické škálování založené na událostech založených na Kubernetes nebo KEDA. Když se nevyskytnou žádné události, KEDA může škálovat až na 0 instancí a pak v reakci na události může škálovat počet kontejnerů tak, aby splnily požadavky pomocí vodorovného automatického škálování pod. [Přečtěte si další informace o škálování Azure Functions pomocí keda](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).

## <a name="references"></a>Reference

- [Spuštění Azure Functions v kontejneru Docker](https://markheath.net/post/azure-functions-docker)
- [Vytvoření funkce na platformě Linux pomocí vlastní image](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [Azure Functions pomocí automatického škálování založeného na událostech Kubernetes](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)

>[!div class="step-by-step"]
>[Předchozí](leverage-serverless-functions.md)
>[Další](deploy-containers-azure.md)
