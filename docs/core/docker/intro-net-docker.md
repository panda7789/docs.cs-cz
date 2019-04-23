---
title: Seznámení s Dockerem
description: Tento článek obsahuje přehled a úvod do Docker v kontextu aplikace .NET Core.
ms.date: 03/20/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: acf1307c241d9462278bc0fce5cf59fdde0750a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480726"
---
# <a name="introduction-to-net-and-docker"></a>Úvod k .NET a Dockeru

.NET core můžete snadno spouštět v kontejneru Dockeru. Kontejnery poskytují jednoduchý způsob, jak izolace aplikace od zbytku systému hostitele, sdílet jenom jádra a používat prostředky zadané pro vaši aplikaci. Pokud nejste obeznámeni s Dockerem, důrazně doporučujeme, abyste si přečetli prostřednictvím Dockeru [přehled dokumentace](https://docs.docker.com/engine/docker-overview/).

Další informace o instalaci Dockeru najdete na stránce stahování pro [Docker Desktopu: Edice Community](https://www.docker.com/products/docker-desktop).

## <a name="docker-basics"></a>Základní informace o dockeru

Existuje několik konceptů, které byste měli znát. Klient Docker má program rozhraní příkazového řádku, který používáte ke správě imagí a kontejnerů. Jak už jsme uvedli, zabere čas, aby si [přehled Dockeru](https://docs.docker.com/engine/docker-overview/) dokumentaci. 

### <a name="images"></a>Obrázky

Obrázek je uspořádaná kolekce změn systému souborů, které představují základ pro kontejner. Obrázek nemá stavu a je jen pro čtení. Nejvíce času bitovou kopii je založena na jiné image, ale pomocí vlastního nastavení. Například při vytváření nové image pro vaši aplikaci, můžete by ji založit na stávající bitovou kopii, která již obsahuje modul runtime .NET Core.

Kontejnery se vytváří z Image, Image obsahují sadu parametrů běhu (například výchozí spustitelný soubor), na kterých běží při spuštění kontejneru.

### <a name="containers"></a>Kontejnery

Kontejner je spustitelné instanci bitové kopie. Během vytváření bitové kopie, nasaďte aplikaci a závislosti. Pak můžete vytvořit instanci více kontejnerů, každý izolované od sebe. Každou instanci kontejneru má svůj vlastní systém souborů, paměti a síťového rozhraní.

### <a name="registries"></a>Registry

Registry kontejnerů jsou kolekce bitové kopie úložiště. Image můžete založit na bitové kopie registru. Vytvoření kontejnerů přímo z image v registru. [Vztah mezi kontejnery Dockeru, obrázky a registry](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) je důležitý koncept při [navrhování a sestavování kontejnerizovaných aplikací nebo mikroslužeb](../../standard/microservices-architecture/architect-microservice-container-applications/index.md). Tento postup značně zkracuje dobu mezi vývojem a nasazení.

Docker má veřejného registru hostovaných [Docker Hubu](https://hub.docker.com/) , který vám pomůže. [Image související s .NET core](https://hub.docker.com/_/microsoft-dotnet-core/) jsou uvedeny v Docker Hubu. 

Microsoft Container Registry (MCR) je oficiálním zdrojem imagí kontejnerů poskytovaný společností Microsoft. MCR je postavená na Azure CDN k poskytování globálně replikovat imagí. Ale MCR nemá veřejnou webu a je primárním způsob, jak Seznamte se s imagí kontejnerů poskytovaný společností Microsoft prostřednictvím [stránky Microsoft Docker Hubu](https://hub.docker.com/_/microsoft-dotnet-core/).

### <a name="dockerfile"></a>Dockerfile

A **soubor Dockerfile** je soubor, který definuje sadu pokynů, které vytvoří bitovou kopii. Každou instrukci v **soubor Dockerfile** vytvoří vrstvu na obrázku. Ve většině případů při opětovném sestavování bitovou kopii pouze vrstvy, které se změnily se znovu sestavit. **Soubor Dockerfile** lze distribuovat ostatním uživatelům a umožňuje jim znovu vytvořit novou bitovou kopii stejným způsobem jste ho vytvořili. Přestože to umožňuje distribuovat *pokyny* na tom, jak vytvořit image, hlavní způsob pro distribuci bitové kopie je její publikování do registru.

## <a name="net-core-images"></a>.NET core imagí

Oficiální Image .NET Core Dockeru se publikují do registru Microsoft kontejneru (MCR) a organizací na se [úložišti Microsoft .NET Core, Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Každé úložiště obsahuje Image pro různé kombinace .NET (sada SDK nebo modul Runtime) a operační systém, který můžete použít. 

Společnost Microsoft poskytuje bitové kopie, které jsou přizpůsobené pro konkrétní scénáře. Například [ASP.NET Core úložiště](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje Image, které jsou vytvořeny pro spouštění aplikací ASP.NET Core v produkčním prostředí.

## <a name="azure-services"></a>Služby Azure

Různé služby Azure podporují kontejnery. Vytvoření image Dockeru pro vaši aplikaci a nasadit na jeden z následujících služeb:

* [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/)\
Škálujte a orchestrujte kontejnery Linuxu pomocí Kubernetes.

* [Azure App Service](https://azure.microsoft.com/services/app-service/containers/)\
Nasazení webové aplikace nebo API s využitím kontejnerů Linuxu v prostředí PaaS.

* [Azure Container Instances](https://azure.microsoft.com/services/container-instances/)\
Hostitel kontejneru v cloudu bez jakékoli vyšší úrovně služeb správy.

* [Služba Azure Batch](https://azure.microsoft.com/services/batch/)\
Spouštění opakujících se výpočetních úloh pomocí kontejnerů.

* [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)\
Přenést, shift a modernizace aplikací .NET do mikroslužeb pomocí kontejnerů Windows serveru

* [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)\
Store a správa imagí kontejnerů napříč všemi typy nasazení Azure.

## <a name="next-steps"></a>Další kroky

* [Zjistěte, jak kontejnerizovat aplikace .NET Core.](build-docker-netcore-container.md)
* [Projděte si kurz další Mikroslužeb ASP.NET Core.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
