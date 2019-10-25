---
title: Docker – gRPC pro vývojáře WCF
description: Vytváření imagí Docker pro aplikace ASP.NET Core gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: cc369da9494ade532187dfc8d19a94a3a037ebab
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846676"
---
# <a name="docker"></a>Docker

Tato část se zabývá vytvářením imagí Docker pro aplikace ASP.NET Core gRPC, které jsou připravené ke spuštění v Docker, Kubernetes nebo v jiných kontejnerových prostředích. Použitá ukázková aplikace s ASP.NET Core webovou aplikací MVC a službou gRPC je k dispozici v úložišti [dotnet-Architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) na GitHubu.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Základní image Microsoft pro aplikace ASP.NET Core

Microsoft poskytuje řadu základních imagí pro sestavování a spouštění aplikací .NET Core. Chcete-li vytvořit bitovou kopii ASP.NET Core 3,0, jsou použity dvě základní bitové kopie: image sady SDK pro sestavení a publikování aplikace a bitovou kopii modulu runtime pro nasazení.

| Image | Popis |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | Pro sestavování aplikací pomocí `docker build`. Nedá se použít v produkčním prostředí. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Obsahuje závislosti modulu runtime a ASP.NET Core. Pro produkční prostředí. |

Pro každý obrázek jsou k dispozici čtyři varianty založené na různých distribucích systému Linux, které jsou odlišeny pomocí značek.

| Značky obrázku | Linux | Poznámky |
| --------- | ----- | ----- |
| 3,0 – Buster, 3,0 | Debian 10 | Výchozí obrázek, pokud není zadána varianta operačního systému. |
| 3,0 – Alpine | Alpine 3,9 | Obrázky Alpine Base jsou mnohem menší než Debian nebo Ubuntu. |
| 3,0 – disco | Ubuntu 19,04 | |
| 3,0 – Bionic | Ubuntu 18,04 | |

Základní image Alpine je okolo 100 MB, v porovnání s 200 MB pro Image Debian a Ubuntu, ale některé softwarové balíčky nebo knihovny nemusí být k dispozici ve správě balíčků Alpine. Pokud si nejste jistí, která image se má použít, je nejlepší vytvořit výchozí Debian, pokud nemáte přesvědčivou potřebu použít jiný distribuce.

> [!IMPORTANT]
> Ujistěte se, že používáte stejnou variantu systému Linux pro sestavení a modul runtime. Aplikace sestavené a publikované na jednom variantě nemusí fungovat na jiném.

## <a name="create-a-docker-image"></a>Vytvoření image Docker

Image Docker je definovaná pomocí *souboru Dockerfile*, což je textový soubor, který obsahuje všechny příkazy potřebné k sestavení aplikace a instalaci všech závislostí, které jsou potřebné pro vytvoření nebo spuštění aplikace. Následující příklad ukazuje nejjednodušší souboru Dockerfile pro aplikaci ASP.NET Core 3,0:

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/core/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

Souboru Dockerfile má dvě části: první používá základní image `sdk` k sestavení a publikování aplikace. Druhá vytvoří bitovou kopii modulu runtime ze základu `aspnet`. Důvodem je to, že bitová kopie `sdk` přibližně 900 MB v porovnání s přibližně 200 MB pro bitovou kopii modulu runtime a většina jejího obsahu není po dobu běhu potřebná.

### <a name="the-build-steps"></a>Kroky sestavení

| Krok | Popis |
| ---- | ----------- |
| `FROM ...` | Deklaruje základní obrázek a přiřadí alias `builder` (vysvětlení naleznete v další části.) |
| `WORKDIR /src` | Vytvoří adresář `/src` a nastaví ho jako aktuální pracovní adresář. |
| `COPY . .` | Zkopíruje vše pod aktuálním adresářem v hostiteli do aktuálního adresáře v imagi. |
| `RUN dotnet restore` | Obnoví všechny externí balíčky (ASP.NET Core 3,0 Framework je předem nainstalovaná s SDK). |
| `RUN dotnet publish ...` | Vytvoří a publikuje sestavení pro vydání. Všimněte si, že příznak `--runtime` není povinný. |

### <a name="the-runtime-image-steps"></a>Kroky bitové kopie modulu runtime

