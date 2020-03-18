---
title: Úvod do Dockeru
description: Tento článek poskytuje úvod a přehled Dockeru v kontextu aplikace .NET Core.
ms.date: 03/20/2019
ms.custom: mvc
ms.openlocfilehash: eedfd1e7c1b361beb9d4f271e739657ef5e894a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157788"
---
# <a name="introduction-to-net-and-docker"></a>Úvod k .NET a Dockeru

.NET Core lze snadno spustit v kontejneru Dockeru. Kontejnery poskytují lehký způsob, jak izolovat aplikaci od zbytku hostitelského systému, sdílení pouze jádra a pomocí prostředků daných do vaší aplikace. Pokud nejste obeznámeni s Dockerem, důrazně doporučujeme, abyste si [přečetli dokumentaci přehledu Dockeru](https://docs.docker.com/engine/docker-overview/).

Další informace o instalaci Dockeru najdete na stránce pro stažení [plochy v Dockeru: Community Edition](https://www.docker.com/products/docker-desktop).

## <a name="docker-basics"></a>Základy Dockeru

Existuje několik konceptů, které byste měli znát. Klient Dockeru má velnařízení o vytvoření funkce pro nastavení vkladů, které můžete použít ke správě bitových kopií a kontejnerů. Jak již bylo uvedeno, měli byste mít čas na čtení prostřednictvím dokumentace [přehled dockeru.](https://docs.docker.com/engine/docker-overview/)

### <a name="images"></a>Image

Bitová kopie je uspořádaná kolekce změn souborového systému, které tvoří základ kontejneru. Obrázek nemá stav a je jen pro čtení. Hodně času obraz je založen na jiném obrázku, ale s některými přizpůsobení. Například při vytváření nové bitové kopie pro vaši aplikaci, by ji založit na existující bitovou kopii, která již obsahuje .NET Core runtime.

Vzhledem k tomu, že kontejnery jsou vytvořeny z bitových kopií, bitové kopie mají sadu parametrů spuštění (například spuštění spustitelný soubor), které běží při spuštění kontejneru.

### <a name="containers"></a>Kontejnery

Kontejner je spustitelná instance bitové kopie. Při vytváření image nasadíte aplikaci a závislosti. Potom může být vytvořena instance více kontejnerů, z nichž každý je od sebe izolován. Každá instance kontejneru má svůj vlastní souborový systém, paměť a síťové rozhraní.

### <a name="registries"></a>Registry

Kontejnerové registry jsou kolekce úložišť obrázků. Obrázky můžete založit na bitové kopii registru. Kontejnery můžete vytvořit přímo z bitové kopie v registru. [Vztah mezi kontejnery Dockeru, image a registry](../../architecture/microservices/container-docker-introduction/docker-containers-images-registries.md) je důležitý koncept při navrhování a vytváření [kontejnerizovaných aplikací nebo mikroslužeb](../../architecture/microservices/architect-microservice-container-applications/index.md). Tento přístup výrazně zkracuje dobu mezi vývojem a nasazením.

Docker má veřejný registr hostovaný v [Docker Hubu,](https://hub.docker.com/) který můžete použít. [Bitové kopie související s jádrem .NET](https://hub.docker.com/_/microsoft-dotnet-core/) jsou uvedeny v centru Docker.

Microsoft Container Registry (MCR) je oficiálním zdrojem image kontejneru poskytovaného společností Microsoft. MCR je postaven na Azure CDN poskytovat globálně replikované image. MCR však nemá veřejný web a primární způsob, jak získat informace o iimages kontejnerů poskytovaných společností Microsoft, je prostřednictvím [stránek Microsoft Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).

### <a name="dockerfile"></a>Soubor dockeru

**Dockerfile** je soubor, který definuje sadu instrukcí, které vytvoří bitovou kopii. Každá instrukce v **Dockerfile** vytvoří vrstvu v obraze. Z větší části se při opětovném sestavení obrazu znovu vytvoří pouze vrstvy, které se změnily. **Dockerfile** lze distribuovat ostatním a umožňuje jim znovu vytvořit novou bitovou kopii stejným způsobem, jakým jste jej vytvořili. I když to umožňuje distribuovat *pokyny,* jak vytvořit obrázek, hlavní způsob, jak distribuovat obrázek je publikovat do registru.

## <a name="net-core-images"></a>Bitové kopie .NET Core

Oficiální image .NET Core Docker umožnou v registru Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Každé úložiště obsahuje obrázky pro různé kombinace .NET (SDK nebo Runtime) a Operačního serveru, které můžete použít.

Společnost Microsoft poskytuje obrázky, které jsou přizpůsobeny pro konkrétní scénáře. [Například úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje image, které jsou vytvořené pro spouštění aplikací ASP.NET Core v produkčním prostředí.

## <a name="azure-services"></a>Služby Azure

Různé služby Azure podporují kontejnery. Vytvoříte image Dockeru pro vaši aplikaci a nasadíte ji do jedné z následujících služeb:

- [Služba Azure Kubernetes (AKS)](https://azure.microsoft.com/services/kubernetes-service/)\
Škálování a orchestrace linuxových kontejnerů pomocí Kubernetes.

- [Azure App Service](https://azure.microsoft.com/services/app-service/containers/)\
Nasazujte webové aplikace nebo api pomocí linuxových kontejnerů v prostředí PaaS.

- [Instance kontejnerů Azure](https://azure.microsoft.com/services/container-instances/)\
Hostujte svůj kontejner v cloudu bez jakýchkoli služeb pro správu vyšší úrovně.

- [Azure Batch](https://azure.microsoft.com/services/batch/)\
Spouštějte opakující se výpočetní úlohy pomocí kontejnerů.

- [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)\
Výtah, shift a modernizovat aplikace .NET mikroslužeb pomocí kontejnerů Windows Server.

- [Registr kontejnerů Azure](https://azure.microsoft.com/services/container-registry/)\
Uklápěte a spravujte ibi kontejnerů napříč všemi typy nasazení Azure.

## <a name="next-steps"></a>Další kroky

- [Přečtěte si, jak kontejnerizovat aplikaci .NET Core.](build-container.md)
- [Přečtěte si, jak kontejnerizovat aplikaci ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Vyzkoušejte kurz Learn ASP.NET Core Microservice.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Informace o nástrojích kontejnerů v sadě Visual Studio](/visualstudio/containers/overview)
