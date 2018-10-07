---
title: Zabezpečení vlastních vazeb
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
author: BrucePerlerMS
ms.openlocfilehash: 85d069fed9fb1e82670c81003b5ef091c22a8e92
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841576"
---
# <a name="custom-binding-security"></a><span data-ttu-id="79c9d-102">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="79c9d-102">Custom Binding Security</span></span>
<span data-ttu-id="79c9d-103">Tento příklad ukazuje, jak nakonfigurovat zabezpečení a použití vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="79c9d-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="79c9d-104">Ukazuje, jak povolit zabezpečení na úrovni zprávy spolu s zabezpečeného přenosu pomocí vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="79c9d-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="79c9d-105">To je užitečné, když zabezpečeného přenosu je potřebná pro přenos zpráv mezi klientem a službou a současně zprávy musí být zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="79c9d-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="79c9d-106">Tato konfigurace není podporována vazeb poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="79c9d-106">This configuration is not supported by system-provided bindings.</span></span>

 <span data-ttu-id="79c9d-107">Tento příklad se skládá z programu konzoly klienta (EXE) a služby konzolový program (EXE).</span><span class="sxs-lookup"><span data-stu-id="79c9d-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="79c9d-108">Služba implementuje duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="79c9d-108">The service implements a duplex contract.</span></span> <span data-ttu-id="79c9d-109">Smlouva je definován `ICalculatorDuplex` rozhraní, které zveřejňuje matematických operací (Přidat odečíst, násobení a dělení).</span><span class="sxs-lookup"><span data-stu-id="79c9d-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="79c9d-110">`ICalculatorDuplex` Rozhraní umožňuje klientovi k provádění matematických operací spuštěných výsledek výpočtu přes relaci.</span><span class="sxs-lookup"><span data-stu-id="79c9d-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="79c9d-111">Nezávisle na sobě, mohou vracet výsledky na službu `ICalculatorDuplexCallback` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="79c9d-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="79c9d-112">Duplexní kontrakt vyžaduje relaci, protože kontextu musí být stanovena ke korelaci sadu zprávy odesílané mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="79c9d-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="79c9d-113">Vlastní vazby je definován, který podporuje duplexní komunikaci a je bezpečné.</span><span class="sxs-lookup"><span data-stu-id="79c9d-113">A custom binding is defined that supports duplex communication and is secure.</span></span>

> [!NOTE]
>  <span data-ttu-id="79c9d-114">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="79c9d-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="79c9d-115">Konfigurace služby definuje vlastní vazby, který podporuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="79c9d-115">The service configuration defines a custom binding that supports the following:</span></span>

-   <span data-ttu-id="79c9d-116">Komunikace protokolu TCP chráněny pomocí protokolu TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="79c9d-116">TCP communication protected by using the TLS/SSL protocol.</span></span>

