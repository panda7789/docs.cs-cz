---
title: Členství a poskytovatel rolí
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: 73084bb766274d6eab497555e82e029f94be0359
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638402"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="9fffe-102">Členství a poskytovatel rolí</span><span class="sxs-lookup"><span data-stu-id="9fffe-102">Membership and Role Provider</span></span>
<span data-ttu-id="9fffe-103">Zprostředkovatel členství a rolí ukázka demonstruje, jak můžete použít službu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství a rolí k ověřování a autorizaci klientů.</span><span class="sxs-lookup"><span data-stu-id="9fffe-103">The Membership and Role Provider sample demonstrates how a service can use the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="9fffe-104">V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="9fffe-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fffe-105">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9fffe-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9fffe-106">Vzorek ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="9fffe-106">The sample demonstrates how:</span></span>  
  
- <span data-ttu-id="9fffe-107">Klient může ověřit pomocí kombinace uživatelského jména hesla.</span><span class="sxs-lookup"><span data-stu-id="9fffe-107">A client can authenticate by using the username-password combination.</span></span>  
  
- <span data-ttu-id="9fffe-108">Server můžete ověřit přihlašovací údaje klienta proti [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství.</span><span class="sxs-lookup"><span data-stu-id="9fffe-108">The server can validate the client credentials against the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
- <span data-ttu-id="9fffe-109">Na serveru, lze ověřit pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="9fffe-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
- <span data-ttu-id="9fffe-110">Server můžete namapovat ověřený klient do role pomocí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí.</span><span class="sxs-lookup"><span data-stu-id="9fffe-110">The server can map the authenticated client to a role by using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider.</span></span>  
  
- <span data-ttu-id="9fffe-111">Server můžete použít `PrincipalPermissionAttribute` pro řízení přístupu k určité metody, které jsou vystaveny službou.</span><span class="sxs-lookup"><span data-stu-id="9fffe-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="9fffe-112">Zprostředkovatele členství a role jsou nakonfigurovány pro použití úložiště se opírá o systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9fffe-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="9fffe-113">Připojovací řetězec a různé možnosti jsou uvedeny v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="9fffe-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="9fffe-114">Zprostředkovatel členství je označen názvem `SqlMembershipProvider` při zprostředkovatele rolí je označen názvem `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="9fffe-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
```xml  
<!-- Set the connection string for SQL Server -->  
<connectionStrings>  
  <add name="SqlConn"   
       connectionString="Data Source=localhost;Integrated Security=SSPI;Initial Catalog=aspnetdb;" />  
</connectionStrings>  
  
<system.web>  
  <!-- Configure the Sql Membership Provider -->  
  <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
    <providers>  
      <clear />  
      <add   
        name="SqlMembershipProvider"   
        type="System.Web.Security.SqlMembershipProvider"   
        connectionStringName="SqlConn"  
        applicationName="MembershipAndRoleProviderSample"  
        enablePasswordRetrieval="false"  
        enablePasswordReset="false"  
        requiresQuestionAndAnswer="false"  
        requiresUniqueEmail="true"  
        passwordFormat="Hashed" />  
    </providers>  
  </membership>  
  
  <!-- Configure the Sql Role Provider -->  
  <roleManager enabled ="true"   
               defaultProvider ="SqlRoleProvider" >  
    <providers>  
      <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
    </providers>  
  </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="9fffe-115">Služba poskytuje jeden koncový bod pro komunikaci se službou, která je definována pomocí konfiguračního souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="9fffe-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="9fffe-116">Koncový bod se skládá z adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="9fffe-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="9fffe-117">Je vazba konfigurována se standardní `wsHttpBinding`, která ve výchozím nastavení používá ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="9fffe-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="9fffe-118">Tato ukázka nastaví standardní `wsHttpBinding` ověřování uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="9fffe-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="9fffe-119">Chování Určuje, že certifikát serveru se bude používat pro ověřování služby.</span><span class="sxs-lookup"><span data-stu-id="9fffe-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="9fffe-120">Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` jako `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="9fffe-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="9fffe-121">Kromě toho chování Určuje, že ověřování uživatelského jména hesla páry provádí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství a rolí mapování se provádí pomocí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí tak, že zadáte názvy definované pro dva poskytovatelé.</span><span class="sxs-lookup"><span data-stu-id="9fffe-121">In addition the behavior specifies that authentication of username-password pairs is performed by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider and role mapping is performed by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider by specifying the names defined for the two providers.</span></span>  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Set up a binding that uses Username as the client credential type -->  
      <binding>  
        <security mode ="Message">  
          <message clientCredentialType ="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!-- Configure role based authorization to use the Role Provider -->  
        <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                              roleProviderName ="SqlRoleProvider" />  
        <serviceCredentials>  
          <!-- Configure user name authentication to use the Membership Provider -->  
          <userNameAuthentication userNamePasswordValidationMode ="MembershipProvider"   
                                  membershipProviderName ="SqlMembershipProvider"/>  
          <!-- Configure the service certificate -->  
          <serviceCertificate storeLocation ="LocalMachine"   
                              storeName ="My"   
                              x509FindType ="FindBySubjectName"  
                              findValue ="localhost" />  
        </serviceCredentials>  
        <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
        <serviceDebug includeExceptionDetailInFaults="false" />  
        <serviceMetadata httpGetEnabled="true"/>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9fffe-122">Při spuštění ukázky klient volá různé operace služby do dvou různých uživatelských účtů: Alici, Roberta a Karel.</span><span class="sxs-lookup"><span data-stu-id="9fffe-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="9fffe-123">Operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="9fffe-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9fffe-124">Všechny čtyři volání provedli jako uživatel "Alice" uspěli.</span><span class="sxs-lookup"><span data-stu-id="9fffe-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="9fffe-125">Uživatel "Bob" by měl získat chybu při pokusu o volání metody dělení odepření přístupu.</span><span class="sxs-lookup"><span data-stu-id="9fffe-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="9fffe-126">Uživatel "Karel" by měl získat chybu při pokusu o volání odepření přístupu vynásobí metody.</span><span class="sxs-lookup"><span data-stu-id="9fffe-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="9fffe-127">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="9fffe-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9fffe-128">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="9fffe-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9fffe-129">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9fffe-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="9fffe-130">Ujistěte se, že jste nakonfigurovali [databáze aplikačních služeb ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94997).</span><span class="sxs-lookup"><span data-stu-id="9fffe-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9fffe-131">Pokud používáte systém SQL Server Express Edition, je název vašeho serveru. \SQLEXPRESS.</span><span class="sxs-lookup"><span data-stu-id="9fffe-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="9fffe-132">Tento server by měl při konfiguraci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] databáze služeb aplikací stejně jako v souboru Web.config připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="9fffe-132">This server should be used when configuring the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9fffe-133">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Účet pracovního procesu musí mít oprávnění databáze, která se vytvoří v tomto kroku.</span><span class="sxs-lookup"><span data-stu-id="9fffe-133">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="9fffe-134">K tomu použijte nástroj sqlcmd nebo SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="9fffe-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="9fffe-135">Ke spuštění ukázky v konfiguraci s jedním nebo více počítači, použijte následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="9fffe-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="9fffe-136">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="9fffe-136">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="9fffe-137">Ujistěte se, že cesta obsahuje složku, kde je umístěn Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="9fffe-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="9fffe-138">Spusťte Setup.bat z instalační složky s ukázkou v příkazovém řádku pro vývojáře pro sadu Visual Studio spusťte s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="9fffe-138">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="9fffe-139">Tím se nainstaluje služba certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="9fffe-139">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="9fffe-140">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="9fffe-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="9fffe-141">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="9fffe-141">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="9fffe-142">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="9fffe-142">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="9fffe-143">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="9fffe-143">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="9fffe-144">Vytvoření adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="9fffe-144">Create a directory on the service computer.</span></span> <span data-ttu-id="9fffe-145">Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="9fffe-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="9fffe-146">Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="9fffe-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="9fffe-147">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="9fffe-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="9fffe-148">Také kopírovat soubory Setup.bat GetComputerName.vbs a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="9fffe-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="9fffe-149">Vytvoření adresáře v klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="9fffe-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="9fffe-150">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="9fffe-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="9fffe-151">Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="9fffe-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="9fffe-152">Na serveru, otevřete příkazový řádek vývojáře pro sadu Visual Studio s oprávněními správce a spusťte `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="9fffe-152">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="9fffe-153">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="9fffe-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="9fffe-154">Upravit soubor Web.config tak, aby odrážely nový název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), což je stejné jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="9fffe-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="9fffe-155">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="9fffe-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="9fffe-156">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="9fffe-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="9fffe-157">V klientském počítači otevřete příkazový řádek vývojáře pro sadu Visual Studio s oprávněními správce a spusťte ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="9fffe-157">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="9fffe-158">To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="9fffe-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="9fffe-159">Na klientském počítači spusťte Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="9fffe-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="9fffe-160">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="9fffe-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="9fffe-161">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="9fffe-161">To clean up after the sample</span></span>  
  
- <span data-ttu-id="9fffe-162">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="9fffe-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fffe-163">Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích.</span><span class="sxs-lookup"><span data-stu-id="9fffe-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="9fffe-164">Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="9fffe-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="9fffe-165">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="9fffe-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="9fffe-166">Instalační dávkový soubor</span><span class="sxs-lookup"><span data-stu-id="9fffe-166">The Setup Batch File</span></span>  
 <span data-ttu-id="9fffe-167">Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace v místním prostředí, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="9fffe-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="9fffe-168">Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.</span><span class="sxs-lookup"><span data-stu-id="9fffe-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="9fffe-169">Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v odpovídající konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="9fffe-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
- <span data-ttu-id="9fffe-170">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="9fffe-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="9fffe-171">Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="9fffe-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="9fffe-172">% Proměnná % název_serveru Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="9fffe-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="9fffe-173">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="9fffe-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="9fffe-174">Tento dávkový soubor výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="9fffe-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="9fffe-175">Certifikát je uložen v úložišti (osobních) v části umístění úložiště LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="9fffe-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="9fffe-176">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="9fffe-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="9fffe-177">Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="9fffe-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="9fffe-178">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="9fffe-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="9fffe-179">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="9fffe-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
