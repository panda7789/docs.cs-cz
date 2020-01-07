---
title: Samoobslužné aplikace gRPC – gRPC pro vývojáře WCF
description: Nasazení ASP.NET Corech aplikací gRPC jako samoobslužných služeb.
ms.date: 09/02/2019
ms.openlocfilehash: 00b4ad50eae629b5b36a890d1eecf7119386c74c
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545065"
---
# <a name="self-hosted-grpc-applications"></a>Samoobslužné aplikace gRPC

I když aplikace ASP.NET Core 3,0 je možné hostovat ve službě IIS na Windows serveru, v současné době není možné hostovat aplikaci gRPC ve službě IIS, protože některé funkce HTTP/2 se ještě nepodporují. Tato funkce se očekává v budoucí aktualizaci Windows serveru.

Aplikaci můžete spustit jako službu systému Windows nebo jako službu pro Linux řízenou [systémem](https://en.wikipedia.org/wiki/Systemd), a to díky některým novým funkcím v rozšířeních hostování .net Core 3,0.

## <a name="run-your-app-as-a-windows-service"></a>Spuštění aplikace jako služby systému Windows

Chcete-li nakonfigurovat aplikaci ASP.NET Core tak, aby běžela jako služba systému Windows, nainstalujte balíček [Microsoft. Extensions. Hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) z nástroje NuGet. Pak přidejte volání `UseWindowsService` do metody `CreateHostBuilder` v `Program.cs`.

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

Při publikování aplikace .NET Core se můžete rozhodnout pro vytvoření nasazení *závislého na rozhraní* nebo *samostatného* nasazení. Nasazení závislá na rozhraní vyžadují, aby byl na hostiteli, na kterém je spuštěný, nainstalovaný sdílený modul .NET Core Shared. Samostatně obsažená nasazení jsou publikována s úplnou kopií modulu runtime .NET Core a architekturou a lze ji spustit na jakémkoli hostiteli. Další informace, včetně výhod a nevýhod každého přístupu, naleznete v dokumentaci k [nasazení aplikace .NET Core](../../core/deploying/index.md) .

Chcete-li publikovat samostatné sestavení aplikace, které nevyžaduje instalaci modulu runtime .NET Core 3,0 na hostitele, zadejte modul runtime, který bude součástí aplikace pomocí příznaku `-r` (nebo `--runtime`).

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

Chcete-li publikovat sestavení závislé na rozhraní, vynechejte příznak `-r`.

```console
dotnet publish -c Release -o ./publish
```

Zkopírujte celý obsah adresáře `publish` do instalační složky a pomocí [Nástroje SC](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) vytvořte pro spustitelný soubor službu systému Windows.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a>Přihlášení do protokolu událostí systému Windows

Metoda `UseWindowsService` automaticky přidá poskytovatele [protokolování](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) , který zapíše zprávy protokolu do protokolu událostí systému Windows. Protokolování pro tohoto zprostředkovatele můžete nakonfigurovat přidáním položky `EventLog` do oddílu `Logging` `appsettings.json` nebo jiného zdroje konfigurace. Název zdroje používaný v protokolu událostí lze přepsat nastavením vlastnosti `SourceName` v těchto nastaveních. Pokud název nezadáte, použije se výchozí název aplikace (obvykle se jedná o spustitelný název sestavení).

Další informace o protokolování najdete na konci této kapitoly.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Spuštění aplikace jako služby pro Linux se systémem

Pokud chcete svou aplikaci ASP.NET Core nakonfigurovat tak, aby běžela jako služba pro Linux (nebo *démon* v systému Linux agilním), nainstalujte balíček [Microsoft. Extensions. Hosting. systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) z NuGet. Pak přidejte volání `UseSystemd` do metody `CreateHostBuilder` v `Program.cs`.

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

Nyní publikujte aplikaci (Buď závislou na rozhraní, nebo samostatnou pro příslušné prostředí Linux Runtime), například `linux-x64`), buď ze sady Visual Studio, kliknutím pravým tlačítkem myši na projekt a výběrem možnosti *publikovat* z místní nabídky nebo z .NET Core CLI pomocí následujícího příkazu.

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

