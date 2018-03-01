---
title: "Zabezpečení zpráv s anonymní metodou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: d6f3ac3ba51939f319d1d0e98265d7867233f2b6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="message-security-anonymous"></a><span data-ttu-id="7ae04-102">Zabezpečení zpráv s anonymní metodou</span><span class="sxs-lookup"><span data-stu-id="7ae04-102">Message Security Anonymous</span></span>
<span data-ttu-id="7ae04-103">Ukázku zprávu zabezpečení anonymní ukazuje, jak implementovat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace používající zabezpečení na úrovni zpráv bez jakéhokoli ověřování klienta, ale která vyžaduje server ověřování pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="7ae04-103">The Message Security Anonymous sample demonstrates how to implement a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span> <span data-ttu-id="7ae04-104">Všechny zprávy aplikace mezi klientem a serverem jsou podepsat a zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="7ae04-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="7ae04-105">Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="7ae04-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span> <span data-ttu-id="7ae04-106">Tato ukázka se skládá z konzoly programu klienta (.exe) a služby knihovny (DLL) hostované Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="7ae04-106">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="7ae04-107">Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="7ae04-107">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ae04-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7ae04-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7ae04-109">Tato ukázka přidá operaci nového kalkulačky rozhraní, které vrátí `True` Pokud klient nebyl ověřen.</span><span class="sxs-lookup"><span data-stu-id="7ae04-109">This sample adds a new operation to the calculator interface that returns `True` if the client was not authenticated.</span></span>  
  
