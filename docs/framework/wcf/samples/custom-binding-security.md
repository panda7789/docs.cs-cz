---
title: Zabezpečení vlastních vazeb
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
caps.latest.revision: 30
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 4774e4ed6c5afc6e9c4af50e0663ffe8c0964b7f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="custom-binding-security"></a><span data-ttu-id="1cce7-102">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="1cce7-102">Custom Binding Security</span></span>
<span data-ttu-id="1cce7-103">Tento příklad ukazuje, jak nakonfigurovat zabezpečení tak, že použití vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="1cce7-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="1cce7-104">Ukazuje, jak použít k povolení zabezpečení na úrovni zpráv společně s zabezpečený přenos vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="1cce7-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="1cce7-105">To je užitečné, když zabezpečení přenosu je potřeba k přenosu zpráv mezi klientem a službou a současně zprávy musí být zabezpečení na úrovni zpráv.</span><span class="sxs-lookup"><span data-stu-id="1cce7-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="1cce7-106">Tato konfigurace není podporována vazby poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="1cce7-106">This configuration is not supported by system-provided bindings.</span></span>  
  
 <span data-ttu-id="1cce7-107">Tato ukázka se skládá z konzoly programu klienta (EXE) a program konzoly služby (EXE).</span><span class="sxs-lookup"><span data-stu-id="1cce7-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="1cce7-108">Služba se implementuje duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1cce7-108">The service implements a duplex contract.</span></span> <span data-ttu-id="1cce7-109">Kontrakt je definována `ICalculatorDuplex` rozhraní, která zpřístupňuje matematické operace (přidat, odečíst, násobit a dělit).</span><span class="sxs-lookup"><span data-stu-id="1cce7-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="1cce7-110">`ICalculatorDuplex` Rozhraní umožňuje klientovi provádět matematické operace, výpočet výsledku spuštěných v relaci.</span><span class="sxs-lookup"><span data-stu-id="1cce7-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="1cce7-111">Nezávisle, mohou službu vracet výsledky na `ICalculatorDuplexCallback` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1cce7-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="1cce7-112">Duplexní kontrakt vyžaduje relaci, protože kontextu musí být stanovena ke korelaci sadu zprávy odesílané mezi klientem a službu.</span><span class="sxs-lookup"><span data-stu-id="1cce7-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="1cce7-113">Vlastní vazby je definována, která podporuje duplexní komunikace a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1cce7-113">A custom binding is defined that supports duplex communication and is secure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cce7-114">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="1cce7-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1cce7-115">Konfigurace služby definuje vlastní vazby, který podporuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="1cce7-115">The service configuration defines a custom binding that supports the following:</span></span>  
  
-   <span data-ttu-id="1cce7-116">Komunikaci TCP chráněný pomocí protokolu TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="1cce7-116">TCP communication protected by using the TLS/SSL protocol.</span></span>  
  
