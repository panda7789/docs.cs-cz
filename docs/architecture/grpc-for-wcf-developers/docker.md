---
title: Docker – gRPC pro vývojáře WCF
description: Vytváření imagí Docker pro aplikace ASP.NET Core gRPC
ms.date: 09/02/2019
ms.openlocfilehash: d23dc46526183b459c36f11bae4def8b1c9b9410
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711304"
---
# <a name="create-docker-images"></a>Vytváření imagí Docker

Tato část se zabývá vytvářením imagí Docker pro aplikace ASP.NET Core gRPC, které jsou připravené ke spuštění v Docker, Kubernetes nebo v jiných kontejnerových prostředích. Použitá ukázková aplikace s ASP.NET Core webovou aplikací MVC a službou gRPC je k dispozici v úložišti [dotnet-Architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) na GitHubu.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Základní image Microsoft pro aplikace ASP.NET Core

Microsoft poskytuje řadu základních imagí pro sestavování a spouštění aplikací .NET Core. Pokud chcete vytvořit image ASP.NET Core 3,0, použijete dvě základní Image: 

- Image sady SDK pro sestavování a publikování aplikace
- Bitová kopie modulu runtime pro nasazení.

| Obrázek | Popis |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | Pro sestavování aplikací pomocí `docker build`. Nedá se použít v produkčním prostředí. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Obsahuje závislosti modulu runtime a ASP.NET Core. Pro produkční prostředí. |

Pro každý obrázek jsou k dispozici čtyři varianty založené na různých distribucích systému Linux, které jsou odlišeny pomocí značek.

| Značky obrázku | Linux | Poznámky |
| --------- | ----- | ----- |
| 3,0 – Buster, 3,0 | Debian 10 | Výchozí obrázek, pokud není zadána varianta operačního systému. |
| 3,0 – Alpine | Alpine 3,9 | Obrázky Alpine Base jsou mnohem menší než Debian nebo Ubuntu. |
| 3,0 – disco | Ubuntu 19.04 | |
| 3,0 – Bionic | Ubuntu 18,04 | |

Základní obrázek Alpine je okolo 100 MB, v porovnání s 200 MB pro Image Debian a Ubuntu. Některé softwarové balíčky nebo knihovny nemusí být k dispozici ve správě balíčků Alpine. Pokud si nejste jistí, která image se má použít, měli byste zvolit výchozí Debian.

> [!IMPORTANT]
> Ujistěte se, že používáte stejnou variantu systému Linux pro sestavení a modul runtime. Aplikace sestavené a publikované na jednom variantě nemusí fungovat na jiném.

## <a name="create-a-docker-image"></a>Vytvoření image Docker

Image Docker je definovaná pomocí *souboru Dockerfile*. Jedná se o textový soubor, který obsahuje všechny příkazy potřebné k sestavení aplikace a instalaci všech závislostí, které jsou požadovány pro vytvoření nebo spuštění aplikace. Následující příklad ukazuje nejjednodušší souboru Dockerfile pro aplikaci ASP.NET Core 3,0:

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

Souboru Dockerfile má dvě části: první používá základní image `sdk` k sestavení a publikování aplikace. Druhá vytvoří bitovou kopii modulu runtime ze základu `aspnet`. Důvodem je to, že bitová kopie `sdk` o velikosti přibližně 900 MB, v porovnání s přibližně 200 MB pro bitovou kopii za běhu a většinu jejího obsahu nepotřebnou za běhu.

### <a name="the-build-steps"></a>Kroky sestavení

| Krok | Popis |
| ---- | ----------- |
| `FROM ...` | Deklaruje základní obrázek a přiřadí alias `builder`. |
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

Základní image Microsoftu pro Docker nastaví proměnnou prostředí `ASPNETCORE_URLS` na `http://+:80`, což znamená, že Kestrel na tomto portu běží bez protokolu HTTPS. Pokud používáte protokol HTTPS s vlastním certifikátem (jak je popsáno v [samoobslužných aplikacích gRPC](self-hosted.md)), měli byste ho přepsat. Nastavte proměnnou prostředí v rámci souboru Dockerfile pro vytvoření bitové kopie modulu runtime.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>Soubor. dockerignore

Podobně jako `.gitignore` soubory, které vyloučí určité soubory a adresáře ze správy zdrojového kódu, lze `.dockerignore` soubor použít k vyloučení souborů a adresářů, které se zkopírují do bitové kopie během sestavení. Tím se nejen ukládá pouze kopírování času, ale může se taky vyhnout nějakým chybám, které vyplývají z toho, že se `obj` adresář z počítače zkopíroval do image. Do souboru `.dockerignore` byste měli přidat položky pro `bin` a `obj`.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Sestavení image

Pro řešení s jednou aplikací, a proto jediným souboru Dockerfile, je nejjednodušší umístit souboru Dockerfile do základního adresáře. Jinými slovy, umístěte je do stejného adresáře jako soubor `.sln`. V takovém případě pro sestavení image použijte následující příkaz `docker build` z adresáře obsahujícího rozhraní souboru Dockerfile.

```console
docker build --tag stockdata .
```

Nematoucí název `--tag` příznakem (který může být zkrácen na `-t`) určuje celý název obrázku, včetně skutečné značky, je-li tento parametr zadán. `.` na konci určuje kontext, ve kterém se bude sestavení spouštět; aktuální pracovní adresář pro příkazy `COPY` v souboru Dockerfile.

Pokud máte více aplikací v rámci jednoho řešení, můžete souboru Dockerfile pro každou aplikaci ve vlastní složce vedle souboru `.csproj`. Stále byste měli spustit příkaz `docker build` ze základního adresáře, aby bylo zajištěno, že řešení a všechny projekty budou zkopírovány do obrázku. Pomocí příznaku `--file` (nebo `-f`) můžete zadat souboru Dockerfile pod aktuálním adresářem.

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Spuštění image v kontejneru na počítači

Pokud chcete spustit image v místní instanci Docker, použijte příkaz `docker run`.

```console
docker run -ti -p 5000:80 stockdata
```

Příznak `-ti` připojí váš aktuální terminál k terminálu kontejneru a spustí se v interaktivním režimu. `-p 5000:80` zveřejňuje (odkazy) port 80 na kontejneru na port 80 na síťovém rozhraní localhost.

## <a name="push-the-image-to-a-registry"></a>Vložení image do registru

Až ověříte, že image funguje, nahrajte ji do registru Docker a zpřístupněte ji v dalších systémech. Interní sítě budou muset zřídit registr Docker. Může to být tak jednoduché jako [image s vlastním `registry`m](https://docs.docker.com/registry/deploying/) , která je k dispozici, a je k dispozici i několik komplexních řešení. Pro externí sdílení a cloudové použití jsou k dispozici různé spravované Registry, například [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) nebo [Docker Hub](https://docs.docker.com/docker-hub/repos/).

Pokud chcete přejít do Docker Hub, nahraďte název bitové kopie vaším uživatelem nebo názvem organizace.

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

Pokud chcete přejít do privátního registru, použijte předponu názvu bitové kopie s názvem hostitele registru a názvem organizace.

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

Jakmile je bitová kopie v registru, můžete ji nasadit na jednotlivé hostitele Docker nebo na modul pro orchestraci kontejnerů, jako je Kubernetes.

>[!div class="step-by-step"]
>[Předchozí](self-hosted.md)
>[Další](kubernetes.md)