```  
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
  
 <span data-ttu-id="7ae04-110">Službu zpřístupní jeden koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru (Web.config).</span><span class="sxs-lookup"><span data-stu-id="7ae04-110">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="7ae04-111">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="7ae04-111">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="7ae04-112">Vazba je nakonfigurována s `wsHttpBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="7ae04-112">The binding is configured with a `wsHttpBinding` binding.</span></span> <span data-ttu-id="7ae04-113">Výchozí režim zabezpečení `wsHttpBinding` vazba je `Message`.</span><span class="sxs-lookup"><span data-stu-id="7ae04-113">The default security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="7ae04-114">`clientCredentialType` Je nastavena na hodnotu `None`.</span><span class="sxs-lookup"><span data-stu-id="7ae04-114">The `clientCredentialType` attribute is set to `None`.</span></span>  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
     <!--   
     <!--This configuration defines the security mode as Message and-->  
     <!--the clientCredentialType as None. This mode provides -- >  
     <!--server authentication only using the service certificate.-->  
  
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
  
 <span data-ttu-id="7ae04-115">Přihlašovací údaje, které má být použit pro ověřování služby jsou určené v [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span><span class="sxs-lookup"><span data-stu-id="7ae04-115">The credentials to be used for service authentication are specified in the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span></span> <span data-ttu-id="7ae04-116">Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` jako zadaná hodnota parametru `findValue` atributu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="7ae04-116">The server certificate must contain the same value for the `SubjectName` as the value specified for the `findValue` attribute as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="7ae04-117">Konfigurace klienta koncový bod se skládá z absolutní adresu pro koncový bod služby, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="7ae04-117">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="7ae04-118">Režim zabezpečení klienta `wsHttpBinding` vazba je `Message`.</span><span class="sxs-lookup"><span data-stu-id="7ae04-118">The client security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="7ae04-119">`clientCredentialType` Je nastavena na hodnotu `None`.</span><span class="sxs-lookup"><span data-stu-id="7ae04-119">The `clientCredentialType` attribute is set to `None`.</span></span>  
  
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
  
 <span data-ttu-id="7ae04-120">Ukázka sady <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> k <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> pro ověřování certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="7ae04-120">The sample sets the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> to <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> for authenticating the service's certificate.</span></span> <span data-ttu-id="7ae04-121">To se provádí v souboru App.config klienta v `behaviors` oddílu.</span><span class="sxs-lookup"><span data-stu-id="7ae04-121">This is done in the client's App.config file in the `behaviors` section.</span></span> <span data-ttu-id="7ae04-122">To znamená, že pokud je certifikát v úložišti důvěryhodných osob uživatele, pak je důvěryhodný bez provedení ověření řetězu vystavitele certifikátu.</span><span class="sxs-lookup"><span data-stu-id="7ae04-122">This means that if the certificate is in the user's Trusted People store, then it is trusted without performing a validation of the certificate's issuer chain.</span></span> <span data-ttu-id="7ae04-123">Toto nastavení je zde slouží pro usnadnění práce, aby ukázce je možné spouštět bez vyžadování certifikátů vystavených certifikační autoritou (CA).</span><span class="sxs-lookup"><span data-stu-id="7ae04-123">This setting is used here for convenience so that the sample can be run without requiring certificates issued by a certification authority (CA).</span></span> <span data-ttu-id="7ae04-124">Toto nastavení je méně bezpečné než výchozí, ChainTrust.</span><span class="sxs-lookup"><span data-stu-id="7ae04-124">This setting is less secure than the default, ChainTrust.</span></span> <span data-ttu-id="7ae04-125">Bezpečnostních důsledcích tohoto nastavení je třeba pečlivě zvážit před použitím `PeerOrChainTrust` v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="7ae04-125">The security implications of this setting should be carefully considered before using `PeerOrChainTrust` in production code.</span></span>  
  
 <span data-ttu-id="7ae04-126">Implementace klienta přidá volání `IsCallerAnonymous` metoda a jinak neliší od [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="7ae04-126">The client implementation adds a call to the `IsCallerAnonymous` method and otherwise does not differ from the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>  
  
```  
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
  
 <span data-ttu-id="7ae04-127">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="7ae04-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7ae04-128">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="7ae04-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
IsCallerAnonymous returned: True  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="7ae04-129">Dávkový soubor Setup.bat součástí ukázku zprávu zabezpečení anonymní umožňuje nakonfigurovat server se příslušný certifikát spuštění hostované aplikace, která vyžaduje zabezpečení na základě certifikátu.</span><span class="sxs-lookup"><span data-stu-id="7ae04-129">The Setup.bat batch file included with the Message Security Anonymous sample enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="7ae04-130">Dávkový soubor lze spustit ve dvou režimech.</span><span class="sxs-lookup"><span data-stu-id="7ae04-130">The batch file can be run in two modes.</span></span> <span data-ttu-id="7ae04-131">Chcete-li spustit dávkový soubor v režimu jednoho počítače, zadejte `setup.bat` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="7ae04-131">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="7ae04-132">Chcete-li spustit v režimu služby, zadejte `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="7ae04-132">To run it in service mode, type `setup.bat service`.</span></span> <span data-ttu-id="7ae04-133">Tento režim používejte při spuštění ukázky mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="7ae04-133">Use this mode when running the sample across computers.</span></span> <span data-ttu-id="7ae04-134">Přečtěte si postup instalace na konci tohoto tématu podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="7ae04-134">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="7ae04-135">Následující poskytuje stručný přehled různých oddílů dávkové soubory:</span><span class="sxs-lookup"><span data-stu-id="7ae04-135">The following provides a brief overview of the different sections of the batch files:</span></span>  
  
-   <span data-ttu-id="7ae04-136">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="7ae04-136">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="7ae04-137">Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="7ae04-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="7ae04-138">Proměnná % název_serveru % Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="7ae04-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="7ae04-139">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="7ae04-139">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="7ae04-140">Jestli dávkový soubor Instalační program se spustí s parametrem služby (například `setup.bat service`) název_serveru % obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="7ae04-140">If the setup batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="7ae04-141">V opačném případě bude výchozí localhost.</span><span class="sxs-lookup"><span data-stu-id="7ae04-141">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="7ae04-142">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="7ae04-142">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="7ae04-143">Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob na klienta.</span><span class="sxs-lookup"><span data-stu-id="7ae04-143">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="7ae04-144">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="7ae04-144">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="7ae04-145">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="7ae04-145">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="7ae04-146">Udělení oprávnění pro privátní klíč certifikátu.</span><span class="sxs-lookup"><span data-stu-id="7ae04-146">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="7ae04-147">Zkontrolujte následující řádky v dávkovém souboru, Setup.bat certifikát serveru, který je uložen v úložišti LocalMachine přístupné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účet pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="7ae04-147">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
    ```  
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="7ae04-148">Pokud používáte jiný USA Anglickou verzi systému Windows, musíte upravit soubor Setup.bat a nahraďte `NT AUTHORITY\NETWORK SERVICE` název účtu s vaší místní ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="7ae04-148">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7ae04-149">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="7ae04-149">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7ae04-150">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7ae04-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7ae04-151">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7ae04-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="7ae04-152">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="7ae04-152">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="7ae04-153">Ujistěte se, že cesta obsahuje složku, kde jsou umístěny Makecert.exe a FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="7ae04-153">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2.  <span data-ttu-id="7ae04-154">Spuštění Setup.bat od vzorku instalační složku v sadě Visual Studio příkazovém řádku spusťte s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="7ae04-154">Run Setup.bat from the sample install folder in a Visual Studio command prompt run with administrator privileges.</span></span> <span data-ttu-id="7ae04-155">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="7ae04-155">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7ae04-156">Dávkový soubor Instalační program je určen pro spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7ae04-156">The setup batch file is designed to be run from a  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]Command Prompt.</span></span> <span data-ttu-id="7ae04-157">To vyžaduje, aby proměnné prostředí path přejděte na adresář, kam nainstalovat sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="7ae04-157">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="7ae04-158">Tato proměnná prostředí bude automaticky nastavena v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7ae04-158">This environment variable is automatically set within a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]Command Prompt.</span></span>  
  