-   <span data-ttu-id="79c9d-117">Zabezpečení zpráv Windows.</span><span class="sxs-lookup"><span data-stu-id="79c9d-117">Windows message security.</span></span>

 <span data-ttu-id="79c9d-118">Konfigurace vlastních vazeb umožňuje zabezpečeného přenosu současně povolením zprávy úroveň zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="79c9d-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="79c9d-119">Řazení elementů vazby je důležité při definování vlastní vazby, protože každý reprezentuje vrstvu v kanálu zásobníku (viz [vlastních vazeb](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="79c9d-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="79c9d-120">Vlastní vazba je definována v konfiguračních souborů klienta a služby, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="79c9d-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>

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

 <span data-ttu-id="79c9d-121">Vlastní vazba používá certifikát služby pro ověření služby na úrovni přenosu a k ochraně zprávy během přenosu mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="79c9d-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="79c9d-122">Toho lze dosáhnout `sslStreamSecurity` element vazby.</span><span class="sxs-lookup"><span data-stu-id="79c9d-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="79c9d-123">Certifikát služby je nakonfigurovaný pomocí chování služby, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="79c9d-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>

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

 <span data-ttu-id="79c9d-124">Kromě toho používá vlastní vazby zabezpečení zpráv s typ přihlašovacích údajů Windows – jedná se o výchozí typ přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="79c9d-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="79c9d-125">Toho lze dosáhnout `security` element vazby.</span><span class="sxs-lookup"><span data-stu-id="79c9d-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="79c9d-126">Klient a služba ověření pomocí zabezpečení na úrovni zprávy, když mechanismus ověřování protokolu Kerberos je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="79c9d-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="79c9d-127">To se stane, když spuštění ukázky v prostředí služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="79c9d-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="79c9d-128">Pokud mechanismus ověřování protokolu Kerberos není k dispozici, bude použito ověřování NTLM.</span><span class="sxs-lookup"><span data-stu-id="79c9d-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="79c9d-129">NTLM ověřuje klienta pro službu, ale neověří služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="79c9d-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="79c9d-130">`security` Element vazby je nakonfigurován na použití `SecureConversation``authenticationType`, což vede k vytvoření relace zabezpečení klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="79c9d-130">The `security` binding element is configured to use `SecureConversation``authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="79c9d-131">To je nutné povolit duplexního kontraktu služby pro práci.</span><span class="sxs-lookup"><span data-stu-id="79c9d-131">This is required to enable the service's duplex contract to work.</span></span>

 <span data-ttu-id="79c9d-132">Při spuštění ukázky operace žádosti a odpovědi jsou zobrazeny v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="79c9d-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="79c9d-133">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="79c9d-133">Press ENTER in the client window to shut down the client.</span></span>

```
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

 <span data-ttu-id="79c9d-134">Když spustíte ukázku, uvidíte zpráv vrácených do klienta na rozhraní zpětného volání odeslané ze služby.</span><span class="sxs-lookup"><span data-stu-id="79c9d-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="79c9d-135">Zobrazí se každý přechodný výsledek, za nímž následuje celou rovnici. Po dokončení všech operací.</span><span class="sxs-lookup"><span data-stu-id="79c9d-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="79c9d-136">Stiskněte klávesu ENTER pro vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="79c9d-136">Press ENTER to shut down the client.</span></span>

 <span data-ttu-id="79c9d-137">Zahrnutý soubor Setup.bat můžete nakonfigurovat klienta a serveru s certifikátem příslušné služby ke spuštění prostředí aplikace, které vyžadují zabezpečení na základě certifikátů.</span><span class="sxs-lookup"><span data-stu-id="79c9d-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="79c9d-138">Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.</span><span class="sxs-lookup"><span data-stu-id="79c9d-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="79c9d-139">Následující body nabízí stručný přehled o různých částech dávkové soubory, které se vztahují k této ukázce tak, aby se lze upravit a spustit v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="79c9d-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>

-   <span data-ttu-id="79c9d-140">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="79c9d-140">Creating the server certificate.</span></span>

     <span data-ttu-id="79c9d-141">Následující řádky z se soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="79c9d-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="79c9d-142">`%SERVER_NAME%` Proměnné Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="79c9d-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="79c9d-143">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="79c9d-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="79c9d-144">Tento dávkový soubor výchozí hodnota názvu serveru localhost.</span><span class="sxs-lookup"><span data-stu-id="79c9d-144">This batch file defaults the server name to localhost.</span></span>

     <span data-ttu-id="79c9d-145">Certifikát je uložen v úložišti CurrentUser pro hostované webové služby.</span><span class="sxs-lookup"><span data-stu-id="79c9d-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="79c9d-146">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="79c9d-146">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="79c9d-147">Uložte následující řádky v kopírování souborů Setup.bat certifikát serveru do klienta důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="79c9d-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="79c9d-148">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="79c9d-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="79c9d-149">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="79c9d-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="79c9d-150">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2010 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="79c9d-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="79c9d-151">To vyžaduje, aby proměnné prostředí MSSDK bodu do adresáře, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="79c9d-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="79c9d-152">Tato proměnná prostředí je nastavena automaticky v rámci Visual Studio 2010 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="79c9d-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="79c9d-153">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="79c9d-153">To set up, build, and run the sample</span></span>

1.  <span data-ttu-id="79c9d-154">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79c9d-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="79c9d-155">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79c9d-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3.  <span data-ttu-id="79c9d-156">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79c9d-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="79c9d-157">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="79c9d-157">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="79c9d-158">Otevřete okno Příkazový řádek sady Visual Studio s oprávněními správce a spusťte Setup.bat z instalační složky s ukázkou.</span><span class="sxs-lookup"><span data-stu-id="79c9d-158">Open a Visual Studio Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="79c9d-159">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="79c9d-159">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="79c9d-160">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="79c9d-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="79c9d-161">Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="79c9d-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="79c9d-162">Spusťte Service.exe z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="79c9d-162">Launch Service.exe from \service\bin.</span></span>  
  
