---
ms.openlocfilehash: 5e77b7bd73c09e061a94a29703cf5286814d1ebb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602913"
---

[Rozhraní .NET Core je dostupné z obchodu s modulem snap-in.](https://snapcraft.io/dotnet-sdk)

Modul snap je sada aplikací a její závislosti, které fungují beze změn v mnoha různých distribucích systému Linux. Přichycení jsou zjistitelná a instalovatelné z úložiště pro modul snap-in. Další informace o modulu snap-in najdete v tématu [Začínáme s modulem snap-in](https://snapcraft.io/docs/getting-started).

Prostřednictvím modulu snap-in jsou k dispozici pouze podporované verze rozhraní .NET Core.

### <a name="install-the-sdk"></a>Instalace sady SDK

Balíčky přichycení pro .NET Core SDK jsou všechny publikovány pod stejným identifikátorem: `dotnet-sdk` . Konkrétní verzi sady SDK můžete nainstalovat zadáním kanálu. Sada SDK obsahuje modul runtime pro přereakci. V následující tabulce jsou uvedeny kanály:

| Verze .NET Core | Přichycení balíčku             |
|-------------------|--------------------------|
| 3,1 (LTS)         | `3.1` nebo `latest/stable` |
| 2,1 (LTS)         | `2.1`                    |
| .NET 5,0 Preview  | `5.0/beta`               |

`snap install`K instalaci balíčku .NET Core SDK přichycení použijte příkaz. Pomocí `--channel` parametru určete, která verze se má nainstalovat. Pokud je tento parametr vynechán, `latest/stable` je použit. V tomto příkladu `3.1` je určena:

```bash
sudo snap install dotnet-sdk --classic --channel=3.1
```

Dále Zaregistrujte `dotnet` příkaz pro systém pomocí `snap alias` příkazu:

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

Tento příkaz je formátován jako: `sudo snap alias {package}.{command} {alias}` . Můžete zvolit libovolný `{alias}` název, který chcete. Příkaz můžete například pojmenovat po konkrétní verzi nainstalované modulem snap: `sudo snap alias dotnet-sdk.dotnet dotnet31` . Při použití příkazu `dotnet31` vyvoláte tuto specifickou verzi rozhraní .NET. Není to ale kompatibilní s většinou výukových kurzů a příkladů, protože očekávají, že `dotnet` příkaz bude k dispozici.

### <a name="install-the-runtime"></a>Instalace modulu runtime

Balíčky přichycení pro modul runtime .NET Core jsou publikovány v rámci vlastního identifikátoru balíčku. V následující tabulce jsou uvedeny identifikátory balíčků:

| Verze .NET Core | Přichycení balíčku        |
|-------------------|---------------------|
| 3,1 (LTS)         | `dotnet-runtime-31` |
| 3.0               | `dotnet-runtime-30` |
| 2,2               | `dotnet-runtime-22` |
| 2,1 (LTS)         | `dotnet-runtime-21` |

Použijte `snap install` příkaz k instalaci balíčku modulu runtime .NET Core Runtime. V tomto příkladu je nainstalovaná platforma .NET Core 3,1:

```bash
sudo snap install dotnet-runtime-31 --classic
```

Dále Zaregistrujte `dotnet` příkaz pro systém pomocí `snap alias` příkazu:

```bash
sudo snap alias dotnet-runtime-31.dotnet dotnet
```

Tento příkaz je formátován jako: `sudo snap alias {package}.{command} {alias}` . Můžete zvolit libovolný `{alias}` název, který chcete. Příkaz můžete například pojmenovat po konkrétní verzi nainstalované modulem snap: `sudo snap alias dotnet-runtime-31.dotnet dotnet31` . Při použití příkazu `dotnet31` vyvoláte tuto specifickou verzi rozhraní .NET. Není to ale kompatibilní s většinou výukových kurzů a příkladů, protože očekávají, že `dotnet` příkaz bude k dispozici.

### <a name="ssl-certificate-errors"></a>Chyby certifikátu SSL

Když je rozhraní .NET nainstalované prostřednictvím modulu snap-in, je možné, že na některých distribuce se certifikáty .NET SSL nenašly a v průběhu této chyby se může zobrazit chyba podobná této `restore` :

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

Chcete-li tento problém vyřešit, nastavte několik proměnných prostředí:

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

Umístění certifikátu se bude lišit podle distribuce. Tady jsou umístění pro distribuce, kde jsme narazili na problém.

* Fedora`/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`
* OpenSUSE`/etc/ssl/ca-bundle.pem`
* Solus -`/etc/ssl/certs/ca-certificates.crt`
