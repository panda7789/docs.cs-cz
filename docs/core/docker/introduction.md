---
title: Úvod do Docker
description: Tento článek poskytuje úvodní informace a přehled pro Docker v kontextu aplikace .NET Core.
ms.date: 03/20/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: 7f19b12d84543e8ae69c2f8728872bf94ef0536f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73416646"
---
# <a name="introduction-to-net-and-docker"></a>Úvod k .NET a Dockeru

.NET Core se dá snadno spustit v kontejneru Docker. Kontejnery poskytují odlehčený způsob izolace vaší aplikace ze zbytku hostitelského systému, sdílení pouze jádra a používání prostředků, které jsou dané aplikaci k dispozici. Pokud Docker neznáte, důrazně doporučujeme, abyste si přečetli [dokumentaci k přehledům](https://docs.docker.com/engine/docker-overview/)Docker.

Další informace o tom, jak nainstalovat Docker, najdete na stránce pro stažení [Docker desktopu: Community Edition](https://www.docker.com/products/docker-desktop).

## <a name="docker-basics"></a>Základy Docker

Existuje několik konceptů, které byste měli znát. Klient Docker má program rozhraní příkazového řádku, který používáte ke správě imagí a kontejnerů. Jak už bylo uvedeno výše, měli byste si projít čas, abyste si přečetli dokumentaci k dokumentaci s [přehledem Docker](https://docs.docker.com/engine/docker-overview/) . 

### <a name="images"></a>Obrázky

Obrázek je uspořádaná kolekce změn systému souborů, které tvoří základ kontejneru. Obrázek nemá stav a je určen jen pro čtení. Mnohem tím, kdy je obrázek založen na jiné imagi, ale s některým přizpůsobením. Například při vytváření nové image pro aplikaci byste ji měli založit na stávající imagi, která již obsahuje modul runtime .NET Core.

Vzhledem k tomu, že kontejnery jsou vytvořeny z imagí, mají image sadu parametrů spuštění (například spuštění spustitelného souboru), který se spouští při spuštění kontejneru.

### <a name="containers"></a>Kontejnery

Kontejner je instance spustitelný obrázku. Při sestavování image nasadíte svoji aplikaci a závislosti. Potom lze vytvořit instanci více kontejnerů, z nichž každá je izolována od sebe. Každá instance kontejneru má vlastní systém souborů, paměť a síťové rozhraní.

### <a name="registries"></a>Registr

Registry kontejnerů jsou kolekcí úložišť imagí. Obrázky můžete založit na imagi registru. Kontejnery můžete vytvořit přímo z image v registru. [Vztah mezi kontejnery Docker, obrázky a Registry](../../architecture/microservices/container-docker-introduction/docker-containers-images-registries.md) je důležitý koncept při [navrhování a sestavování kontejnerových aplikací nebo mikroslužeb](../../architecture/microservices/architect-microservice-container-applications/index.md). Tento přístup značně zkracuje dobu mezi vývojem a nasazením.

Docker má veřejný registr hostovaný v [Docker Hub](https://hub.docker.com/) , který můžete použít. [Image související s .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) jsou uvedené v Docker Hub. 

Microsoft Container Registry (MCR) je oficiálním zdrojem imagí kontejnerů poskytovaných společností Microsoft. MCR je postaven na Azure CDN k poskytování globálně replikovaných imagí. MCR ale nemá veřejný web a primární způsob, jak získat informace o imagí kontejnerů poskytovaných Microsoftem, je prostřednictvím [stránek Microsoft Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).

### <a name="dockerfile"></a>Souboru Dockerfile

**Souboru Dockerfile** je soubor, který definuje sadu instrukcí, které vytvoří obrázek. Každá instrukce v **souboru Dockerfile** vytvoří vrstvu v obrázku. Ve většině případů se při opětovném sestavování image znovu sestaví jenom vrstvy, které se změnily. **Souboru Dockerfile** je možné distribuovat jiným uživatelům a umožnit jim opětovné vytvoření nového obrázku stejným způsobem, jako jste ho vytvořili. I když vám to umožňuje distribuovat *pokyny* k vytvoření image, hlavní způsob, jak distribuovat image, je publikovat je do registru.

## <a name="net-core-images"></a>Image .NET Core

Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít. 

Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře. Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.

## <a name="azure-services"></a>Služby Azure

Různé kontejnery podpory služeb Azure. Vytvoříte image Docker pro aplikaci a nasadíte ji na jednu z následujících služeb:

- [Služba Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/) \
Škálujte a orchestrujte kontejnery Linux pomocí Kubernetes.

- [Azure App Service](https://azure.microsoft.com/services/app-service/containers/) \
Nasaďte webové aplikace nebo rozhraní API s využitím kontejnerů Linux v prostředí PaaS.

- [Azure Container Instances](https://azure.microsoft.com/services/container-instances/) \
Hostujte svůj kontejner v cloudu bez jakýchkoli služeb pro správu vyšší úrovně.

 [Azure Batch](https://azure.microsoft.com/services/batch/) \
Spusťte opakované výpočetní úlohy s využitím kontejnerů.

- \ [Service Fabric Azure](https://azure.microsoft.com/services/service-fabric/)
Namodernizovat aplikace .NET do mikroslužeb pomocí kontejnerů Windows serveru.

- [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) \
Ukládání a Správa imagí kontejnerů napříč všemi typy nasazení Azure

## <a name="next-steps"></a>Další kroky

- [Přečtěte si, jak kontejnerizace aplikaci .NET Core.](build-container.md)
- [Naučte se, jak kontejnerizace aplikaci ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Vyzkoušejte si kurz ASP.NET Core mikroslužeb.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Další informace o nástrojích kontejnerů v aplikaci Visual Studio](/visualstudio/containers/overview)
