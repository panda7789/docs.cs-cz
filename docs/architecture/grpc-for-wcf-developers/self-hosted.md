---
title: Samoobslužné aplikace gRPC – gRPC pro vývojáře WCF
description: Nasazení ASP.NET Corech aplikací gRPC jako samoobslužných služeb.
ms.date: 09/02/2019
ms.openlocfilehash: 2244f161ad4b5d60138ae0f7b4d6a9c8c8829aa8
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503399"
---
# <a name="self-hosted-grpc-applications"></a>Samoobslužné aplikace gRPC

I když je možné aplikace ASP.NET Core 3,0 hostovat ve službě IIS na Windows serveru, v současné době není možné hostovat aplikaci gRPC ve službě IIS, protože některé funkce HTTP/2 se nepodporují. Tato funkce je cílem budoucí aktualizace Windows serveru.

Aplikaci můžete spustit jako službu systému Windows. Nebo ho můžete spustit jako službu Linux řízenou [systémem](https://en.wikipedia.org/wiki/Systemd), protože v rozšířeních hostování .net Core 3,0 jsou nové funkce.

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

Nyní můžete aplikaci publikovat pomocí jedné z následujících metod:

* V aplikaci Visual Studio kliknutím pravým tlačítkem myši na projekt a výběrem možnosti **publikovat** v místní nabídce.
* Z .NET Core CLI.

Při publikování aplikace .NET Core se můžete rozhodnout pro vytvoření nasazení *závislého na rozhraní* nebo *samostatného* nasazení. Nasazení závislá na rozhraní vyžadují, aby byl na hostiteli, na kterém je spuštěný, nainstalovaný sdílený modul .NET Core Shared. Samostatně obsažená nasazení jsou publikována s úplnou kopií modulu runtime .NET Core a architekturou a lze ji spustit na jakémkoli hostiteli. Další informace, včetně výhod a nevýhod každého přístupu, naleznete v dokumentaci k [nasazení aplikace .NET Core](../../core/deploying/index.md) .

Chcete-li publikovat samostatné sestavení aplikace, které nevyžaduje instalaci modulu runtime .NET Core 3,0 na hostitele, zadejte modul runtime, který bude součástí aplikace. Použijte příznak `-r` (nebo `--runtime`).

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

Chcete-li publikovat sestavení závislé na rozhraní, vynechejte příznak `-r`.

```dotnetcli
dotnet publish -c Release -o ./publish
```

Zkopírujte celý obsah adresáře `publish` do instalační složky. Pak pomocí [Nástroje SC](/windows/desktop/services/controlling-a-service-using-sc) vytvořte službu systému Windows pro spustitelný soubor.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>Přihlášení do protokolu událostí systému Windows

Metoda `UseWindowsService` automaticky přidá poskytovatele [protokolování](/aspnet/core/fundamentals/logging/) , který zapíše zprávy protokolu do protokolu událostí systému Windows. Protokolování pro tohoto zprostředkovatele můžete nakonfigurovat přidáním položky `EventLog` do oddílu `Logging` `appsettings.json` nebo jiného zdroje konfigurace. 

Název zdroje použitý v protokolu událostí můžete přepsat nastavením vlastnosti `SourceName` v těchto nastaveních. Pokud název nezadáte, použije se výchozí název aplikace (obvykle se jedná o spustitelný název sestavení).

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

Nyní publikujte aplikaci. Aplikace může být buď závislá na architektuře, nebo samostatná jako pro příslušné prostředí Linux runtime (například `linux-x64`). Můžete publikovat pomocí jedné z následujících metod:

* V aplikaci Visual Studio kliknutím pravým tlačítkem myši na projekt a výběrem možnosti **publikovat** v místní nabídce. 
* Z .NET Core CLI pomocí následujícího příkazu:

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
Zkopírujte celý obsah adresáře `publish` do instalační složky na hostiteli se systémem Linux. Registrace služby vyžaduje speciální soubor nazvaný *soubor jednotky*, který bude přidán do adresáře `/etc/systemd/system`. K vytvoření souboru v této složce budete potřebovat oprávnění root. Pojmenujte soubor s identifikátorem, který chcete použít `systemd` a rozšířením `.service`. Použijte například `/etc/systemd/system/myapp.service`.

Soubor služby používá formát INI, jak je znázorněno v následujícím příkladu:

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

Pokud jste službu správně nakonfigurovali, získáte následující výstup:

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

Ekvivalent systému Linux v protokolu událostí Windows je `journald`, strukturované protokolovací služby protokolování, která je součástí `systemd`. Protokolovat zprávy zapsané do standardního výstupu pomocí démona Linux se automaticky zapisují do `journald`. Chcete-li nakonfigurovat úrovně protokolování, použijte část `Console` v konfiguraci protokolování. Metoda `UseSystemd` Host Builder automaticky konfiguruje výstupní formát konzoly tak, aby odpovídaly deníku.

Vzhledem k tomu, že `journald` je standard pro protokoly Linux, je k tomu integrovaná celá řada nástrojů. Protokoly můžete snadno směrovat z `journald` do externího systému protokolování. Místně pracujete na hostiteli pomocí příkazu `journalctl` k zobrazení protokolů z příkazového řádku.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Pokud máte k dispozici prostředí GUI na vašem hostiteli, je pro Linux k dispozici několik grafických prohlížečů, jako jsou například *QJournalctl* a *GNOME-* log.

Další informace o dotazování deníku `systemd` z příkazového řádku pomocí `journalctl`najdete [na stránkách Man](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Certifikáty HTTPS pro samoobslužné aplikace

Pokud spouštíte aplikaci gRPC v produkčním prostředí, měli byste použít certifikát TLS od důvěryhodné certifikační autority (CA). Tato certifikační autorita může být veřejná certifikační autoritou nebo interní pro vaši organizaci.

Na hostitelích se systémem Windows můžete načíst certifikát z zabezpečeného [úložiště certifikátů](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) pomocí třídy <xref:System.Security.Cryptography.X509Certificates.X509Store>. Můžete také použít třídu `X509Store` s úložištěm klíčů OpenSSL na některých hostitelích se systémem Linux.

Můžete také vytvořit certifikáty pomocí jednoho z [konstruktorů X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), a to z těchto:

* Soubor, například soubor `.pfx` chráněný silným heslem
* Binární data načtená ze zabezpečené služby úložiště, jako je [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)

Kestrel můžete nakonfigurovat tak, aby používal certifikát dvěma způsoby: z konfigurace nebo v kódu.

### <a name="set-https-certificates-by-using-configuration"></a>Nastavení certifikátů HTTPS pomocí konfigurace

Konfigurační přístup vyžaduje nastavení cesty k souboru `.pfx` certifikátu a heslo v oddílu konfigurace Kestrel. V `appsettings.json`by to vypadalo takto:

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

Zadejte heslo pomocí zabezpečeného zdroje konfigurace, například Azure Key Vault nebo trezoru Hashicorp.

> [!IMPORTANT]
> V konfiguračních souborech neukládejte nešifrovaná hesla.

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

Znovu nezapomeňte uložit heslo pro soubor `.pfx` v a načíst ho ze zabezpečeného zdroje konfigurace.

>[!div class="step-by-step"]
>[Předchozí](grpc-in-production.md)
>[Další](docker.md)
