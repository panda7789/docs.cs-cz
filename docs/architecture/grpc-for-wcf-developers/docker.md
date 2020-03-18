---
title: Docker - gRPC pro vývojáře WCF
description: Vytváření imitací Dockeru pro ASP.NET core gRPC aplikace
ms.date: 09/02/2019
ms.openlocfilehash: e67c43f9486fbfe9a5d3e84e3b74770eb621f604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148111"
---
# <a name="create-docker-images"></a>Vytváření imitek Dockeru

Tato část popisuje vytváření imitek Dockeru pro ASP.NET core gRPC aplikace, připravené ke spuštění v Dockeru, Kubernetes nebo jiných kontejnerových prostředích. Použitá ukázková aplikace s ASP.NET webové aplikace Core MVC a službou gRPC je k dispozici v úložišti [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) na GitHubu.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Základní image Microsoftu pro aplikace ASP.NET Core

Společnost Microsoft poskytuje řadu základních bitových kopií pro vytváření a spouštění aplikací .NET Core. Chcete-li vytvořit obraz ASP.NET Jádra 3.0, použijte dva základní obrazy:

- Bitovou kopii sady SDK pro sestavení a publikování aplikace.
- Bitová kopie za běhu pro nasazení.

| Image | Popis |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | Pro vytváření `docker build`aplikací s . Nepoužívat ve výrobě. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Obsahuje závislosti runtime a ASP.NET Core. Pro výrobu. |

Pro každý obrázek existují čtyři varianty založené na různých distribucích Linuxu, které se vyznačují značkami.

| Značka obrázku (značky) | Linux | Poznámky |
| --------- | ----- | ----- |
| 3.0-buster, 3.0 | Debian 10 | Výchozí obrázek, pokud není zadána žádná varianta operačního systému. |
| 3.0-alpské | Alpská 3,9 | Alpské základní obrazy jsou mnohem menší než ty Debian nebo Ubuntu. |
| 3.0-diskotéka | Ubuntu 19.04 | |
| 3.0-bionické | Ubuntu 18.04 | |

Základní obrázek Alpine je kolem 100 MB, ve srovnání s 200 MB pro obrazy Debian a Ubuntu. Některé softwarové balíčky nebo knihovny nemusí být ve správě balíčků společnosti Alpine k dispozici. Pokud si nejste jisti, který obrázek použít, měli byste pravděpodobně zvolit výchozí Debian.

> [!IMPORTANT]
> Ujistěte se, že používáte stejnou variantu Linuxu pro sestavení a runtime. Aplikace vytvořené a publikované na jedné variantě nemusí fungovat na jiné variantě.

## <a name="create-a-docker-image"></a>Vytvoření image Dockeru

Image Dockeru je definována *dockerfile*. Jedná se o textový soubor, který obsahuje všechny příkazy potřebné k vytvoření aplikace a instalaci všech závislostí, které jsou požadovány pro sestavení nebo spuštění aplikace. Následující příklad ukazuje nejjednodušší Dockerfile pro ASP.NET core 3.0 aplikace:

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

Dockerfile má dvě části: první `sdk` používá základní image k sestavení a publikování aplikace; druhý vytvoří bitovou kopii `aspnet` za běhu ze základny. Důvodem je, že `sdk` obraz je kolem 900 MB, ve srovnání s přibližně 200 MB pro bitovou kopii za běhu a většina jeho obsahu jsou zbytečné za běhu.

### <a name="the-build-steps"></a>Kroky sestavení

| Krok | Popis |
| ---- | ----------- |
| `FROM ...` | Deklaruje základní obrázek a přiřadí `builder` alias. |
| `WORKDIR /src` | Vytvoří `/src` adresář a nastaví jej jako aktuální pracovní adresář. |
| `COPY . .` | Zkopíruje vše pod aktuálním adresářem na hostiteli do aktuálního adresáře v obraze. |
| `RUN dotnet restore` | Obnoví všechny externí balíčky (ASP.NET core 3.0 framework je předinstalovaný s SadsDK). |
| `RUN dotnet publish ...` | Vytvoří a publikuje sestavení verze. Všimněte `--runtime` si, že příznak není povinný. |

### <a name="the-runtime-image-steps"></a>Kroky bitové kopie za běhu