3.  <span data-ttu-id="79c9d-163">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="79c9d-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="79c9d-164">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="79c9d-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="79c9d-165">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="79c9d-165">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="79c9d-166">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="79c9d-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="79c9d-167">Na počítači se službou:</span><span class="sxs-lookup"><span data-stu-id="79c9d-167">On the service computer:</span></span>  
  
    1.  <span data-ttu-id="79c9d-168">Vytvořte virtuální adresář s názvem servicemodelsamples na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="79c9d-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>  
  
    2.  <span data-ttu-id="79c9d-169">Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="79c9d-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="79c9d-170">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="79c9d-170">Ensure that you copy the files in the \bin subdirectory.</span></span>  
  
    3.  <span data-ttu-id="79c9d-171">Zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="79c9d-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
    4.  <span data-ttu-id="79c9d-172">Spuštění následujícího příkazu v příkazovém řádku aplikace Visual Studio otevřeného s oprávněními správce: `Setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="79c9d-172">Run the following command in a Visual Studio command prompt opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="79c9d-173">Tím se vytvoří certifikát služby s názvem subjektu odpovídající název počítače, který byl spuštěn dávkového souboru.</span><span class="sxs-lookup"><span data-stu-id="79c9d-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="79c9d-174">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2010 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="79c9d-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="79c9d-175">To vyžaduje, aby proměnné prostředí path v bodu do adresáře, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="79c9d-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="79c9d-176">Tato proměnná prostředí je nastavena automaticky v rámci Visual Studio 2010 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="79c9d-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

    5.  <span data-ttu-id="79c9d-177">Změnit [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) uvnitř Service.exe.config souboru tak, aby odrážely název subjektu certifikátu vygenerovaného v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="79c9d-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>

    6.  <span data-ttu-id="79c9d-178">Spusťte Service.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="79c9d-178">Run Service.exe from a command prompt.</span></span>

2.  <span data-ttu-id="79c9d-179">Na klientském počítači:</span><span class="sxs-lookup"><span data-stu-id="79c9d-179">On the client computer:</span></span>

    1.  <span data-ttu-id="79c9d-180">Zkopírujte soubory programu klienta ze složky \client\bin\ do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="79c9d-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="79c9d-181">Zkopírujte také soubor Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="79c9d-181">Also copy the Cleanup.bat file.</span></span>

    2.  <span data-ttu-id="79c9d-182">Spusťte Cleanup.bat odebrání starého certifikátů z předchozí ukázky.</span><span class="sxs-lookup"><span data-stu-id="79c9d-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>

    3.  <span data-ttu-id="79c9d-183">Exportujte certifikát služby tak, že otevřete příkazový řádek sady Visual Studio s oprávněními správce a spuštěním následujícího příkazu na počítači se službou (Nahraďte `%SERVER_NAME%` s plně kvalifikovaný název počítače, kde je služba spuštění):</span><span class="sxs-lookup"><span data-stu-id="79c9d-183">Export the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>

        ```
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4.  <span data-ttu-id="79c9d-184">Zkopírujte %SERVER_NAME%.cer ke klientskému počítači (nahraďte název_serveru % s plně kvalifikovaný název počítače, ve kterém je služba spuštěná).</span><span class="sxs-lookup"><span data-stu-id="79c9d-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>

    5.  <span data-ttu-id="79c9d-185">Naimportujte certifikát služby tak, že otevřete příkazový řádek sady Visual Studio s oprávněními správce a spuštěním následujícího příkazu v klientském počítači (nahraďte název_serveru % s plně kvalifikovaný název počítače, kde je služba spuštění):</span><span class="sxs-lookup"><span data-stu-id="79c9d-185">Import the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>

        ```
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

         <span data-ttu-id="79c9d-186">Kroky nejsou nutné v případě, že certifikát vystavil důvěryhodného vystavitele c, d a e.</span><span class="sxs-lookup"><span data-stu-id="79c9d-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>

    6.  <span data-ttu-id="79c9d-187">Upravte soubor App.config klienta následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="79c9d-187">Modify the client’s App.config file as follows:</span></span>

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

    7.  <span data-ttu-id="79c9d-188">Pokud služba běží v rámci účtu než NetworkService nebo LocalSystem účet v prostředí domény, je třeba upravit identitě koncového bodu pro koncový bod služby v souboru App.config klienta pro nastavení odpovídající hlavní název uživatele nebo na základě hlavního názvu služby u účtu, který se používá ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="79c9d-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="79c9d-189">Další informace o identitě koncového bodu, najdete v článku [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="79c9d-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>

    8.  <span data-ttu-id="79c9d-190">Spusťte Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="79c9d-190">Run Client.exe from a command prompt.</span></span>

### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="79c9d-191">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="79c9d-191">To clean up after the sample</span></span>

-   <span data-ttu-id="79c9d-192">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="79c9d-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>

## <a name="see-also"></a><span data-ttu-id="79c9d-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="79c9d-193">See Also</span></span>