-   <span data-ttu-id="1cce7-117">Zabezpečení zpráv systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1cce7-117">Windows message security.</span></span>  
  
 <span data-ttu-id="1cce7-118">Konfigurace vlastních vazeb umožňuje zabezpečený přenos současně povolením zprávy úroveň zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1cce7-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="1cce7-119">Řazení elementů vazby je důležité k definování vlastní vazby, protože každý představuje vrstvy v zásobníku kanál (viz [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="1cce7-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="1cce7-120">Vlastní vazby je definována v konfiguračních souborech klienta a služby, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1cce7-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="1cce7-121">Vlastní vazby používá certifikát služby k ověřování na úrovni přenosu a k ochraně zprávy během přenosu mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="1cce7-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="1cce7-122">To lze provést `sslStreamSecurity` prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="1cce7-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="1cce7-123">Certifikát služby je nakonfigurovaný pomocí chování služby, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1cce7-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="1cce7-124">Kromě toho používá vlastní vazby zabezpečení zpráv s typ přihlašovacích údajů Windows – jedná se o výchozí typ přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="1cce7-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="1cce7-125">To lze provést `security` prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="1cce7-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="1cce7-126">Klienta a služby se ověřují pomocí zabezpečení na úrovni zpráv, pokud se mechanismus ověřování protokolu Kerberos je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1cce7-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="1cce7-127">To se stane, když ukázku běží v prostředí služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1cce7-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="1cce7-128">Pokud se mechanismus ověřování protokolu Kerberos není k dispozici, je použít ověřování NTLM.</span><span class="sxs-lookup"><span data-stu-id="1cce7-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="1cce7-129">NTLM ověřuje klienta pro službu ale neověřuje služby klienta.</span><span class="sxs-lookup"><span data-stu-id="1cce7-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="1cce7-130">`security` Prvku vazby je nakonfigurovaný na použití `SecureConversation``authenticationType`, což vede k vytvoření relace zabezpečení na klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="1cce7-130">The `security` binding element is configured to use `SecureConversation``authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="1cce7-131">To je nutné povolit duplexního kontraktu služby pracovat.</span><span class="sxs-lookup"><span data-stu-id="1cce7-131">This is required to enable the service's duplex contract to work.</span></span>  
  
 <span data-ttu-id="1cce7-132">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="1cce7-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="1cce7-133">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="1cce7-133">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 <span data-ttu-id="1cce7-134">Když spustíte ukázku, uvidíte zprávy vrácen do klienta na rozhraní zpětné volání odeslaných ze služby.</span><span class="sxs-lookup"><span data-stu-id="1cce7-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="1cce7-135">Zobrazí se každý zprostředkující výsledek, za nímž následuje celý rovnice po dokončení všech operací.</span><span class="sxs-lookup"><span data-stu-id="1cce7-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="1cce7-136">Stisknutím klávesy ENTER vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="1cce7-136">Press ENTER to shut down the client.</span></span>  
  
 <span data-ttu-id="1cce7-137">Vložený soubor Setup.bat umožňuje nakonfigurovat certifikát příslušné služby, který chcete spustit hostované aplikace, která vyžaduje zabezpečení na základě certifikátu klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="1cce7-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="1cce7-138">Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.</span><span class="sxs-lookup"><span data-stu-id="1cce7-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="1cce7-139">Následující poskytuje stručný přehled různých oddílů dávkové soubory, které se vztahují k této ukázce tak, aby může být změněn na spouštění v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="1cce7-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="1cce7-140">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="1cce7-140">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="1cce7-141">Následující řádky ze souboru Setup.bat vytvořit certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="1cce7-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="1cce7-142">`%SERVER_NAME%` Proměnná Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="1cce7-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="1cce7-143">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="1cce7-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="1cce7-144">Tento dávkový soubor výchozí název serveru a localhost.</span><span class="sxs-lookup"><span data-stu-id="1cce7-144">This batch file defaults the server name to localhost.</span></span>  
  
     <span data-ttu-id="1cce7-145">Certifikát je uložen v úložišti CurrentUser pro hostované webové služby.</span><span class="sxs-lookup"><span data-stu-id="1cce7-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="1cce7-146">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="1cce7-146">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="1cce7-147">Následující řádky do kopírování souborů Setup.bat certifikát serveru do důvěryhodných osob klienta úložiště.</span><span class="sxs-lookup"><span data-stu-id="1cce7-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="1cce7-148">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="1cce7-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="1cce7-149">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="1cce7-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1cce7-150">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2010 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="1cce7-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="1cce7-151">Se vyžaduje, aby proměnné prostředí MSSDK bodu na adresář, kam nainstalovat sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="1cce7-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="1cce7-152">Tato proměnná prostředí bude automaticky nastavena v rámci Visual Studio 2010 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="1cce7-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1cce7-153">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="1cce7-153">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1cce7-154">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1cce7-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1cce7-155">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1cce7-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1cce7-156">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1cce7-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="1cce7-157">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="1cce7-157">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="1cce7-158">Otevřete okno příkazového řádku Visual Studio s oprávněními správce a spusťte Setup.bat z ukázkové složky instalace.</span><span class="sxs-lookup"><span data-stu-id="1cce7-158">Open a Visual Studio Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="1cce7-159">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="1cce7-159">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1cce7-160">Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1cce7-160">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="1cce7-161">Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="1cce7-161">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="1cce7-162">Spusťte Service.exe z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="1cce7-162">Launch Service.exe from \service\bin.</span></span>  
  
3.  <span data-ttu-id="1cce7-163">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="1cce7-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="1cce7-164">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="1cce7-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="1cce7-165">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="1cce7-165">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="1cce7-166">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="1cce7-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="1cce7-167">Na počítači se službou:</span><span class="sxs-lookup"><span data-stu-id="1cce7-167">On the service computer:</span></span>  
  
    1.  <span data-ttu-id="1cce7-168">Vytvořte virtuální adresář s názvem servicemodelsamples na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="1cce7-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>  
  
    2.  <span data-ttu-id="1cce7-169">Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="1cce7-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="1cce7-170">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="1cce7-170">Ensure that you copy the files in the \bin subdirectory.</span></span>  
  
    3.  <span data-ttu-id="1cce7-171">Zkopírujte soubory Setup.bat a Cleanup.bat na počítač služby.</span><span class="sxs-lookup"><span data-stu-id="1cce7-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
    4.  <span data-ttu-id="1cce7-172">Spusťte následující příkaz v příkazovém řádku Visual Studia otevřít s oprávněními správce: `Setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="1cce7-172">Run the following command in a Visual Studio command prompt opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="1cce7-173">Tím se vytvoří certifikát služby s názvem subjektu odpovídající názvu počítače, který byl spuštěn dávkového souboru.</span><span class="sxs-lookup"><span data-stu-id="1cce7-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="1cce7-174">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2010 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="1cce7-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="1cce7-175">To vyžaduje, aby proměnné prostředí path přejděte na adresář, kam nainstalovat sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="1cce7-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="1cce7-176">Tato proměnná prostředí bude automaticky nastavena v rámci Visual Studio 2010 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="1cce7-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>  
  
    5.  <span data-ttu-id="1cce7-177">Změna [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) v souboru Service.exe.config tak, aby odrážela název předmětu certifikátu vygenerované v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="1cce7-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>  
  
    6.  <span data-ttu-id="1cce7-178">Spusťte Service.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1cce7-178">Run Service.exe from a command prompt.</span></span>  
  
2.  <span data-ttu-id="1cce7-179">Na klientském počítači:</span><span class="sxs-lookup"><span data-stu-id="1cce7-179">On the client computer:</span></span>  
  
    1.  <span data-ttu-id="1cce7-180">Zkopírujte soubory programu klienta ze složky \client\bin\ do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="1cce7-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="1cce7-181">Taky zkopírujte soubor Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="1cce7-181">Also copy the Cleanup.bat file.</span></span>  
  
    2.  <span data-ttu-id="1cce7-182">Spusťte Cleanup.bat odebrat všechny certifikáty, staré z předchozí ukázky.</span><span class="sxs-lookup"><span data-stu-id="1cce7-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>  
  
    3.  <span data-ttu-id="1cce7-183">Exportujte certifikát služby tak, že otevřete příkazový řádek sady Visual Studio s oprávněními správce a spuštěním následujícího příkazu na počítači se službou (Nahraďte `%SERVER_NAME%` s plně kvalifikovaný název počítače, kde je služba spuštění):</span><span class="sxs-lookup"><span data-stu-id="1cce7-183">Export the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  <span data-ttu-id="1cce7-184">Zkopírujte %SERVER_NAME%.cer do klientského počítače (substitute název_serveru % s plně kvalifikovaný název počítače, kde je služba spuštěná).</span><span class="sxs-lookup"><span data-stu-id="1cce7-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>  
  
    5.  <span data-ttu-id="1cce7-185">Importujte certifikát služby, že otevřete příkazový řádek sady Visual Studio s oprávněními správce a spuštěním následujícího příkazu na klientském počítači (substitute název_serveru % s plně kvalifikovaný název počítače, kde je služba spuštění):</span><span class="sxs-lookup"><span data-stu-id="1cce7-185">Import the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         <span data-ttu-id="1cce7-186">Kroky c, d a e nejsou nutné v případě, že certifikát je vydán důvěryhodného vystavitele.</span><span class="sxs-lookup"><span data-stu-id="1cce7-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>  
  
    6.  <span data-ttu-id="1cce7-187">Upravte soubor App.config klienta následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1cce7-187">Modify the client’s App.config file as follows:</span></span>  
  
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
  
    7.  <span data-ttu-id="1cce7-188">Služba běží pod účtu, než NetworkService nebo pod účtem LocalSystem v prostředí domény, může být potřeba změnit identitu koncového bodu pro koncový bod služby v souboru App.config klienta nastavit na příslušný hlavní název uživatele nebo na základě hlavního názvu služby na účet, který se používá ke spouštění služby.</span><span class="sxs-lookup"><span data-stu-id="1cce7-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="1cce7-189">Další informace o identitě koncového bodu najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="1cce7-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>  
  
    8.  <span data-ttu-id="1cce7-190">Spusťte Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1cce7-190">Run Client.exe from a command prompt.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="1cce7-191">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="1cce7-191">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="1cce7-192">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="1cce7-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cce7-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cce7-193">See Also</span></span>
