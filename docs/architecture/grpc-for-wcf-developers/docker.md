---
title: Docker – gRPC pro vývojáře WCF
description: Vytváření imagí Docker pro aplikace ASP.NET Core gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6e9d4956077286d133d09ab8e681ba5e82ab1aa4
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184475"
---
# <a name="docker"></a>Docker

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Tato část se zabývá vytvářením imagí Docker pro aplikace ASP.NET Core gRPC, které jsou připravené ke spuštění v Docker, Kubernetes nebo v jiných kontejnerových prostředích. Použitá ukázková aplikace s ASP.NET Core webovou aplikací MVC a službou gRPC je k dispozici v úložišti [RendleLabs/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) na GitHubu.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Základní image Microsoft pro aplikace ASP.NET Core

Microsoft poskytuje řadu základních imagí pro sestavování a spouštění aplikací .NET Core. Chcete-li vytvořit bitovou kopii ASP.NET Core 3,0, jsou použity dvě základní bitové kopie: image sady SDK pro sestavení a publikování aplikace a bitovou kopii modulu runtime pro nasazení.

| Image | Popis |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | Pro sestavování `docker build`aplikací pomocí. Nedá se použít v produkčním prostředí. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Obsahuje závislosti modulu runtime a ASP.NET Core. Pro produkční prostředí. |

Pro každý obrázek jsou k dispozici čtyři varianty založené na různých distribucích systému Linux, které jsou odlišeny pomocí značek.

| Značky obrázku | Linux | Poznámky |
| --------- | ----- | ----- |
| 3,0 – Buster, 3,0 | Debian 10 | Výchozí obrázek, pokud není zadána varianta operačního systému. |
| 3,0 – Alpine | Alpine 3,9 | Obrázky Alpine Base jsou mnohem menší než Debian nebo Ubuntu. |
| 3,0 – disco | Ubuntu 19,04 | |
| 3,0 – Bionic | Ubuntu 18.04 | |

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

Souboru Dockerfile má dvě části: první používá `sdk` základní image k sestavení a publikování aplikace. druhý vytvoří bitovou kopii modulu runtime `aspnet` ze základní třídy. Důvodem je `sdk` to, že bitová kopie je přibližně 900 MB v porovnání s přibližně 200 MB pro bitovou kopii modulu runtime a většina jejího obsahu je za běhu nepotřebná.

### <a name="the-build-steps"></a>Kroky sestavení

| Krok | Popis |
| ---- | ----------- |
| `FROM ...` | Deklaruje základní obrázek a přiřadí `builder` alias (viz další oddíl vysvětlení). |
| `WORKDIR /src` | `/src` Vytvoří adresář a nastaví ho jako aktuální pracovní adresář. |
| `COPY . .` | Zkopíruje vše pod aktuálním adresářem v hostiteli do aktuálního adresáře v imagi. |
| `RUN dotnet restore` | Obnoví všechny externí balíčky (ASP.NET Core 3,0 Framework je předem nainstalovaná s SDK). |
| `RUN dotnet publish ...` | Vytvoří a publikuje sestavení pro vydání. Všimněte si, `--runtime` že příznak není povinný. |

### <a name="the-runtime-image-steps"></a>Kroky bitové kopie modulu runtime

| Krok | Popis |
| ---- | ----------- |
| `FROM ...` | Deklaruje novou základní image. |
| `WORKDIR /app` | `/app` Vytvoří adresář a nastaví ho jako aktuální pracovní adresář. |
| `COPY --from=builder ...` | Zkopíruje publikovanou aplikaci z předchozího obrázku pomocí `builder` aliasu z prvního `FROM` řádku. |
| `ENTRYPOINT [ ... ]` | Nastaví příkaz, který se spustí při spuštění kontejneru. `dotnet` Příkaz v běhové imagi může spouštět pouze soubory DLL. |

### <a name="https-in-docker"></a>HTTPS v Docker

Základní image Microsoftu pro Docker nastaví `ASPNETCORE_URLS` proměnnou prostředí na `http://+:80`, což znamená, že Kestrel se na tomto portu spustí bez protokolu HTTPS. Pokud používáte protokol HTTPS s vlastním certifikátem (jak je popsáno v [předchozí části](self-hosted.md)), měli byste ho přepsat nastavením proměnné prostředí **v části Vytvoření bitové kopie modulu runtime v rámci** vašeho souboru dockerfileu.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>Soubor. dockerignore

Podobně jako `.gitignore` soubory, které vyloučí určité soubory a adresáře ze správy zdrojového `.dockerignore` kódu, lze soubor použít k vyloučení souborů a adresářů, které se zkopírují do bitové kopie během sestavení. Tím se nejen ukládá pouze kopírování času, ale může se taky vyhnout některým nematoucím chybám, které vzniknou `obj` (zejména) adresářem z počítače zkopírovaného do image. Měli byste přidat alespoň položky pro `bin` a `obj` do `.dockerignore` souboru.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Sestavení image

Pro řešení s jednou aplikací, a proto jediným souboru Dockerfile, je nejjednodušší umístit souboru Dockerfile do základního adresáře. To znamená, že se jedná o stejný `.sln` adresář jako soubor. V takovém případě pro sestavení image použijte následující `docker build` příkaz z adresáře obsahujícího souboru Dockerfile.

```console
docker build --tag stockdata .
```

Nematoucí pojmenovaný `--tag` příznak (který může být zkrácen na `-t`) určuje celý název obrázku, *včetně* skutečné značky, je-li tento parametr zadán. Na konci určuje *kontext* , ve kterém se bude sestavení spouštět; aktuální `COPY` pracovní adresář pro příkazy v souboru Dockerfile. `.`

Pokud máte více aplikací v rámci jednoho řešení, můžete souboru Dockerfile pro každou aplikaci ve vlastní složce vedle `.csproj` souboru, ale přesto byste měli `docker build` spustit příkaz ze základního adresáře, aby bylo zajištěno, že řešení a všechny projekty jsou zkopírovány do obrázku. Pomocí `--file` příznaku (nebo `-f`) můžete zadat souboru Dockerfile pod aktuálním adresářem.

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Spuštění image v kontejneru na počítači

Pokud chcete spustit image v místní instanci Docker, použijte `docker run` příkaz.

```console
docker run -ti -p 5000:80 stockdata
```

`-ti` Příznak připojuje váš aktuální terminál k terminálu kontejneru a spouští se v interaktivním režimu. `-p 5000:80` Zveřejňuje port 80 na kontejneru na port 80 na síťovém rozhraní localhost.

## <a name="push-the-image-to-a-registry"></a>Vložení image do registru

Jakmile ověříte, že bitová kopie funguje, budete ji muset odeslat do registru Docker, aby byla k dispozici v jiných systémech. Interní sítě budou muset zřídit registr Docker. Může to být tak jednoduché jako [vlastní `registry` image běžícího Docker](https://docs.docker.com/registry/deploying/) (to je správné, registr Docker běží v kontejneru Docker), ale k dispozici jsou i další komplexní řešení. Pro externí sdílení a cloudové použití jsou k dispozici různé spravované Registry, například [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) nebo [Docker Hub](https://docs.docker.com/docker-hub/repos/).

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