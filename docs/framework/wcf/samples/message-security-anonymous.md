---
title: Zabezpečení zpráv s anonymní metodou
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: 9ac411cd13869b70edc46724219776ec411a23dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680747"
---
# <a name="message-security-anonymous"></a><span data-ttu-id="4f251-102">Zabezpečení zpráv s anonymní metodou</span><span class="sxs-lookup"><span data-stu-id="4f251-102">Message Security Anonymous</span></span>
<span data-ttu-id="4f251-103">Zpráva zabezpečení anonymní Ukázka předvádí, jak implementovat aplikace Windows Communication Foundation (WCF), který používá zabezpečení na úrovni zpráv bez ověřování klienta, ale, který vyžaduje ověření serveru pomocí serveru X.509 certifikát.</span><span class="sxs-lookup"><span data-stu-id="4f251-103">The Message Security Anonymous sample demonstrates how to implement a Windows Communication Foundation (WCF) application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span> <span data-ttu-id="4f251-104">Všechny zprávy aplikace mezi klientem a serverem jsou podepsaný a zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="4f251-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="4f251-105">Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="4f251-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span> <span data-ttu-id="4f251-106">Tento příklad se skládá z programu konzoly klienta (.exe) a služby knihovny (.dll) hostované v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="4f251-106">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="4f251-107">Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="4f251-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
>  <span data-ttu-id="4f251-108">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4f251-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="4f251-109">Tato ukázka přidá novou operaci Kalkulačka rozhraní, která vrací `True` Pokud klient není ověřený.</span><span class="sxs-lookup"><span data-stu-id="4f251-109">This sample adds a new operation to the calculator interface that returns `True` if the client was not authenticated.</span></span>