3.  <span data-ttu-id="7ae04-159">Ověřte přístup ke službě pomocí prohlížeče zadáním adresy http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="7ae04-159">Verify access to the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
4.  <span data-ttu-id="7ae04-160">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="7ae04-160">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="7ae04-161">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="7ae04-161">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="7ae04-162">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="7ae04-162">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="7ae04-163">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="7ae04-163">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="7ae04-164">Vytvořte adresář na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="7ae04-164">Create a directory on the service computer.</span></span> <span data-ttu-id="7ae04-165">Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="7ae04-165">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="7ae04-166">Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="7ae04-166">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="7ae04-167">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="7ae04-167">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="7ae04-168">Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="7ae04-168">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="7ae04-169">Vytvořte adresář na klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="7ae04-169">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="7ae04-170">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="7ae04-170">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="7ae04-171">Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="7ae04-171">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="7ae04-172">Na serveru, spusťte `setup.bat service` ve z příkazového řádku Visual Studia otevřen s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="7ae04-172">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="7ae04-173">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="7ae04-173">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="7ae04-174">Upravit soubor Web.config tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), což je stejný jako název plně kvalifikované domény počítače.</span><span class="sxs-lookup"><span data-stu-id="7ae04-174">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="7ae04-175">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="7ae04-175">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="7ae04-176">V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="7ae04-176">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="7ae04-177">V klientovi spusťte ImportServiceCert.bat v z příkazového řádku Visual Studia otevřít s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="7ae04-177">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="7ae04-178">Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="7ae04-178">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="7ae04-179">Na klientském počítači spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="7ae04-179">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="7ae04-180">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="7ae04-180">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="7ae04-181">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="7ae04-181">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="7ae04-182">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="7ae04-182">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ae04-183">Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="7ae04-183">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="7ae04-184">Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="7ae04-184">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="7ae04-185">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="7ae04-185">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae04-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ae04-186">See Also</span></span>