Zkopírujte celý obsah adresáře `publish` do instalační složky na hostiteli se systémem Linux. Registrace služby vyžaduje speciální soubor, který se označuje jako "soubor jednotky", který se má přidat do adresáře `/etc/systemd/system`. K vytvoření souboru v této složce budete potřebovat oprávnění root. Pojmenujte soubor s identifikátorem, který chcete použít `systemd` a rozšířením `.service`. Například `/etc/systemd/system/myapp.service`.

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

Vlastnost `Type=notify` oznamuje `systemd`, že ji aplikace upozorní na spuštění a vypnutí. Nastavení `WantedBy=multi-user.target` způsobí, že se služba spustí, když systém Linux dosáhne "runlevel 2", což znamená, že je aktivní negrafické prostředí pro více uživatelů.

Předtím, než `systemd` rozpozná službu, musí znovu načíst konfiguraci. `systemd` můžete ovládat pomocí příkazu `systemctl`. Po opětovném načtení pomocí dílčího příkazu `status` potvrďte, že se aplikace úspěšně zaregistrovala.

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

Službu spusťte pomocí příkazu `start`.

```console
sudo systemctl start myapp.service
```

> [!TIP]
> Rozšíření `.service` je při použití `systemctl start`volitelné.

Chcete-li sdělit `systemd`, aby se služba automaticky spouštěla při spuštění systému, použijte příkaz `enable`.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Přihlášení do deníku

Ekvivalent systému Linux z protokolu událostí systému Windows je `journald`, strukturované protokolovací služby protokolování, která je součástí `systemd`. Protokolovat zprávy zapsané do standardního výstupu pomocí démona Linux se automaticky zapisují do `journald`, takže pokud chcete nakonfigurovat úrovně protokolování, použijte `Console` části Konfigurace protokolování. Metoda `UseSystemd` Host Builder automaticky konfiguruje výstupní formát konzoly tak, aby odpovídaly deníku.

Vzhledem k tomu, že `journald` je standard pro systémy Linux, existuje celá řada nástrojů, které jsou s ní integrovány, a můžete snadno směrovat protokoly z `journald` do externího systému protokolování. Místně pracujete na hostiteli pomocí příkazu `journalctl` k zobrazení protokolů z příkazového řádku.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Pokud máte k dispozici prostředí GUI na vašem hostiteli, je pro Linux k dispozici několik grafických prohlížečů, jako jsou například *QJournalctl* a *GNOME-* log.

Další informace o dotazování systémového deníku z příkazového řádku pomocí `journalctl`naleznete [na stránce muž](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Certifikáty HTTPS pro samoobslužné aplikace

Při spuštění aplikace gRPC v produkčním prostředí byste měli použít certifikát TLS od důvěryhodné certifikační autority (CA). Tato certifikační autorita může být veřejná certifikační autoritou nebo interní pro vaši organizaci.

Na hostitelích s Windows může být certifikát načtený z zabezpečeného [úložiště certifikátů](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) pomocí třídy <xref:System.Security.Cryptography.X509Certificates.X509Store>. Třídu `X509Store` lze také použít s úložištěm klíčů OpenSSL na některých hostitelích se systémem Linux.

Certifikáty mohou být také vytvořeny pomocí jednoho z [konstruktorů X509Certificate2](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), buď ze souboru (například `.pfx` chráněný silným heslem), nebo z binárních dat načtených ze zabezpečené služby úložiště, jako je například [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).

Kestrel se dá nakonfigurovat tak, aby používal certifikát dvěma způsoby: z konfigurace nebo v kódu.

### <a name="set-https-certificates-using-configuration"></a>Nastavení certifikátů HTTPS pomocí konfigurace

Konfigurační přístup vyžaduje nastavení cesty k souboru `.pfx` certifikátu a heslo v oddílu konfigurace Kestrel. V `appsettings.json`, které by vypadaly takto.

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

Chcete-li nakonfigurovat HTTPS na Kestrel v kódu, použijte metodu `ConfigureKestrel` pro `IWebHostBuilder` ve třídě `Program`.

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

Heslo pro `.pfx` soubor by se mělo znovu uložit v a načíst ze zdroje zabezpečené konfigurace.

>[!div class="step-by-step"]
>[Předchozí](grpc-in-production.md)
>[Další](docker.md)
