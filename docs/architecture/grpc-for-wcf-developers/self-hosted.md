---
title: Samoobslužné aplikace gRPC – gRPC pro vývojáře WCF
description: Nasazení ASP.NET Corech aplikací gRPC jako samoobslužných služeb.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1269137b58f4d25f407a6a04327c51bc9f069c1b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184104"
---
# <a name="self-hosted-grpc-applications"></a>Samoobslužné aplikace gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

I když aplikace ASP.NET Core 3,0 je možné hostovat ve službě IIS na Windows serveru, v současné době není možné hostovat aplikaci gRPC ve službě IIS, protože některé funkce HTTP/2 se ještě nepodporují. Tato funkce se očekává v budoucí aktualizaci Windows serveru.

Aplikaci můžete spustit jako službu systému Windows nebo jako službu pro Linux řízenou [systémem](https://en.wikipedia.org/wiki/Systemd), a to díky některým novým funkcím v rozšířeních hostování .net Core 3,0.

## <a name="run-your-app-as-a-windows-service"></a>Spuštění aplikace jako služby systému Windows

Chcete-li nakonfigurovat aplikaci ASP.NET Core tak, aby běžela jako služba systému Windows, nainstalujte balíček [Microsoft. Extensions. Hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) z nástroje NuGet. Pak přidejte volání `UseWindowsService` `CreateHostBuilder` do metody v `Program.cs`.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseWindowsService() // Enable running as a Windows service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> Pokud aplikace není spuštěna jako služba systému Windows, `UseWindowsService` metoda neprovede žádné akce.

Nyní můžete aplikaci publikovat buď ze sady Visual Studio, a to tak, že kliknete pravým tlačítkem na projekt a zvolíte možnost *publikovat* z kontextové nabídky nebo z .NET Core CLI.

Při publikování aplikace .NET Core se můžete rozhodnout pro vytvoření nasazení *závislého na rozhraní* nebo *samostatného* nasazení. Nasazení závislá na rozhraní vyžadují, aby byl na hostiteli, na kterém je spuštěný, nainstalovaný sdílený modul .NET Core Shared. Samostatně obsažená nasazení jsou publikována s úplnou kopií modulu runtime .NET Core a architekturou a lze ji spustit na jakémkoli hostiteli. Další informace, včetně výhod a nevýhod každého přístupu, naleznete v dokumentaci k [nasazení aplikace .NET Core](https://docs.microsoft.com/dotnet/core/deploying/) .

Chcete-li publikovat samostatné sestavení aplikace, které nevyžaduje instalaci modulu runtime .NET Core 3,0 na hostitele, zadejte modul runtime, který bude součástí aplikace pomocí `-r` příznaku (nebo `--runtime`).

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

Chcete-li publikovat sestavení závislé na rozhraní, vynechejte `-r` příznak.

```console
dotnet publish -c Release -o ./publish
```

Zkopírujte celý obsah `publish` adresáře do instalační složky a pomocí [Nástroje SC](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) vytvořte pro spustitelný soubor službu systému Windows.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a>Přihlášení do protokolu událostí systému Windows

Metoda automaticky přidá poskytovatele protokolování, který zapíše zprávy protokolu do protokolu událostí systému Windows. [](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) `UseWindowsService` Protokolování pro tohoto zprostředkovatele můžete nakonfigurovat přidáním `EventLog` položky `Logging` do oddílu `appsettings.json` nebo jiného zdroje konfigurace. Název zdroje, který se používá v protokolu událostí, lze přepsat nastavením `SourceName` vlastnosti v těchto nastaveních. Pokud nezadáte název, použije se výchozí název aplikace (obvykle název sestavení spustitelného souboru).

Další informace o protokolování najdete na konci této kapitoly.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Spuštění aplikace jako služby pro Linux se systémem

Pokud chcete svou aplikaci ASP.NET Core nakonfigurovat tak, aby běžela jako služba pro Linux (nebo *démon* v systému Linux agilním), nainstalujte balíček [Microsoft. Extensions. Hosting. systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) z NuGet. Pak přidejte volání `UseSystemd` `CreateHostBuilder` do metody v `Program.cs`.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseSystemd() // Enable running as a Systemd service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> Pokud aplikace není spuštěna jako služba pro Linux, `UseSystemd` metoda neprovede žádné akce.

Nyní publikujte aplikaci (Buď závislou na rozhraní, nebo samostatnou pro příslušné prostředí Linux runtime `linux-x64`), a to buď ze sady Visual Studio, kliknutím pravým tlačítkem myši na projekt a volbou možnosti *publikovat* z kontextové nabídky nebo z rozhraní .NET. Core CLI pomocí následujícího příkazu.

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

Zkopírujte celý obsah `publish` adresáře do instalační složky v hostiteli systému Linux. Registrace služby vyžaduje speciální soubor, který se označuje jako "soubor jednotky", který se má přidat do `/etc/systemd/system` adresáře. K vytvoření souboru v této složce budete potřebovat oprávnění root. Pojmenujte soubor s identifikátorem, `systemd` který chcete použít `.service` , a rozšířením. Například, `/etc/systemd/system/myapp.service`.

Soubor služby používá formát INI, jak je znázorněno v tomto příkladu.

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

`Type=notify` Vlastnost oznamuje`systemd` , že aplikace bude upozorněna na spuštění a vypnutí. Toto `WantedBy=multi-user.target` nastavení způsobí, že se služba spustí, když systém Linux dosáhne "runlevel 2", což znamená, že je aktivní negrafické prostředí pro více uživatelů.

Předtím `systemd` , než nástroj rozpozná službu, musí znovu načíst konfiguraci. Můžete ovládat `systemd` `systemctl` pomocí příkazu. Po opětovném načtení pomocí `status` dílčího příkazu potvrďte, že se aplikace úspěšně zaregistrovala.

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

Pokud jste službu nakonfigurovali správně, zobrazí se následující výstup:

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

Službu spusťte pomocí příkazu. `start`

```console
sudo systemctl start myapp.service
```

> [!TIP]
> Přípona je při použití `systemctl start`volitelná. `.service`

Chcete- `systemd` li říct, že se služba spustí automaticky při spuštění systému `enable` , použijte příkaz.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Přihlášení do deníku

Ekvivalent systému Linux v protokolu událostí systému Windows je `journald`služba strukturovaného protokolování systému, která je `systemd`součástí nástroje. Protokolovat zprávy zapsané do standardního výstupu pomocí démona Linux se automaticky zapisují do `journald`, takže pokud chcete nakonfigurovat úrovně protokolování, `Console` použijte část konfigurace protokolování. Metoda `UseSystemd` sestavení hostitele automaticky nakonfiguruje výstupní formát konzoly tak, aby odpovídaly deníku.

Vzhledem `journald` k tomu, že je standard pro protokoly Linux, existuje celá řada nástrojů, které se s ním integrují, a můžete snadno směrovat `journald` protokoly z do externího systému protokolování. Místně pracujete na hostiteli, pomocí `journalctl` příkazu můžete zobrazit protokoly z příkazového řádku.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Pokud máte k dispozici prostředí GUI na vašem hostiteli, je pro Linux k dispozici několik grafických prohlížečů, jako jsou například *QJournalctl* a *GNOME-* log.

Další informace o dotazování systémového deníku z příkazového řádku pomocí `journalctl`najdete [na stránkách Man](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Certifikáty HTTPS pro samoobslužné aplikace

Při spuštění aplikace gRPC v produkčním prostředí byste měli použít certifikát TLS od důvěryhodné certifikační autority (CA). Tato certifikační autorita může být veřejná certifikační autoritou nebo interní pro vaši organizaci.

Na hostitelích s Windows může být certifikát načtený z zabezpečeného [úložiště certifikátů](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores) pomocí [třídy X509Store](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0). `X509Store` Třídu lze také použít s úložištěm OpenSSL Key na některých hostitelích se systémem Linux.

Certifikáty je také možné vytvořit pomocí jednoho z [konstruktorů X509Certificate2](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), buď ze souboru (například `.pfx` soubor chráněný silným heslem), nebo z binárních dat načtených ze zabezpečené služby úložiště, jako je [Azure Key Vault ](https://azure.microsoft.com/services/key-vault/).

Kestrel se dá nakonfigurovat tak, aby používal certifikát dvěma způsoby: z konfigurace nebo v kódu.

### <a name="set-https-certificates-using-configuration"></a>Nastavení certifikátů HTTPS pomocí konfigurace

Konfigurační přístup vyžaduje nastavení cesty k souboru certifikátu `.pfx` a heslo v oddílu konfigurace Kestrel. V `appsettings.json` takovém případě by vypadala takto.

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "cert.pfx",
        "Password": "DO NOT STORE PLAINTEXT PASSWORDS IN APPSETTINGS FILES"
      }
    }
  }
}
```

Heslo by mělo být k dispozici pomocí zabezpečeného zdroje konfigurace, jako je Azure webtrezor nebo trezor Hashicorp.

Nešifrovaná hesla byste neměli ukládat v konfiguračních souborech.

### <a name="set-https-certificates-in-code"></a>Nastavení certifikátů HTTPS v kódu

Chcete-li nakonfigurovat https na Kestrel v kódu, `ConfigureKestrel` použijte metodu `IWebHostBuilder` pro ve `Program` třídě.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
            webBuilder.ConfigureKestrel(kestrel =>
            {
                kestrel.ConfigureHttpsDefaults(https =>
                {
                    https.ServerCertificate = new X509Certificate2("mycert.pfx", "password");
                });
            });
        });
```

Heslo pro tento `.pfx` soubor byste znovu měli uložit v a načíst ze zdroje zabezpečené konfigurace.

>[!div class="step-by-step"]
>[Předchozí](grpc-in-production.md)
>[Další](docker.md)
