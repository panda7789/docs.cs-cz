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
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="14470-103">Samoobslužné aplikace gRPC</span><span class="sxs-lookup"><span data-stu-id="14470-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="14470-104">I když je možné aplikace ASP.NET Core 3,0 hostovat ve službě IIS na Windows serveru, v současné době není možné hostovat aplikaci gRPC ve službě IIS, protože některé funkce HTTP/2 se nepodporují.</span><span class="sxs-lookup"><span data-stu-id="14470-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="14470-105">Tato funkce je cílem budoucí aktualizace Windows serveru.</span><span class="sxs-lookup"><span data-stu-id="14470-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="14470-106">Aplikaci můžete spustit jako službu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="14470-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="14470-107">Nebo ho můžete spustit jako službu Linux řízenou [systémem](https://en.wikipedia.org/wiki/Systemd), protože v rozšířeních hostování .net Core 3,0 jsou nové funkce.</span><span class="sxs-lookup"><span data-stu-id="14470-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="14470-108">Spuštění aplikace jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="14470-108">Run your app as a Windows service</span></span>

<span data-ttu-id="14470-109">Chcete-li nakonfigurovat aplikaci ASP.NET Core tak, aby běžela jako služba systému Windows, nainstalujte balíček [Microsoft. Extensions. Hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) z nástroje NuGet.</span><span class="sxs-lookup"><span data-stu-id="14470-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="14470-110">Pak přidejte volání `UseWindowsService` do metody `CreateHostBuilder` v `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="14470-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="14470-111">Pokud aplikace není spuštěna jako služba systému Windows, `UseWindowsService` metoda neprovede žádné akce.</span><span class="sxs-lookup"><span data-stu-id="14470-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="14470-112">Nyní můžete aplikaci publikovat pomocí jedné z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="14470-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="14470-113">V aplikaci Visual Studio kliknutím pravým tlačítkem myši na projekt a výběrem možnosti **publikovat** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="14470-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="14470-114">Z .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="14470-114">From the .NET Core CLI.</span></span>

<span data-ttu-id="14470-115">Při publikování aplikace .NET Core se můžete rozhodnout pro vytvoření nasazení *závislého na rozhraní* nebo *samostatného* nasazení.</span><span class="sxs-lookup"><span data-stu-id="14470-115">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="14470-116">Nasazení závislá na rozhraní vyžadují, aby byl na hostiteli, na kterém je spuštěný, nainstalovaný sdílený modul .NET Core Shared.</span><span class="sxs-lookup"><span data-stu-id="14470-116">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="14470-117">Samostatně obsažená nasazení jsou publikována s úplnou kopií modulu runtime .NET Core a architekturou a lze ji spustit na jakémkoli hostiteli.</span><span class="sxs-lookup"><span data-stu-id="14470-117">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="14470-118">Další informace, včetně výhod a nevýhod každého přístupu, naleznete v dokumentaci k [nasazení aplikace .NET Core](../../core/deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="14470-118">For more information, including the advantages and disadvantages of each approach, see the [.NET Core application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="14470-119">Chcete-li publikovat samostatné sestavení aplikace, které nevyžaduje instalaci modulu runtime .NET Core 3,0 na hostitele, zadejte modul runtime, který bude součástí aplikace.</span><span class="sxs-lookup"><span data-stu-id="14470-119">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="14470-120">Použijte příznak `-r` (nebo `--runtime`).</span><span class="sxs-lookup"><span data-stu-id="14470-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="14470-121">Chcete-li publikovat sestavení závislé na rozhraní, vynechejte příznak `-r`.</span><span class="sxs-lookup"><span data-stu-id="14470-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="14470-122">Zkopírujte celý obsah adresáře `publish` do instalační složky.</span><span class="sxs-lookup"><span data-stu-id="14470-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="14470-123">Pak pomocí [Nástroje SC](/windows/desktop/services/controlling-a-service-using-sc) vytvořte službu systému Windows pro spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="14470-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="14470-124">Přihlášení do protokolu událostí systému Windows</span><span class="sxs-lookup"><span data-stu-id="14470-124">Log to the Windows event log</span></span>

<span data-ttu-id="14470-125">Metoda `UseWindowsService` automaticky přidá poskytovatele [protokolování](/aspnet/core/fundamentals/logging/) , který zapíše zprávy protokolu do protokolu událostí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="14470-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="14470-126">Protokolování pro tohoto zprostředkovatele můžete nakonfigurovat přidáním položky `EventLog` do oddílu `Logging` `appsettings.json` nebo jiného zdroje konfigurace.</span><span class="sxs-lookup"><span data-stu-id="14470-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span> 

<span data-ttu-id="14470-127">Název zdroje použitý v protokolu událostí můžete přepsat nastavením vlastnosti `SourceName` v těchto nastaveních.</span><span class="sxs-lookup"><span data-stu-id="14470-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="14470-128">Pokud název nezadáte, použije se výchozí název aplikace (obvykle se jedná o spustitelný název sestavení).</span><span class="sxs-lookup"><span data-stu-id="14470-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="14470-129">Další informace o protokolování najdete na konci této kapitoly.</span><span class="sxs-lookup"><span data-stu-id="14470-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="14470-130">Spuštění aplikace jako služby pro Linux se systémem</span><span class="sxs-lookup"><span data-stu-id="14470-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="14470-131">Pokud chcete svou aplikaci ASP.NET Core nakonfigurovat tak, aby běžela jako služba pro Linux (nebo *démon* v systému Linux agilním), nainstalujte balíček [Microsoft. Extensions. Hosting. systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) z NuGet.</span><span class="sxs-lookup"><span data-stu-id="14470-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="14470-132">Pak přidejte volání `UseSystemd` do metody `CreateHostBuilder` v `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="14470-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="14470-133">Pokud aplikace není spuštěna jako služba pro Linux, `UseSystemd` metoda neprovede žádné akce.</span><span class="sxs-lookup"><span data-stu-id="14470-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="14470-134">Nyní publikujte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="14470-134">Now publish your application.</span></span> <span data-ttu-id="14470-135">Aplikace může být buď závislá na architektuře, nebo samostatná jako pro příslušné prostředí Linux runtime (například `linux-x64`).</span><span class="sxs-lookup"><span data-stu-id="14470-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="14470-136">Můžete publikovat pomocí jedné z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="14470-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="14470-137">V aplikaci Visual Studio kliknutím pravým tlačítkem myši na projekt a výběrem možnosti **publikovat** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="14470-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span> 
* <span data-ttu-id="14470-138">Z .NET Core CLI pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="14470-138">From the .NET Core CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
<span data-ttu-id="14470-139">Zkopírujte celý obsah adresáře `publish` do instalační složky na hostiteli se systémem Linux.</span><span class="sxs-lookup"><span data-stu-id="14470-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="14470-140">Registrace služby vyžaduje speciální soubor nazvaný *soubor jednotky*, který bude přidán do adresáře `/etc/systemd/system`.</span><span class="sxs-lookup"><span data-stu-id="14470-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="14470-141">K vytvoření souboru v této složce budete potřebovat oprávnění root.</span><span class="sxs-lookup"><span data-stu-id="14470-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="14470-142">Pojmenujte soubor s identifikátorem, který chcete použít `systemd` a rozšířením `.service`.</span><span class="sxs-lookup"><span data-stu-id="14470-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="14470-143">Použijte například `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="14470-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="14470-144">Soubor služby používá formát INI, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="14470-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="14470-145">Vlastnost `Type=notify` oznamuje `systemd`, že ji aplikace upozorní na spuštění a vypnutí.</span><span class="sxs-lookup"><span data-stu-id="14470-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="14470-146">Nastavení `WantedBy=multi-user.target` způsobí, že se služba spustí, když systém Linux dosáhne "runlevel 2", což znamená, že je aktivní negrafické prostředí pro více uživatelů.</span><span class="sxs-lookup"><span data-stu-id="14470-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical multi-user shell is active.</span></span>

<span data-ttu-id="14470-147">Předtím, než `systemd` rozpozná službu, musí znovu načíst konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="14470-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="14470-148">`systemd` můžete ovládat pomocí příkazu `systemctl`.</span><span class="sxs-lookup"><span data-stu-id="14470-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="14470-149">Po opětovném načtení pomocí dílčího příkazu `status` potvrďte, že se aplikace úspěšně zaregistrovala.</span><span class="sxs-lookup"><span data-stu-id="14470-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="14470-150">Pokud jste službu správně nakonfigurovali, získáte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="14470-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="14470-151">Službu spusťte pomocí příkazu `start`.</span><span class="sxs-lookup"><span data-stu-id="14470-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="14470-152">Rozšíření `.service` je při použití `systemctl start`volitelné.</span><span class="sxs-lookup"><span data-stu-id="14470-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="14470-153">Chcete-li sdělit `systemd`, aby se služba automaticky spouštěla při spuštění systému, použijte příkaz `enable`.</span><span class="sxs-lookup"><span data-stu-id="14470-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="14470-154">Přihlášení do deníku</span><span class="sxs-lookup"><span data-stu-id="14470-154">Log to journald</span></span>

<span data-ttu-id="14470-155">Ekvivalent systému Linux v protokolu událostí Windows je `journald`, strukturované protokolovací služby protokolování, která je součástí `systemd`.</span><span class="sxs-lookup"><span data-stu-id="14470-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="14470-156">Protokolovat zprávy zapsané do standardního výstupu pomocí démona Linux se automaticky zapisují do `journald`.</span><span class="sxs-lookup"><span data-stu-id="14470-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="14470-157">Chcete-li nakonfigurovat úrovně protokolování, použijte část `Console` v konfiguraci protokolování.</span><span class="sxs-lookup"><span data-stu-id="14470-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="14470-158">Metoda `UseSystemd` Host Builder automaticky konfiguruje výstupní formát konzoly tak, aby odpovídaly deníku.</span><span class="sxs-lookup"><span data-stu-id="14470-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="14470-159">Vzhledem k tomu, že `journald` je standard pro protokoly Linux, je k tomu integrovaná celá řada nástrojů.</span><span class="sxs-lookup"><span data-stu-id="14470-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="14470-160">Protokoly můžete snadno směrovat z `journald` do externího systému protokolování.</span><span class="sxs-lookup"><span data-stu-id="14470-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="14470-161">Místně pracujete na hostiteli pomocí příkazu `journalctl` k zobrazení protokolů z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="14470-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="14470-162">Pokud máte k dispozici prostředí GUI na vašem hostiteli, je pro Linux k dispozici několik grafických prohlížečů, jako jsou například *QJournalctl* a *GNOME-* log.</span><span class="sxs-lookup"><span data-stu-id="14470-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="14470-163">Další informace o dotazování deníku `systemd` z příkazového řádku pomocí `journalctl`najdete [na stránkách Man](https://manpages.debian.org/buster/systemd/journalctl.1).</span><span class="sxs-lookup"><span data-stu-id="14470-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the man pages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="14470-164">Certifikáty HTTPS pro samoobslužné aplikace</span><span class="sxs-lookup"><span data-stu-id="14470-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="14470-165">Pokud spouštíte aplikaci gRPC v produkčním prostředí, měli byste použít certifikát TLS od důvěryhodné certifikační autority (CA).</span><span class="sxs-lookup"><span data-stu-id="14470-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="14470-166">Tato certifikační autorita může být veřejná certifikační autoritou nebo interní pro vaši organizaci.</span><span class="sxs-lookup"><span data-stu-id="14470-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="14470-167">Na hostitelích se systémem Windows můžete načíst certifikát z zabezpečeného [úložiště certifikátů](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) pomocí třídy <xref:System.Security.Cryptography.X509Certificates.X509Store>.</span><span class="sxs-lookup"><span data-stu-id="14470-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="14470-168">Můžete také použít třídu `X509Store` s úložištěm klíčů OpenSSL na některých hostitelích se systémem Linux.</span><span class="sxs-lookup"><span data-stu-id="14470-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="14470-169">Můžete také vytvořit certifikáty pomocí jednoho z [konstruktorů X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), a to z těchto:</span><span class="sxs-lookup"><span data-stu-id="14470-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="14470-170">Soubor, například soubor `.pfx` chráněný silným heslem</span><span class="sxs-lookup"><span data-stu-id="14470-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="14470-171">Binární data načtená ze zabezpečené služby úložiště, jako je [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span><span class="sxs-lookup"><span data-stu-id="14470-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="14470-172">Kestrel můžete nakonfigurovat tak, aby používal certifikát dvěma způsoby: z konfigurace nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="14470-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="14470-173">Nastavení certifikátů HTTPS pomocí konfigurace</span><span class="sxs-lookup"><span data-stu-id="14470-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="14470-174">Konfigurační přístup vyžaduje nastavení cesty k souboru `.pfx` certifikátu a heslo v oddílu konfigurace Kestrel.</span><span class="sxs-lookup"><span data-stu-id="14470-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="14470-175">V `appsettings.json`by to vypadalo takto:</span><span class="sxs-lookup"><span data-stu-id="14470-175">In `appsettings.json`, that would look like this:</span></span>

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

<span data-ttu-id="14470-176">Zadejte heslo pomocí zabezpečeného zdroje konfigurace, například Azure Key Vault nebo trezoru Hashicorp.</span><span class="sxs-lookup"><span data-stu-id="14470-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="14470-177">V konfiguračních souborech neukládejte nešifrovaná hesla.</span><span class="sxs-lookup"><span data-stu-id="14470-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="14470-178">Nastavení certifikátů HTTPS v kódu</span><span class="sxs-lookup"><span data-stu-id="14470-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="14470-179">Chcete-li nakonfigurovat HTTPS na Kestrel v kódu, použijte metodu `ConfigureKestrel` pro `IWebHostBuilder` ve třídě `Program`.</span><span class="sxs-lookup"><span data-stu-id="14470-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="14470-180">Znovu nezapomeňte uložit heslo pro soubor `.pfx` v a načíst ho ze zabezpečeného zdroje konfigurace.</span><span class="sxs-lookup"><span data-stu-id="14470-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="14470-181">[Předchozí](grpc-in-production.md)
>[Další](docker.md)</span><span class="sxs-lookup"><span data-stu-id="14470-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
