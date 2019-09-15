---
title: Zabezpečení vlastních vazeb
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: b0b293c58e13f7add6f2cb49ea3c108a86292691
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990012"
---
# <a name="custom-binding-security"></a><span data-ttu-id="ad4b5-102">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="ad4b5-102">Custom Binding Security</span></span>

<span data-ttu-id="ad4b5-103">Tato ukázka demonstruje, jak nakonfigurovat zabezpečení pomocí vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="ad4b5-104">Ukazuje, jak použít vlastní vazbu k povolení zabezpečení na úrovni zprávy společně se zabezpečeným přenosem.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="ad4b5-105">To je užitečné, když zabezpečený přenos vyžaduje k přenosu zpráv mezi klientem a službou a současně musí být zprávy na úrovni zprávy zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="ad4b5-106">Tato konfigurace není podporována vazbami poskytovanými systémem.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-106">This configuration is not supported by system-provided bindings.</span></span>

<span data-ttu-id="ad4b5-107">Tato ukázka se skládá z klientského konzolového programu (EXE) a programu Service Console (EXE).</span><span class="sxs-lookup"><span data-stu-id="ad4b5-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="ad4b5-108">Služba implementuje oboustranný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-108">The service implements a duplex contract.</span></span> <span data-ttu-id="ad4b5-109">Kontrakt je definován `ICalculatorDuplex` rozhraním, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení).</span><span class="sxs-lookup"><span data-stu-id="ad4b5-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="ad4b5-110">`ICalculatorDuplex` Rozhraní umožňuje klientovi provádět matematické operace a vypočítat běžící výsledek během relace.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="ad4b5-111">Nezávisle, služba může vracet výsledky na `ICalculatorDuplexCallback` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="ad4b5-112">Duplexní smlouva vyžaduje relaci, protože je nutné vytvořit kontext, který bude korelovat sadu zpráv odesílaných mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="ad4b5-113">Vlastní vazba je definována, která podporuje duplexní komunikaci a je zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-113">A custom binding is defined that supports duplex communication and is secure.</span></span>

> [!NOTE]
> <span data-ttu-id="ad4b5-114">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="ad4b5-115">Konfigurace služby definuje vlastní vazbu, která podporuje následující:</span><span class="sxs-lookup"><span data-stu-id="ad4b5-115">The service configuration defines a custom binding that supports the following:</span></span>

- <span data-ttu-id="ad4b5-116">Komunikace TCP chráněná pomocí protokolu TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-116">TCP communication protected by using the TLS/SSL protocol.</span></span>

- <span data-ttu-id="ad4b5-117">Zabezpečení zpráv Windows.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-117">Windows message security.</span></span>