| Krok | Popis |
| ---- | ----------- |
| `FROM ...` | Deklaruje novou základní image. |
| `WORKDIR /app` | Vytvoří adresář `/app` a nastaví ho jako aktuální pracovní adresář. |
| `COPY --from=builder ...` | Zkopíruje publikovanou aplikaci z předchozího obrázku pomocí aliasu `builder` z prvního `FROM` řádku. |
| `ENTRYPOINT [ ... ]` | Nastaví příkaz, který se spustí při spuštění kontejneru. Příkaz `dotnet` v imagi modulu runtime může spouštět pouze soubory DLL. |

### <a name="https-in-docker"></a>HTTPS v Docker

Základní image Microsoftu pro Docker nastaví proměnnou prostředí `ASPNETCORE_URLS` na `http://+:80`, což znamená, že Kestrel na tomto portu bude běžet bez protokolu HTTPS. Pokud používáte protokol HTTPS s vlastním certifikátem (jak je popsáno v [předchozí části](self-hosted.md)), měli byste ho přepsat nastavením proměnné prostředí **v části Vytvoření bitové kopie modulu runtime v rámci** vašeho souboru dockerfileu.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>Soubor. dockerignore

Podobně jako `.gitignore` soubory, které vyloučí určité soubory a adresáře ze správy zdrojového kódu, lze `.dockerignore` soubor použít k vyloučení souborů a adresářů, které se zkopírují do bitové kopie během sestavení. To nejenom šetří čas kopírováním, ale může se taky vyhnout některým nematoucím chybám, které vznikají od sebe (zejména) `obj` Directory z počítače zkopírovaného do image. Měli byste přidat alespoň položky pro `bin` a `obj` do souboru `.dockerignore`.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Sestavení image

Pro řešení s jednou aplikací, a proto jediným souboru Dockerfile, je nejjednodušší umístit souboru Dockerfile do základního adresáře. To znamená, že se jedná o stejný adresář jako soubor `.sln`. V takovém případě pro sestavení image použijte následující příkaz `docker build` z adresáře obsahujícího rozhraní souboru Dockerfile.

```console
docker build --tag stockdata .
```

Nematoucí název `--tag` příznakem (který může být zkrácen na `-t`) určuje celý název obrázku, *včetně* skutečné značky, je-li tento parametr zadán. `.` na konci určuje *kontext* , ve kterém se bude sestavení spouštět; aktuální pracovní adresář pro příkazy `COPY` v souboru Dockerfile.

Máte-li v rámci jednoho řešení více aplikací, můžete souboru Dockerfile pro každou aplikaci ve vlastní složce vedle `.csproj` souboru, ale přesto byste měli spustit příkaz `docker build` ze základního adresáře, aby bylo zajištěno, že řešení a všechny projekty jsou zkopírovány do obrázku. Pomocí příznaku `--file` (nebo `-f`) můžete zadat souboru Dockerfile pod aktuálním adresářem.

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Spuštění image v kontejneru na počítači

Pokud chcete spustit image v místní instanci Docker, použijte příkaz `docker run`.

```console
docker run -ti -p 5000:80 stockdata
```

Příznak `-ti` připojí aktuální terminál k terminálu kontejneru a spustí se v interaktivním režimu. `-p 5000:80` zveřejňuje (odkazy) port 80 na kontejneru na port 80 na síťovém rozhraní localhost.

## <a name="push-the-image-to-a-registry"></a>Vložení image do registru

Jakmile ověříte, že bitová kopie funguje, budete ji muset odeslat do registru Docker, aby byla k dispozici v jiných systémech. Interní sítě budou muset zřídit registr Docker. To může být jednoduché jako [`registry` image s vlastním prostředím Docker](https://docs.docker.com/registry/deploying/) (to je správné, registr Docker běží v kontejneru Docker), ale k dispozici jsou různá komplexnější řešení. Pro externí sdílení a cloudové použití jsou k dispozici různé spravované Registry, například [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) nebo [Docker Hub](https://docs.docker.com/docker-hub/repos/).

Pokud chcete přejít do dokovacího centra, pojmenujte název image názvem uživatele nebo organizace.

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

Pokud chcete přejít do privátního registru, použijte předponu názvu bitové kopie s názvem hostitele registru a názvem organizace.

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

Jakmile je obrázek v registru, můžete ho nasadit na jednotlivé hostitele Docker nebo na modul pro orchestraci kontejnerů, jako je Kubernetes.

>[!div class="step-by-step"]
>[Předchozí](self-hosted.md)
>[Další](kubernetes.md)
