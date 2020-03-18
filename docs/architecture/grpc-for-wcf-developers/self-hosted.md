---
title: Samostatně hostované gRPC aplikace - gRPC pro vývojáře WCF
description: Nasazení ASP.NET aplikací Core gRPC jako samoobslužných služeb.
ms.date: 09/02/2019
ms.openlocfilehash: 00fb1453e19a02469f80af79672e0c1f72c7280f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147799"
---
# <a name="self-hosted-grpc-applications"></a>Samoobslužné gRPC aplikace

Přestože ASP.NET aplikace Core 3.0 mohou být hostovány ve službě IIS v systému Windows Server, v současné době není možné hostovat aplikaci gRPC ve službě IIS, protože některé funkce HTTP/2 nejsou podporovány. Tato funkce je cílem budoucí aktualizace systému Windows Server.

Aplikaci můžete spustit jako službu systému Windows. Nebo ji můžete spustit jako službu Linuxu řízenou [systemd](https://en.wikipedia.org/wiki/Systemd), protože nové funkce v rozšířeních .NET Core 3.0 hosting.

## <a name="run-your-app-as-a-windows-service"></a>Spuštění aplikace jako služby Windows

Chcete-li nakonfigurovat ASP.NET základní aplikaci tak, aby běžela jako služba systému Windows, nainstalujte balíček [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) z NuGet. Potom přidejte `UseWindowsService` volání `CreateHostBuilder` k `Program.cs`metodě v .

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
> Pokud aplikace není spuštěna jako služba `UseWindowsService` systému Windows, metoda neprovádí nic.

Nyní publikujte aplikaci pomocí jedné z těchto metod:

* Z Visual Studia kliknutím pravým tlačítkem myši na projekt a výběrem **publikovat** v místní nabídce.
* Z rozhraní .NET Core CLI.

Při publikování aplikace .NET Core můžete vytvořit nasazení *závislé na rozhraní* nebo *samostatné* nasazení. Nasazení závislá na rozhraní vyžadují, aby byl sdílený runtime .NET Core nainstalován na hostiteli, kde jsou spuštěny. Samostatná nasazení jsou publikována s úplnou kopií runtime a frameworku .NET Core a lze je spustit na libovolném hostiteli. Další informace, včetně výhod a nevýhod každého přístupu, naleznete v dokumentaci [k nasazení aplikace .NET Core.](../../core/deploying/index.md)

Chcete-li publikovat samostatné sestavení aplikace, která nevyžaduje instalaci runtime .NET Core 3.0 na hostiteli, zadejte dobu runtime, která má být součástí aplikace. Použijte `-r` příznak `--runtime`(nebo).

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

Chcete-li publikovat sestavení závislé na `-r` rámci, vyneche příznak.

```dotnetcli
dotnet publish -c Release -o ./publish
```

Zkopírujte celý obsah `publish` adresáře do instalační složky. Potom pomocí [nástroje sc](/windows/desktop/services/controlling-a-service-using-sc) vytvořte službu systému Windows pro spustitelný soubor.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>Protokolovat do protokolu událostí systému Windows

Metoda `UseWindowsService` automaticky přidá [zprostředkovatele protokolování,](/aspnet/core/fundamentals/logging/) který zapisuje zprávy protokolu do protokolu událostí systému Windows. Protokolování tohoto zprostředkovatele můžete `EventLog` nakonfigurovat `Logging` přidáním `appsettings.json` položky do oddílu nebo jiného zdroje konfigurace.

Název zdroje použitý v protokolu událostí můžete přepsat `SourceName` nastavením vlastnosti v těchto nastaveních. Pokud název nezadáte, bude použit výchozí název aplikace (obvykle název spustitelného sestavení).

Více informací o protokolování je na konci této kapitoly.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Spusťte aplikaci jako službu Linuxu s systemd

Chcete-li nakonfigurovat aplikaci ASP.NET Core tak, aby běžela jako služba Linuxu (nebo *daemon* v jazyce Linuxu), nainstalujte balíček [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) z NuGet. Potom přidejte `UseSystemd` volání `CreateHostBuilder` k `Program.cs`metodě v .

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
> Pokud aplikace není spuštěna jako služba `UseSystemd` Linuxu, metoda neprovádí nic.

Nyní publikujte svou žádost. Aplikace může být závislá na rámci nebo samostatně obsažená pro příslušný `linux-x64`linuxový runtime (například). Publikovat můžete pomocí jedné z těchto metod:

* Z Visual Studia kliknutím pravým tlačítkem myši na projekt a výběrem **publikovat** v místní nabídce.
* Z rozhraní příkazového příkazu .NET Core pomocí následujícího příkazu:

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
Zkopírujte celý obsah `publish` adresáře do instalační složky na hostiteli Linuxu. Registrace služby vyžaduje přidání do *unit file* `/etc/systemd/system` adresáře speciální soubor nazývaný soubor jednotky . K vytvoření souboru v této složce budete potřebovat oprávnění root. Pojmenujte soubor identifikátorem, `systemd` který chcete `.service` použít, a příponou. Použijte například `/etc/systemd/system/myapp.service`.

Soubor služby používá formát INI, jak je znázorněno v tomto příkladu:

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

Vlastnost `Type=notify` říká, `systemd` že aplikace ji upozorní na spuštění a vypnutí. Nastavení `WantedBy=multi-user.target` způsobí spuštění služby, když systém Linux dosáhne "runlevel 2", což znamená, že je aktivní negrafické prostředí pro více uživatelů.

Předtím, než `systemd` rozpozná službu, je třeba znovu načíst jeho konfiguraci. Řízení `systemd` pomocí příkazu. `systemctl` Po opětovném načtení použijte `status` podpříkaz k potvrzení, že aplikace byla úspěšně zaregistrována.

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

Pokud jste službu nakonfigurovali správně, získáte následující výstup:

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

Ke `start` spuštění služby použijte příkaz.

```console
sudo systemctl start myapp.service
```

> [!TIP]
> Rozšíření `.service` je volitelné, pokud `systemctl start`používáte .

Chcete-li spustit `systemd` službu automaticky při `enable` spuštění systému, použijte příkaz.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Protokolovat do deníku

Linuxový ekvivalent protokolu událostí `journald`systému Windows je strukturovaná systémová `systemd`služba protokolování, která je součástí aplikace . Protokolovat zprávy zapsané do standardního výstupu linuxovým `journald`daemonem jsou automaticky zapsány do aplikace . Chcete-li konfigurovat úrovně `Console` protokolování, použijte část konfigurace protokolování. Metoda `UseSystemd` tvůrce hostitelů automaticky konfiguruje výstupní formát konzoly tak, aby vyhovoval deníku.

Vzhledem k tomu, `journald` že je standardem pro protokoly Linux, různé nástroje integrovat s ním. Protokoly můžete snadno `journald` směrovat do externího systému protokolování. Pracovat místně na hostiteli, můžete `journalctl` použít příkaz k zobrazení protokolů z příkazového řádku.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Pokud máte na hostiteli k dispozici prostředí GUI, je k dispozici několik grafických prohlížečů protokolů pro Linux, jako jsou *QJournalctl* a *gnome-logs*.

Další informace o dotazování `systemd` deníku z příkazového řádku pomocí naleznete `journalctl`na stránkách [man](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Certifikáty HTTPS pro samoobslužné aplikace

Pokud v produkčním provozu používáte aplikaci gRPC, měli byste použít certifikát TLS od důvěryhodné certifikační autority (CA). Tato certifikační autorita může být veřejná certifikační autorita nebo interní certifikační autorita pro vaši organizaci.

Na hostitelích systému Windows můžete certifikát načíst <xref:System.Security.Cryptography.X509Certificates.X509Store> z úložiště zabezpečených [certifikátů](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) pomocí třídy. Třídu `X509Store` můžete také použít s úložištěm klíčů OpenSSL na některých hostitelích Linuxu.

Certifikáty můžete také vytvořit pomocí jednoho z [konstruktorů X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), a to buď z následujících:

* Soubor, například `.pfx` soubor chráněný silným heslem
* Binární data načtená ze služby zabezpečeného úložiště, jako je [azure key vault](https://azure.microsoft.com/services/key-vault/)

Kestrel můžete nakonfigurovat tak, aby používal certifikát dvěma způsoby: z konfigurace nebo v kódu.

### <a name="set-https-certificates-by-using-configuration"></a>Nastavení certifikátů HTTPS pomocí konfigurace

Konfigurační přístup vyžaduje nastavení `.pfx` cesty k souboru certifikátu a hesla v části konfigurace kestrelu. V `appsettings.json`, které by vypadaly takto:

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

Zadejte heslo pomocí zabezpečeného konfiguračního zdroje, jako je Azure Key Vault nebo Hashicorp Vault.

> [!IMPORTANT]
> Neuklápejte nešifrovaná hesla do konfiguračních souborů.

### <a name="set-https-certificates-in-code"></a>Nastavení certifikátů HTTPS v kódu

Chcete-li nakonfigurovat protokol HTTPS na `ConfigureKestrel` kestrelu v kódu, použijte metodu ve `IWebHostBuilder` `Program` třídě.

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

Opět nezapomeňte uložit heslo pro `.pfx` soubor a načíst z zabezpečeného konfiguračního zdroje.

>[!div class="step-by-step"]
>[Předchozí](grpc-in-production.md)
>[další](docker.md)
