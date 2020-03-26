---
title: Samostatně hostované gRPC aplikace - gRPC pro vývojáře WCF
description: Nasazení ASP.NET aplikací Core gRPC jako samoobslužných služeb.
ms.date: 09/02/2019
ms.openlocfilehash: 69f70e4077247fd07eba7abeee82f257dd1f4f90
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110903"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="c589b-103">Samoobslužné gRPC aplikace</span><span class="sxs-lookup"><span data-stu-id="c589b-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="c589b-104">Přestože ASP.NET aplikace Core 3.0 mohou být hostovány ve službě IIS v systému Windows Server, v současné době není možné hostovat aplikaci gRPC ve službě IIS, protože některé funkce HTTP/2 nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="c589b-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="c589b-105">Tato funkce je cílem budoucí aktualizace systému Windows Server.</span><span class="sxs-lookup"><span data-stu-id="c589b-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="c589b-106">Aplikaci můžete spustit jako službu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c589b-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="c589b-107">Nebo ji můžete spustit jako službu Linuxu řízenou [systemd](https://en.wikipedia.org/wiki/Systemd), protože nové funkce v rozšířeních .NET Core 3.0 hosting.</span><span class="sxs-lookup"><span data-stu-id="c589b-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="c589b-108">Spuštění aplikace jako služby Windows</span><span class="sxs-lookup"><span data-stu-id="c589b-108">Run your app as a Windows service</span></span>

<span data-ttu-id="c589b-109">Chcete-li nakonfigurovat ASP.NET základní aplikaci tak, aby běžela jako služba systému Windows, nainstalujte balíček [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) z NuGet.</span><span class="sxs-lookup"><span data-stu-id="c589b-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="c589b-110">Potom přidejte `UseWindowsService` volání `CreateHostBuilder` k `Program.cs`metodě v .</span><span class="sxs-lookup"><span data-stu-id="c589b-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="c589b-111">Pokud aplikace není spuštěna jako služba `UseWindowsService` systému Windows, metoda neprovádí nic.</span><span class="sxs-lookup"><span data-stu-id="c589b-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="c589b-112">Nyní publikujte aplikaci pomocí jedné z těchto metod:</span><span class="sxs-lookup"><span data-stu-id="c589b-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="c589b-113">Z Visual Studia kliknutím pravým tlačítkem myši na projekt a výběrem **publikovat** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="c589b-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="c589b-114">Z rozhraní .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="c589b-114">From the .NET Core CLI.</span></span>

<span data-ttu-id="c589b-115">Při publikování aplikace .NET Core můžete vytvořit nasazení *závislé na rozhraní* nebo *samostatné* nasazení.</span><span class="sxs-lookup"><span data-stu-id="c589b-115">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="c589b-116">Nasazení závislá na rozhraní vyžadují, aby byl sdílený runtime .NET Core nainstalován na hostiteli, kde jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="c589b-116">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="c589b-117">Samostatná nasazení jsou publikována s úplnou kopií runtime a frameworku .NET Core a lze je spustit na libovolném hostiteli.</span><span class="sxs-lookup"><span data-stu-id="c589b-117">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="c589b-118">Další informace, včetně výhod a nevýhod každého přístupu, naleznete v dokumentaci [k nasazení aplikace .NET Core.](../../core/deploying/index.md)</span><span class="sxs-lookup"><span data-stu-id="c589b-118">For more information, including the advantages and disadvantages of each approach, see the [.NET Core application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="c589b-119">Chcete-li publikovat samostatné sestavení aplikace, která nevyžaduje instalaci runtime .NET Core 3.0 na hostiteli, zadejte dobu runtime, která má být součástí aplikace.</span><span class="sxs-lookup"><span data-stu-id="c589b-119">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="c589b-120">Použijte `-r` příznak `--runtime`(nebo).</span><span class="sxs-lookup"><span data-stu-id="c589b-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="c589b-121">Chcete-li publikovat sestavení závislé na `-r` rámci, vyneche příznak.</span><span class="sxs-lookup"><span data-stu-id="c589b-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="c589b-122">Zkopírujte celý obsah `publish` adresáře do instalační složky.</span><span class="sxs-lookup"><span data-stu-id="c589b-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="c589b-123">Potom pomocí [nástroje sc](/windows/desktop/services/controlling-a-service-using-sc) vytvořte službu systému Windows pro spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="c589b-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="c589b-124">Protokolovat do protokolu událostí systému Windows</span><span class="sxs-lookup"><span data-stu-id="c589b-124">Log to the Windows event log</span></span>

<span data-ttu-id="c589b-125">Metoda `UseWindowsService` automaticky přidá [zprostředkovatele protokolování,](/aspnet/core/fundamentals/logging/) který zapisuje zprávy protokolu do protokolu událostí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c589b-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="c589b-126">Protokolování tohoto zprostředkovatele můžete `EventLog` nakonfigurovat `Logging` přidáním `appsettings.json` položky do oddílu nebo jiného zdroje konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c589b-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span>

<span data-ttu-id="c589b-127">Název zdroje použitý v protokolu událostí můžete přepsat `SourceName` nastavením vlastnosti v těchto nastaveních.</span><span class="sxs-lookup"><span data-stu-id="c589b-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="c589b-128">Pokud název nezadáte, bude použit výchozí název aplikace (obvykle název spustitelného sestavení).</span><span class="sxs-lookup"><span data-stu-id="c589b-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="c589b-129">Více informací o protokolování je na konci této kapitoly.</span><span class="sxs-lookup"><span data-stu-id="c589b-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="c589b-130">Spusťte aplikaci jako službu Linuxu s systemd</span><span class="sxs-lookup"><span data-stu-id="c589b-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="c589b-131">Chcete-li nakonfigurovat aplikaci ASP.NET Core tak, aby běžela jako služba Linuxu (nebo *daemon* v jazyce Linuxu), nainstalujte balíček [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) z NuGet.</span><span class="sxs-lookup"><span data-stu-id="c589b-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="c589b-132">Potom přidejte `UseSystemd` volání `CreateHostBuilder` k `Program.cs`metodě v .</span><span class="sxs-lookup"><span data-stu-id="c589b-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="c589b-133">Pokud aplikace není spuštěna jako služba `UseSystemd` Linuxu, metoda neprovádí nic.</span><span class="sxs-lookup"><span data-stu-id="c589b-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="c589b-134">Nyní publikujte svou žádost.</span><span class="sxs-lookup"><span data-stu-id="c589b-134">Now publish your application.</span></span> <span data-ttu-id="c589b-135">Aplikace může být závislá na rámci nebo samostatně obsažená pro příslušný `linux-x64`linuxový runtime (například).</span><span class="sxs-lookup"><span data-stu-id="c589b-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="c589b-136">Publikovat můžete pomocí jedné z těchto metod:</span><span class="sxs-lookup"><span data-stu-id="c589b-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="c589b-137">Z Visual Studia kliknutím pravým tlačítkem myši na projekt a výběrem **publikovat** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="c589b-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="c589b-138">Z rozhraní příkazového příkazu .NET Core pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="c589b-138">From the .NET Core CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
<span data-ttu-id="c589b-139">Zkopírujte celý obsah `publish` adresáře do instalační složky na hostiteli Linuxu.</span><span class="sxs-lookup"><span data-stu-id="c589b-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="c589b-140">Registrace služby vyžaduje přidání do *unit file* `/etc/systemd/system` adresáře speciální soubor nazývaný soubor jednotky .</span><span class="sxs-lookup"><span data-stu-id="c589b-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="c589b-141">K vytvoření souboru v této složce budete potřebovat oprávnění root.</span><span class="sxs-lookup"><span data-stu-id="c589b-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="c589b-142">Pojmenujte soubor identifikátorem, `systemd` který chcete `.service` použít, a příponou.</span><span class="sxs-lookup"><span data-stu-id="c589b-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="c589b-143">Použijte například `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="c589b-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="c589b-144">Soubor služby používá formát INI, jak je znázorněno v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="c589b-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="c589b-145">Vlastnost `Type=notify` říká, `systemd` že aplikace ji upozorní na spuštění a vypnutí.</span><span class="sxs-lookup"><span data-stu-id="c589b-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="c589b-146">Nastavení `WantedBy=multi-user.target` způsobí spuštění služby, když systém Linux dosáhne "runlevel 2", což znamená, že je aktivní negrafické prostředí pro více uživatelů.</span><span class="sxs-lookup"><span data-stu-id="c589b-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical, multi-user shell is active.</span></span>

<span data-ttu-id="c589b-147">Předtím, než `systemd` rozpozná službu, je třeba znovu načíst jeho konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c589b-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="c589b-148">Řízení `systemd` pomocí příkazu. `systemctl`</span><span class="sxs-lookup"><span data-stu-id="c589b-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="c589b-149">Po opětovném načtení použijte `status` podpříkaz k potvrzení, že aplikace byla úspěšně zaregistrována.</span><span class="sxs-lookup"><span data-stu-id="c589b-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="c589b-150">Pokud jste službu nakonfigurovali správně, získáte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c589b-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="c589b-151">Ke `start` spuštění služby použijte příkaz.</span><span class="sxs-lookup"><span data-stu-id="c589b-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="c589b-152">Rozšíření `.service` je volitelné, pokud `systemctl start`používáte .</span><span class="sxs-lookup"><span data-stu-id="c589b-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="c589b-153">Chcete-li spustit `systemd` službu automaticky při `enable` spuštění systému, použijte příkaz.</span><span class="sxs-lookup"><span data-stu-id="c589b-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="c589b-154">Protokolovat do deníku</span><span class="sxs-lookup"><span data-stu-id="c589b-154">Log to journald</span></span>

<span data-ttu-id="c589b-155">Linuxový ekvivalent protokolu událostí `journald`systému Windows je strukturovaná systémová `systemd`služba protokolování, která je součástí aplikace .</span><span class="sxs-lookup"><span data-stu-id="c589b-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="c589b-156">Protokolovat zprávy zapsané do standardního výstupu linuxovým `journald`daemonem jsou automaticky zapsány do aplikace .</span><span class="sxs-lookup"><span data-stu-id="c589b-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="c589b-157">Chcete-li konfigurovat úrovně `Console` protokolování, použijte část konfigurace protokolování.</span><span class="sxs-lookup"><span data-stu-id="c589b-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="c589b-158">Metoda `UseSystemd` tvůrce hostitelů automaticky konfiguruje výstupní formát konzoly tak, aby vyhovoval deníku.</span><span class="sxs-lookup"><span data-stu-id="c589b-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="c589b-159">Vzhledem k tomu, `journald` že je standardem pro protokoly Linux, různé nástroje integrovat s ním.</span><span class="sxs-lookup"><span data-stu-id="c589b-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="c589b-160">Protokoly můžete snadno `journald` směrovat do externího systému protokolování.</span><span class="sxs-lookup"><span data-stu-id="c589b-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="c589b-161">Pracovat místně na hostiteli, můžete `journalctl` použít příkaz k zobrazení protokolů z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c589b-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="c589b-162">Pokud máte na hostiteli k dispozici prostředí GUI, je k dispozici několik grafických prohlížečů protokolů pro Linux, jako jsou *QJournalctl* a *gnome-logs*.</span><span class="sxs-lookup"><span data-stu-id="c589b-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="c589b-163">Další informace o dotazování `systemd` deníku z příkazového řádku pomocí naleznete `journalctl`na stránkách [.](https://manpages.debian.org/buster/systemd/journalctl.1)</span><span class="sxs-lookup"><span data-stu-id="c589b-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the manpages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="c589b-164">Certifikáty HTTPS pro samoobslužné aplikace</span><span class="sxs-lookup"><span data-stu-id="c589b-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="c589b-165">Pokud v produkčním provozu používáte aplikaci gRPC, měli byste použít certifikát TLS od důvěryhodné certifikační autority (CA).</span><span class="sxs-lookup"><span data-stu-id="c589b-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="c589b-166">Tato certifikační autorita může být veřejná certifikační autorita nebo interní certifikační autorita pro vaši organizaci.</span><span class="sxs-lookup"><span data-stu-id="c589b-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="c589b-167">Na hostitelích systému Windows můžete certifikát načíst <xref:System.Security.Cryptography.X509Certificates.X509Store> z úložiště zabezpečených [certifikátů](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="c589b-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="c589b-168">Třídu `X509Store` můžete také použít s úložištěm klíčů OpenSSL na některých hostitelích Linuxu.</span><span class="sxs-lookup"><span data-stu-id="c589b-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="c589b-169">Certifikáty můžete také vytvořit pomocí jednoho z [konstruktorů X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), a to buď z následujících:</span><span class="sxs-lookup"><span data-stu-id="c589b-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="c589b-170">Soubor, například `.pfx` soubor chráněný silným heslem</span><span class="sxs-lookup"><span data-stu-id="c589b-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="c589b-171">Binární data načtená ze služby zabezpečeného úložiště, jako je [azure key vault](https://azure.microsoft.com/services/key-vault/)</span><span class="sxs-lookup"><span data-stu-id="c589b-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="c589b-172">Kestrel můžete nakonfigurovat tak, aby používal certifikát dvěma způsoby: z konfigurace nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="c589b-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="c589b-173">Nastavení certifikátů HTTPS pomocí konfigurace</span><span class="sxs-lookup"><span data-stu-id="c589b-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="c589b-174">Konfigurační přístup vyžaduje nastavení `.pfx` cesty k souboru certifikátu a hesla v části konfigurace kestrelu.</span><span class="sxs-lookup"><span data-stu-id="c589b-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="c589b-175">V `appsettings.json`, které by vypadaly takto:</span><span class="sxs-lookup"><span data-stu-id="c589b-175">In `appsettings.json`, that would look like this:</span></span>

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

<span data-ttu-id="c589b-176">Zadejte heslo pomocí zabezpečeného konfiguračního zdroje, jako je Azure Key Vault nebo Hashicorp Vault.</span><span class="sxs-lookup"><span data-stu-id="c589b-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c589b-177">Neuklápejte nešifrovaná hesla do konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="c589b-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="c589b-178">Nastavení certifikátů HTTPS v kódu</span><span class="sxs-lookup"><span data-stu-id="c589b-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="c589b-179">Chcete-li nakonfigurovat protokol HTTPS na `ConfigureKestrel` kestrelu v kódu, použijte metodu ve `IWebHostBuilder` `Program` třídě.</span><span class="sxs-lookup"><span data-stu-id="c589b-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="c589b-180">Opět nezapomeňte uložit heslo pro `.pfx` soubor a načíst z zabezpečeného konfiguračního zdroje.</span><span class="sxs-lookup"><span data-stu-id="c589b-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c589b-181">[Předchozí](grpc-in-production.md)
>[další](docker.md)</span><span class="sxs-lookup"><span data-stu-id="c589b-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