```csharp
public class CalculatorService : ICalculator
{
    public bool IsCallerAnonymous()
    {
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.
        return ServiceSecurityContext.Current.IsAnonymous;
    }
    ...
}
```

 <span data-ttu-id="4f251-110">Služba poskytuje jeden koncový bod pro komunikaci se službou, definované pomocí souboru konfigurace (Web.config).</span><span class="sxs-lookup"><span data-stu-id="4f251-110">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="4f251-111">Koncový bod se skládá z adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="4f251-111">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="4f251-112">Je vazba konfigurována se `wsHttpBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="4f251-112">The binding is configured with a `wsHttpBinding` binding.</span></span> <span data-ttu-id="4f251-113">Výchozí režim zabezpečení `wsHttpBinding` vazba je `Message`.</span><span class="sxs-lookup"><span data-stu-id="4f251-113">The default security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="4f251-114">`clientCredentialType` Atribut je nastaven na `None`.</span><span class="sxs-lookup"><span data-stu-id="4f251-114">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

     <binding>
       <security mode="Message">
         <message clientCredentialType="None" />
       </security>
     </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 <span data-ttu-id="4f251-115">Přihlašovací údaje pro ověřování služby jsou uvedeny v [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span><span class="sxs-lookup"><span data-stu-id="4f251-115">The credentials to be used for service authentication are specified in the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span></span> <span data-ttu-id="4f251-116">Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` jako hodnota zadaná pro omezení `findValue` atributu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4f251-116">The server certificate must contain the same value for the `SubjectName` as the value specified for the `findValue` attribute as shown in the following sample code.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <!--
    The serviceCredentials behavior allows you to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
      <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
      </serviceCredentials>
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="4f251-117">Konfigurace koncového bodu klienta se skládá z absolutní adresu pro koncový bod služby, vazba a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="4f251-117">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="4f251-118">Režim zabezpečení klienta `wsHttpBinding` vazba je `Message`.</span><span class="sxs-lookup"><span data-stu-id="4f251-118">The client security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="4f251-119">`clientCredentialType` Atribut je nastaven na `None`.</span><span class="sxs-lookup"><span data-stu-id="4f251-119">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
             address="http://localhost/servicemodelsamples/service.svc"
             binding="wsHttpBinding"
             behaviorConfiguration="ClientCredentialsBehavior"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </client>

  <bindings>
    <wsHttpBinding>
      <!--This configuration defines the security mode as -->
      <!--Message and the clientCredentialType as None. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="None"/>
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 <span data-ttu-id="4f251-120">Ukázka sady <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> k <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> pro ověřování certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="4f251-120">The sample sets the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> to <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> for authenticating the service's certificate.</span></span> <span data-ttu-id="4f251-121">To se provádí v souboru App.config pro klienta v `behaviors` oddílu.</span><span class="sxs-lookup"><span data-stu-id="4f251-121">This is done in the client's App.config file in the `behaviors` section.</span></span> <span data-ttu-id="4f251-122">To znamená, že pokud je certifikát v úložišti důvěryhodných osob uživatele, je důvěryhodný bez provedení ověření řetězu certifikátu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="4f251-122">This means that if the certificate is in the user's Trusted People store, then it is trusted without performing a validation of the certificate's issuer chain.</span></span> <span data-ttu-id="4f251-123">Toto nastavení se používá zde ke zvýšení pohodlí tak, aby ukázku je možné spouštět bez vyžadování certifikátů vystavených certifikační autoritou (CA).</span><span class="sxs-lookup"><span data-stu-id="4f251-123">This setting is used here for convenience so that the sample can be run without requiring certificates issued by a certification authority (CA).</span></span> <span data-ttu-id="4f251-124">Toto nastavení je méně bezpečné než výchozí, ChainTrust.</span><span class="sxs-lookup"><span data-stu-id="4f251-124">This setting is less secure than the default, ChainTrust.</span></span> <span data-ttu-id="4f251-125">Bezpečnostních důsledcích tohoto nastavení je třeba pečlivě zvážit před použitím `PeerOrChainTrust` v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="4f251-125">The security implications of this setting should be carefully considered before using `PeerOrChainTrust` in production code.</span></span>

 <span data-ttu-id="4f251-126">Implementace klienta přidá volání `IsCallerAnonymous` metoda a v opačném případě se neliší od [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="4f251-126">The client implementation adds a call to the `IsCallerAnonymous` method and otherwise does not differ from the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>

```csharp
// Create a client with a client endpoint configuration.
CalculatorClient client = new CalculatorClient();

// Call the GetCallerIdentity operation.
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

...

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 <span data-ttu-id="4f251-127">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="4f251-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4f251-128">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="4f251-128">Press ENTER in the client window to shut down the client.</span></span>

```
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="4f251-129">Dávkový soubor Setup.bat zprávu zabezpečení anonymní ukázka je součástí umožňuje nakonfigurovat server se příslušný certifikát ke spuštění prostředí aplikace, které vyžadují zabezpečení na základě certifikátů.</span><span class="sxs-lookup"><span data-stu-id="4f251-129">The Setup.bat batch file included with the Message Security Anonymous sample enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="4f251-130">Dávkový soubor může běžet ve dvou režimech.</span><span class="sxs-lookup"><span data-stu-id="4f251-130">The batch file can be run in two modes.</span></span> <span data-ttu-id="4f251-131">Pokud chcete spustit dávkový soubor v režimu jednoho počítače, zadejte `setup.bat` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="4f251-131">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="4f251-132">Chcete-li spustit v režimu služby, zadejte `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="4f251-132">To run it in service mode, type `setup.bat service`.</span></span> <span data-ttu-id="4f251-133">Tento režim používejte při spuštění ukázky na počítačích.</span><span class="sxs-lookup"><span data-stu-id="4f251-133">Use this mode when running the sample across computers.</span></span> <span data-ttu-id="4f251-134">Zobrazit postup nastavení na konci tohoto tématu, kde podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="4f251-134">See the setup procedure at the end of this topic for details.</span></span>

 <span data-ttu-id="4f251-135">Následující body nabízí stručný přehled o různých částech dávkové soubory:</span><span class="sxs-lookup"><span data-stu-id="4f251-135">The following provides a brief overview of the different sections of the batch files:</span></span>

-   <span data-ttu-id="4f251-136">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="4f251-136">Creating the server certificate.</span></span>

     <span data-ttu-id="4f251-137">Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="4f251-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="4f251-138">% Proměnná % název_serveru Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="4f251-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="4f251-139">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="4f251-139">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="4f251-140">Pokud instalační dávkový soubor se spustí s parametrem služby (například `setup.bat service`) název_serveru % obsahuje název plně kvalifikované domény počítače.</span><span class="sxs-lookup"><span data-stu-id="4f251-140">If the setup batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="4f251-141">Jinak je výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="4f251-141">Otherwise it defaults to localhost.</span></span>

-   <span data-ttu-id="4f251-142">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="4f251-142">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="4f251-143">Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta.</span><span class="sxs-lookup"><span data-stu-id="4f251-143">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="4f251-144">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="4f251-144">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="4f251-145">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="4f251-145">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   <span data-ttu-id="4f251-146">Udělení oprávnění pro privátní klíč certifikátu.</span><span class="sxs-lookup"><span data-stu-id="4f251-146">Granting permissions on the certificate's private key.</span></span>

     <span data-ttu-id="4f251-147">Následující řádky do dávkový soubor Setup.bat uložené v úložišti LocalMachine přístupné pro certifikát serveru Ujistěte se, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účet pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="4f251-147">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
>  <span data-ttu-id="4f251-148">Pokud používáte mimo USA Anglickou verzi Windows, musíte upravit soubor Setup.bat a nahraďte `NT AUTHORITY\NETWORK SERVICE` název účtu se místní ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="4f251-148">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4f251-149">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="4f251-149">To set up, build, and run the sample</span></span>

1.  <span data-ttu-id="4f251-150">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4f251-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="4f251-151">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4f251-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="4f251-152">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="4f251-152">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="4f251-153">Ujistěte se, že cesta obsahuje složku, ve kterém jsou umístěny Makecert.exe a FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="4f251-153">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>

2.  <span data-ttu-id="4f251-154">Spusťte Setup.bat z instalační složky s ukázkou v příkazovém řádku pro vývojáře pro sadu Visual Studio spusťte s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="4f251-154">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="4f251-155">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="4f251-155">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4f251-156">Instalační dávkový soubor je navržena pro spouštění na příkazovém řádku pro vývojáře pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4f251-156">The setup batch file is designed to be run from a  Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="4f251-157">To vyžaduje, aby proměnné prostředí path v bodu do adresáře, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="4f251-157">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="4f251-158">Tato proměnná prostředí je nastavena automaticky v rámci příkazového řádku pro vývojáře pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4f251-158">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3.  <span data-ttu-id="4f251-159">Ověření přístupu ke službě pomocí prohlížeče tak, že zadáte adresu `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="4f251-159">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
4.  <span data-ttu-id="4f251-160">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="4f251-160">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="4f251-161">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="4f251-161">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="4f251-162">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="4f251-162">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="4f251-163">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="4f251-163">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="4f251-164">Vytvoření adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="4f251-164">Create a directory on the service computer.</span></span> <span data-ttu-id="4f251-165">Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="4f251-165">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="4f251-166">Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="4f251-166">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="4f251-167">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="4f251-167">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="4f251-168">Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="4f251-168">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="4f251-169">Vytvoření adresáře v klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="4f251-169">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="4f251-170">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="4f251-170">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="4f251-171">Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="4f251-171">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="4f251-172">Na serveru, spusťte `setup.bat service` otevřeného v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="4f251-172">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="4f251-173">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="4f251-173">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="4f251-174">Upravit soubor Web.config tak, aby odrážely nový název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), což je stejné jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="4f251-174">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="4f251-175">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="4f251-175">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="4f251-176">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="4f251-176">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="4f251-177">Na straně klienta spouštění ImportServiceCert.bat v příkazovém řádku pro vývojáře pro sadu Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="4f251-177">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="4f251-178">To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="4f251-178">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="4f251-179">Na klientském počítači spusťte Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4f251-179">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="4f251-180">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="4f251-180">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="4f251-181">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="4f251-181">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="4f251-182">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="4f251-182">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f251-183">Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích.</span><span class="sxs-lookup"><span data-stu-id="4f251-183">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="4f251-184">Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="4f251-184">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="4f251-185">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="4f251-185">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span></span>

## <a name="see-also"></a><span data-ttu-id="4f251-186">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f251-186">See also</span></span>