<span data-ttu-id="ad4b5-118">Vlastní konfigurace vazeb umožňuje zabezpečenou přenos současně s povolením zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="ad4b5-119">Řazení elementů vazby je důležité při definování vlastní vazby, protože každá představuje vrstvu v zásobníku kanálů (viz [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="ad4b5-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="ad4b5-120">Vlastní vazba je definována v konfiguračních souborech služby a klienta, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>

```xml
<bindings>
  <!-- Configure a custom binding. -->
  <customBinding>
    <binding name="Binding1">
      <security authenticationMode="SecureConversation"
                 requireSecurityContextCancellation="true">
      </security>
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>
      <sslStreamSecurity requireClientCertificate="false"/>
      <tcpTransport/>
    </binding>
  </customBinding>
</bindings>
```

<span data-ttu-id="ad4b5-121">Vlastní vazba používá k ověření služby na úrovni přenosu certifikát služby a chrání zprávy během přenosu mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="ad4b5-122">To je dosaženo `sslStreamSecurity` prvkem vazby.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="ad4b5-123">Certifikát služby je nakonfigurovaný pomocí chování služby, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
        <serviceMetadata />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>
        </serviceCredentials>
    </behavior>
    </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="ad4b5-124">Navíc vlastní vazba používá zabezpečení zpráv s typem přihlašovacích údajů systému Windows – jedná se o výchozí typ přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="ad4b5-125">To je dosaženo `security` prvkem vazby.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="ad4b5-126">Klient i služba jsou ověřovány pomocí zabezpečení na úrovni zpráv, pokud je k dispozici mechanismus ověřování protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="ad4b5-127">K tomu dojde, pokud je ukázka spuštěna v prostředí služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="ad4b5-128">Pokud ověřovací mechanismus protokolu Kerberos není k dispozici, použije se ověřování NTLM.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="ad4b5-129">Protokol NTLM ověřuje klienta služby, ale neověřuje službu klientovi.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="ad4b5-130">Prvek vazby je nakonfigurován tak, aby `SecureConversation` používal `authenticationType`, což vede k vytvoření relace zabezpečení v klientovi i ve službě. `security`</span><span class="sxs-lookup"><span data-stu-id="ad4b5-130">The `security` binding element is configured to use `SecureConversation` `authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="ad4b5-131">Tato možnost je nutná k tomu, aby fungovala činnost duplexního kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-131">This is required to enable the service's duplex contract to work.</span></span>

<span data-ttu-id="ad4b5-132">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="ad4b5-133">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-133">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

<span data-ttu-id="ad4b5-134">Při spuštění ukázky se zobrazí zprávy vracené klientovi do rozhraní zpětného volání odeslaného ze služby.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="ad4b5-135">Po dokončení všech operací se zobrazí každý mezilehlé výsledek následovaný celým vzorcem.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="ad4b5-136">Pro vypnutí klienta stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-136">Press ENTER to shut down the client.</span></span>

<span data-ttu-id="ad4b5-137">Zahrnutý soubor Setup. bat vám umožní nakonfigurovat klienta a server s příslušným certifikátem služby pro spuštění hostované aplikace, která vyžaduje zabezpečení na základě certifikátů.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="ad4b5-138">Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

<span data-ttu-id="ad4b5-139">Níže najdete stručný přehled různých částí dávkových souborů, které se vztahují k této ukázce, aby je bylo možné upravit tak, aby se spouštěly v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="ad4b5-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="ad4b5-140">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-140">Creating the server certificate.</span></span>

  <span data-ttu-id="ad4b5-141">Následující řádky ze souboru Setup. bat vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="ad4b5-142">`%SERVER_NAME%` Proměnná Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="ad4b5-143">Změňte tuto proměnnou tak, aby určovala vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="ad4b5-144">Tento soubor dávky nastaví název serveru na localhost.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-144">This batch file defaults the server name to localhost.</span></span>

  <span data-ttu-id="ad4b5-145">Certifikát je uložený v úložišti CurrentUser pro služby hostované na webu.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>

  ```bat
  echo ************
  echo Server cert setup starting
  echo %SERVER_NAME%
  echo ************
  echo making server cert
  echo ************
  makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
  ```

- <span data-ttu-id="ad4b5-146">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-146">Installing the server certificate into the client's trusted certificate store.</span></span>

  <span data-ttu-id="ad4b5-147">Následující řádky v souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ad4b5-148">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ad4b5-149">Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

  ```console
  certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
  ```

  > [!NOTE]
  > <span data-ttu-id="ad4b5-150">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="ad4b5-151">Vyžaduje, aby proměnná prostředí MSSDK odkazovala na adresář, ve kterém je sada SDK nainstalována.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="ad4b5-152">Tato proměnná prostředí se automaticky nastaví v rámci příkazového řádku sady Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ad4b5-153">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="ad4b5-153">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ad4b5-154">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ad4b5-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ad4b5-155">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ad4b5-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="ad4b5-156">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ad4b5-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="ad4b5-157">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="ad4b5-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="ad4b5-158">Otevřete okno Developer Command Prompt pro Visual Studio s oprávněními správce a spusťte Setup. bat z ukázkové instalační složky.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-158">Open a Developer Command Prompt for Visual Studio window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="ad4b5-159">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-159">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ad4b5-160">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="ad4b5-161">Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

2. <span data-ttu-id="ad4b5-162">Spustit Service. exe z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-162">Launch Service.exe from \service\bin.</span></span>

3. <span data-ttu-id="ad4b5-163">Spustit soubor Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="ad4b5-164">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-164">Client activity is displayed on the client console application.</span></span>

4. <span data-ttu-id="ad4b5-165">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ad4b5-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="ad4b5-166">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="ad4b5-166">To run the sample across computers</span></span>

1. <span data-ttu-id="ad4b5-167">Na počítači služby:</span><span class="sxs-lookup"><span data-stu-id="ad4b5-167">On the service computer:</span></span>

    1. <span data-ttu-id="ad4b5-168">Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>

    2. <span data-ttu-id="ad4b5-169">Zkopírujte programové soubory služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="ad4b5-170">Ujistěte se, že jste zkopírovali soubory do podadresáře \Bin.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-170">Ensure that you copy the files in the \bin subdirectory.</span></span>

    3. <span data-ttu-id="ad4b5-171">Zkopírujte soubory Setup. bat a Cleanup. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>

    4. <span data-ttu-id="ad4b5-172">Spusťte následující příkaz v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce: `Setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-172">Run the following command in a Developer Command Prompt for Visual Studio opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="ad4b5-173">Tím se vytvoří certifikát služby s názvem subjektu, který odpovídá názvu počítače, ve kterém byl dávkový soubor spuštěn.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>

        > [!NOTE]
        > <span data-ttu-id="ad4b5-174">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="ad4b5-175">Vyžaduje, aby proměnná prostředí PATH odkazovala na adresář, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="ad4b5-176">Tato proměnná prostředí se automaticky nastaví v rámci příkazového řádku sady Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

    5. <span data-ttu-id="ad4b5-177">Změňte > serviceCertificate v souboru Service. exe. config tak, aby odrážela název subjektu certifikátu vygenerovaného v předchozím kroku. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="ad4b5-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>

    6. <span data-ttu-id="ad4b5-178">Spusťte Service. exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-178">Run Service.exe from a command prompt.</span></span>

2. <span data-ttu-id="ad4b5-179">V klientském počítači:</span><span class="sxs-lookup"><span data-stu-id="ad4b5-179">On the client computer:</span></span>

    1. <span data-ttu-id="ad4b5-180">Zkopírujte soubory klientského programu ze složky \client\bin\ do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="ad4b5-181">Zkopírujte také soubor Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-181">Also copy the Cleanup.bat file.</span></span>

    2. <span data-ttu-id="ad4b5-182">Spuštěním nástroje CleanUp. bat odeberte všechny staré certifikáty z předchozích ukázek.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>

    3. <span data-ttu-id="ad4b5-183">Exportujte certifikát služby otevřením Developer Command Prompt pro sadu Visual Studio s oprávněními správce a spuštěním následujícího příkazu na počítači služby (nahraďte `%SERVER_NAME%` plně kvalifikovaným názvem počítače, kde Služba je spuštěná):</span><span class="sxs-lookup"><span data-stu-id="ad4b5-183">Export the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>

        ```console
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. <span data-ttu-id="ad4b5-184">Zkopírujte% název_serveru%. cer do klientského počítače (nahraďte% název_serveru% plně kvalifikovaným názvem počítače, ve kterém je služba spuštěná).</span><span class="sxs-lookup"><span data-stu-id="ad4b5-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>

    5. <span data-ttu-id="ad4b5-185">Importujte certifikát služby otevřením Developer Command Prompt pro sadu Visual Studio s oprávněními správce a spuštěním následujícího příkazu v klientském počítači (nahraďte% název_serveru% plně kvalifikovaným názvem počítače, kde Služba je spuštěná):</span><span class="sxs-lookup"><span data-stu-id="ad4b5-185">Import the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>

        ```console
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

        <span data-ttu-id="ad4b5-186">Postup c, d a e není nutný, pokud certifikát vystavuje důvěryhodný Vystavitel.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>

    6. <span data-ttu-id="ad4b5-187">Upravte soubor App. config klienta následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ad4b5-187">Modify the client’s App.config file as follows:</span></span>

        ```xml
        <client>
            <endpoint name="default"
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"
                binding="customBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"
                behaviorConfiguration="CalculatorClientBehavior" />
        </client>
        ```

    7. <span data-ttu-id="ad4b5-188">Pokud je služba spuštěná pod jiným účtem než účtem NetworkService nebo LocalSystem v doménovém prostředí, možná budete muset změnit identitu koncového bodu pro koncový bod služby v souboru App. config klienta k nastavení příslušného hlavního názvu uživatele (UPN) nebo hlavního názvu služby (SPN). na účtu, který se používá ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="ad4b5-189">Další informace o identitě koncového bodu najdete v tématu [identita služby a ověřování](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) .</span><span class="sxs-lookup"><span data-stu-id="ad4b5-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>

    8. <span data-ttu-id="ad4b5-190">Spusťte soubor Client. exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-190">Run Client.exe from a command prompt.</span></span>

### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ad4b5-191">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="ad4b5-191">To clean up after the sample</span></span>

- <span data-ttu-id="ad4b5-192">Po dokončení ukázky Spusťte Cleanup. bat ve složce Samples.</span><span class="sxs-lookup"><span data-stu-id="ad4b5-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>