| Krok | Popis |
| ---- | ----------- |
| `FROM ...` | Deklaruje novou základní bitovou kopii. |
| `WORKDIR /app` | Vytvoří `/app` adresář a nastaví jej jako aktuální pracovní adresář. |
| `COPY --from=builder ...` | Zkopíruje publikovanou aplikaci z předchozího `builder` obrázku `FROM` pomocí aliasu z prvního řádku. |
| `ENTRYPOINT [ ... ]` | Nastaví spuštění příkazu při spuštění kontejneru. Příkaz `dotnet` v bitové kopii za běhu může spouštět pouze soubory DLL. |

### <a name="https-in-docker"></a>HTTPS v Dockeru

Základní image Microsoftu `ASPNETCORE_URLS` pro Docker `http://+:80`nastavují proměnnou prostředí na , což znamená, že Kestrel běží na tomto portu bez protokolu HTTPS. Pokud používáte protokol HTTPS s vlastním certifikátem (jak je popsáno v [aplikacích gRPC s vlastním hostitelem),](self-hosted.md)měli byste to přepsat. Nastavte proměnnou prostředí v části vytvoření bitové kopie za běhu vašeho dockerfile.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>Soubor .dockerignore

Podobně `.gitignore` jako soubory, které vylučují `.dockerignore` určité soubory a adresáře ze správy zdrojového kódu, lze soubor použít k vyloučení souborů a adresářů z kopírování do bitové kopie během sestavení. To nejen šetří čas kopírování, ale může také zabránit některým `obj` chybám, které vznikají z toho, že adresář z počítače zkopírován do obrazu. Minimálně byste měli přidat `bin` položky pro a `obj` do `.dockerignore` souboru.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Sestavení image

Pro řešení s jedinou aplikací, a tedy jeden Dockerfile, je nejjednodušší umístit Dockerfile v základním adresáři. Jinými slovy, vložte jej do `.sln` stejného adresáře jako soubor. V takovém případě k vytvoření bitové `docker build` kopie použijte následující příkaz z adresáře obsahujícího soubor Dockerfile.

```console
docker build --tag stockdata .
```

Zmateně pojmenovaný `--tag` příznak (který lze `-t`zkrátit na ) určuje celý název obrázku, včetně skutečné značky, pokud je zadána. Na `.` konci určuje kontext, ve kterém bude spuštěno sestavení; aktuální pracovní adresář `COPY` pro příkazy v souboru Dockerfile.

Pokud máte více aplikací v rámci jednoho řešení, můžete zachovat Dockerfile pro `.csproj` každou aplikaci ve své vlastní složce, vedle souboru. Stále byste měli `docker build` spustit příkaz ze základního adresáře, abyste zajistili, že řešení a všechny projekty jsou zkopírovány do bitové kopie. Soubor Dockerfile můžete zadat pod aktuálním `--file` adresářem pomocí příznaku (nebo). `-f`

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Spuštění obrázku v kontejneru na počítači

Chcete-li spustit bitovou kopii `docker run` v místní instanci Dockeru, použijte příkaz.

```console
docker run -ti -p 5000:80 stockdata
```

Příznak `-ti` připojí aktuální terminál k terminálu kontejneru a běží v interaktivním režimu. Publikuje `-p 5000:80` (odkazy) port 80 na kontejneru port 5000 na localhost síťové rozhraní.

## <a name="push-the-image-to-a-registry"></a>Zasunutí bitové kopie do registru

Po ověření, že image funguje, zatlačte ji do registru Dockeru, aby byla k dispozici v jiných systémech. Interní sítě budou muset zřídit registr Dockeru. To může být stejně jednoduché jako spuštění [vlastní `registry` image Dockeru](https://docs.docker.com/registry/deploying/) (registr Dockeru běží v kontejneru Dockeru), ale jsou k dispozici různá komplexnější řešení. Pro externí sdílení a využití cloudu jsou k dispozici různé spravované registry, jako je [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) nebo Docker [Hub](https://docs.docker.com/docker-hub/repos/).

Chcete-li přetlačit do Centra Dockeru, předponu název bitové kopie s názvem uživatele nebo organizace.

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

Chcete-li přetlačit do soukromého registru, předponu název bitové kopie s názvem hostitele registru a názvem organizace.

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

Poté, co je bitová kopie v registru, můžete ji nasadit na jednotlivé hostitele Dockeru nebo do modulu orchestrace kontejnerů, jako je Kubernetes.

>[!div class="step-by-step"]
>[Předchozí](self-hosted.md)
>[další](kubernetes.md)
