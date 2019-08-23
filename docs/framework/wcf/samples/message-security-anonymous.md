---
title: Zabezpečení zpráv s anonymní metodou
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: fdcf0c25e4e6cab2c99457112b892f5d2c5bd3b4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930625"
---
# <a name="message-security-anonymous"></a><span data-ttu-id="70a74-102">Zabezpečení zpráv s anonymní metodou</span><span class="sxs-lookup"><span data-stu-id="70a74-102">Message Security Anonymous</span></span>
<span data-ttu-id="70a74-103">Anonymní ukázka zabezpečení zpráv ukazuje, jak implementovat aplikaci Windows Communication Foundation (WCF), která používá zabezpečení na úrovni zprávy bez ověřování klientů, ale vyžaduje ověření serveru pomocí X. 509 serveru. certifikát.</span><span class="sxs-lookup"><span data-stu-id="70a74-103">The Message Security Anonymous sample demonstrates how to implement a Windows Communication Foundation (WCF) application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span> <span data-ttu-id="70a74-104">Všechny zprávy aplikací mezi klientem a serverem jsou podepsané a šifrované.</span><span class="sxs-lookup"><span data-stu-id="70a74-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="70a74-105">Tato ukázka je založená na ukázce [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="70a74-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span> <span data-ttu-id="70a74-106">Tato ukázka se skládá z programu klientské konzoly (. exe) a knihovny služeb (. dll) hostované službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="70a74-106">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="70a74-107">Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="70a74-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="70a74-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="70a74-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="70a74-109">Tato ukázka přidá novou operaci do rozhraní kalkulačky, které vrátí `True` , pokud klient nebyl ověřen.</span><span class="sxs-lookup"><span data-stu-id="70a74-109">This sample adds a new operation to the calculator interface that returns `True` if the client was not authenticated.</span></span>

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

 <span data-ttu-id="70a74-110">Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definovaná pomocí konfiguračního souboru (Web. config).</span><span class="sxs-lookup"><span data-stu-id="70a74-110">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="70a74-111">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="70a74-111">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="70a74-112">Vazba je nakonfigurována s `wsHttpBinding` vazbou.</span><span class="sxs-lookup"><span data-stu-id="70a74-112">The binding is configured with a `wsHttpBinding` binding.</span></span> <span data-ttu-id="70a74-113">Výchozím režimem `wsHttpBinding` zabezpečení vazby je `Message`.</span><span class="sxs-lookup"><span data-stu-id="70a74-113">The default security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="70a74-114">Atribut je nastaven na `None`hodnotu. `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="70a74-114">The `clientCredentialType` attribute is set to `None`.</span></span>

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

 <span data-ttu-id="70a74-115">Přihlašovací údaje, které se mají použít k ověřování služby, jsou uvedené v [ \<> chování](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span><span class="sxs-lookup"><span data-stu-id="70a74-115">The credentials to be used for service authentication are specified in the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span></span> <span data-ttu-id="70a74-116">Certifikát serveru musí obsahovat stejnou hodnotu `SubjectName` jako hodnota zadaná `findValue` pro atribut, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="70a74-116">The server certificate must contain the same value for the `SubjectName` as the value specified for the `findValue` attribute as shown in the following sample code.</span></span>

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

 <span data-ttu-id="70a74-117">Konfigurace koncového bodu klienta se skládá z absolutní adresy koncového bodu služby, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="70a74-117">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="70a74-118">Režim zabezpečení klienta pro `wsHttpBinding` vazbu je. `Message`</span><span class="sxs-lookup"><span data-stu-id="70a74-118">The client security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="70a74-119">Atribut je nastaven na `None`hodnotu. `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="70a74-119">The `clientCredentialType` attribute is set to `None`.</span></span>

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

 <span data-ttu-id="70a74-120">Ukázka nastaví <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> pro ověřování certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="70a74-120">The sample sets the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> to <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> for authenticating the service's certificate.</span></span> <span data-ttu-id="70a74-121">To se provádí v souboru App. config klienta v `behaviors` části.</span><span class="sxs-lookup"><span data-stu-id="70a74-121">This is done in the client's App.config file in the `behaviors` section.</span></span> <span data-ttu-id="70a74-122">To znamená, že pokud je certifikát v úložišti důvěryhodných osob uživatele, je důvěryhodný, aniž by prováděl ověření řetězu vystavitele certifikátu.</span><span class="sxs-lookup"><span data-stu-id="70a74-122">This means that if the certificate is in the user's Trusted People store, then it is trusted without performing a validation of the certificate's issuer chain.</span></span> <span data-ttu-id="70a74-123">Toto nastavení se tady používá pro usnadnění, aby bylo možné spustit ukázku bez vyžadování certifikátů vydaných certifikační autoritou (CA).</span><span class="sxs-lookup"><span data-stu-id="70a74-123">This setting is used here for convenience so that the sample can be run without requiring certificates issued by a certification authority (CA).</span></span> <span data-ttu-id="70a74-124">Toto nastavení je méně bezpečné než výchozí ChainTrust.</span><span class="sxs-lookup"><span data-stu-id="70a74-124">This setting is less secure than the default, ChainTrust.</span></span> <span data-ttu-id="70a74-125">Před použitím `PeerOrChainTrust` v produkčním kódu by se mělo pečlivě zvážit dopad na zabezpečení tohoto nastavení.</span><span class="sxs-lookup"><span data-stu-id="70a74-125">The security implications of this setting should be carefully considered before using `PeerOrChainTrust` in production code.</span></span>

 <span data-ttu-id="70a74-126">Implementace klienta přidá volání `IsCallerAnonymous` metody a jinak se neliší od ukázky [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="70a74-126">The client implementation adds a call to the `IsCallerAnonymous` method and otherwise does not differ from the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>

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

 <span data-ttu-id="70a74-127">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="70a74-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="70a74-128">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="70a74-128">Press ENTER in the client window to shut down the client.</span></span>

```
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="70a74-129">Dávkový soubor Setup. bat, který je součástí ukázky zabezpečení zprávy anonymní, vám umožní nakonfigurovat server s relevantním certifikátem pro spuštění hostované aplikace, která vyžaduje zabezpečení založené na certifikátech.</span><span class="sxs-lookup"><span data-stu-id="70a74-129">The Setup.bat batch file included with the Message Security Anonymous sample enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="70a74-130">Dávkový soubor lze spustit ve dvou režimech.</span><span class="sxs-lookup"><span data-stu-id="70a74-130">The batch file can be run in two modes.</span></span> <span data-ttu-id="70a74-131">Pokud chcete spustit dávkový soubor v režimu jednoho počítače, zadejte `setup.bat` do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="70a74-131">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="70a74-132">Pokud ho chcete spustit v režimu služby, `setup.bat service`zadejte.</span><span class="sxs-lookup"><span data-stu-id="70a74-132">To run it in service mode, type `setup.bat service`.</span></span> <span data-ttu-id="70a74-133">Tento režim použijte při spuštění ukázky v různých počítačích.</span><span class="sxs-lookup"><span data-stu-id="70a74-133">Use this mode when running the sample across computers.</span></span> <span data-ttu-id="70a74-134">Podrobnosti najdete v postupu nastavení na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="70a74-134">See the setup procedure at the end of this topic for details.</span></span>

 <span data-ttu-id="70a74-135">V následující části najdete stručný přehled různých částí dávkových souborů:</span><span class="sxs-lookup"><span data-stu-id="70a74-135">The following provides a brief overview of the different sections of the batch files:</span></span>

- <span data-ttu-id="70a74-136">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="70a74-136">Creating the server certificate.</span></span>

     <span data-ttu-id="70a74-137">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="70a74-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="70a74-138">Proměnná% Název_serveru% Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="70a74-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="70a74-139">Certifikát je uložený v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="70a74-139">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="70a74-140">Pokud je instalační dávkový soubor spuštěn s argumentem služby (například `setup.bat service`),% název_serveru% obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="70a74-140">If the setup batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="70a74-141">V opačném případě se použije jako localhost.</span><span class="sxs-lookup"><span data-stu-id="70a74-141">Otherwise it defaults to localhost.</span></span>

- <span data-ttu-id="70a74-142">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="70a74-142">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="70a74-143">Následující řádek zkopíruje certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="70a74-143">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="70a74-144">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="70a74-144">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="70a74-145">Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="70a74-145">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="70a74-146">Udělení oprávnění k privátnímu klíči certifikátu.</span><span class="sxs-lookup"><span data-stu-id="70a74-146">Granting permissions on the certificate's private key.</span></span>

     <span data-ttu-id="70a74-147">Následující řádky v dávkovém souboru Setup. bat umožňují, aby byl certifikát serveru uložený v úložišti LocalMachine dostupný pro účet pracovního procesu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="70a74-147">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>

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
> <span data-ttu-id="70a74-148">Pokud používáte jinou než U. S. Anglická edice Windows: musíte upravit soubor Setup. bat a nahradit `NT AUTHORITY\NETWORK SERVICE` název účtu svým regionálním ekvivalentem.</span><span class="sxs-lookup"><span data-stu-id="70a74-148">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="70a74-149">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="70a74-149">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="70a74-150">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="70a74-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="70a74-151">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="70a74-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="70a74-152">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="70a74-152">To run the sample on the same computer</span></span>

1. <span data-ttu-id="70a74-153">Ujistěte se, že cesta obsahuje složku, ve které jsou umístěny nástroje MakeCert. exe a FindPrivateKey. exe.</span><span class="sxs-lookup"><span data-stu-id="70a74-153">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>

2. <span data-ttu-id="70a74-154">Spusťte Setup. bat z ukázkové instalační složky ve Developer Command Prompt pro Visual Studio spusťte s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="70a74-154">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="70a74-155">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="70a74-155">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="70a74-156">Instalační dávkový soubor je navržený tak, aby se spouštěl z Developer Command Prompt pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="70a74-156">The setup batch file is designed to be run from a  Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="70a74-157">Vyžaduje, aby proměnná prostředí PATH odkazovala na adresář, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="70a74-157">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="70a74-158">Tato proměnná prostředí se automaticky nastaví v rámci Developer Command Prompt pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="70a74-158">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="70a74-159">Zadáním adresy `http://localhost/servicemodelsamples/service.svc`ověřte přístup ke službě pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="70a74-159">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
4. <span data-ttu-id="70a74-160">Spustit soubor Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="70a74-160">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="70a74-161">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="70a74-161">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="70a74-162">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="70a74-162">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="70a74-163">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="70a74-163">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="70a74-164">Vytvořte adresář na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="70a74-164">Create a directory on the service computer.</span></span> <span data-ttu-id="70a74-165">Vytvořte virtuální aplikaci s názvem ServiceModelSamples pro tento adresář pomocí nástroje pro správu služby Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="70a74-165">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="70a74-166">Zkopírujte programové soubory služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="70a74-166">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="70a74-167">Ujistěte se, že jste zkopírovali soubory do podadresáře \Bin.</span><span class="sxs-lookup"><span data-stu-id="70a74-167">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="70a74-168">Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="70a74-168">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="70a74-169">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="70a74-169">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="70a74-170">Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="70a74-170">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="70a74-171">Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="70a74-171">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="70a74-172">Na serveru spusťte `setup.bat service` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="70a74-172">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="70a74-173">Při `setup.bat` spuštění`service` s argumentem se vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.</span><span class="sxs-lookup"><span data-stu-id="70a74-173">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="70a74-174">Upravte soubor Web. config tak, aby odrážel nový název certifikátu ( `findValue` v atributu [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), který je stejný jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="70a74-174">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="70a74-175">Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="70a74-175">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="70a74-176">V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="70a74-176">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="70a74-177">Na straně klienta spusťte ImportServiceCert. bat ve Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="70a74-177">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="70a74-178">Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="70a74-178">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="70a74-179">V klientském počítači spusťte z příkazového řádku soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="70a74-179">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="70a74-180">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="70a74-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="70a74-181">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="70a74-181">To clean up after the sample</span></span>  
  
- <span data-ttu-id="70a74-182">Po dokončení ukázky Spusťte Cleanup. bat ve složce Samples.</span><span class="sxs-lookup"><span data-stu-id="70a74-182">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70a74-183">Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi.</span><span class="sxs-lookup"><span data-stu-id="70a74-183">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="70a74-184">Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="70a74-184">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="70a74-185">K tomu použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Například:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="70a74-185">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span></span>
