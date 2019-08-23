---
title: Členství a poskytovatel rolí
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: 894fcef0cbb25f85043aa6f5c55c45bae5161546
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948550"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="e0d55-102">Členství a poskytovatel rolí</span><span class="sxs-lookup"><span data-stu-id="e0d55-102">Membership and Role Provider</span></span>
<span data-ttu-id="e0d55-103">Ukázka členství a zprostředkovatele rolí předvádí, jak může služba k ověřování a autorizaci klientů použít poskytovatele členství a rolí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e0d55-103">The Membership and Role Provider sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="e0d55-104">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="e0d55-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0d55-105">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e0d55-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e0d55-106">Ukázka ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="e0d55-106">The sample demonstrates how:</span></span>  
  
- <span data-ttu-id="e0d55-107">Klient se může ověřit pomocí kombinace uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="e0d55-107">A client can authenticate by using the username-password combination.</span></span>  
  
- <span data-ttu-id="e0d55-108">Server může ověřit pověření klienta pro poskytovatele členství ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e0d55-108">The server can validate the client credentials against the ASP.NET membership provider.</span></span>  
  
- <span data-ttu-id="e0d55-109">Server se dá ověřit pomocí certifikátu X. 509 serveru.</span><span class="sxs-lookup"><span data-stu-id="e0d55-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
- <span data-ttu-id="e0d55-110">Server může mapovat ověřeného klienta na roli pomocí poskytovatele rolí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e0d55-110">The server can map the authenticated client to a role by using the ASP.NET role provider.</span></span>  
  
- <span data-ttu-id="e0d55-111">Server může použít `PrincipalPermissionAttribute` k řízení přístupu k určitým metodám, které jsou zpřístupněné službou.</span><span class="sxs-lookup"><span data-stu-id="e0d55-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="e0d55-112">Zprostředkovatelé členství a rolí jsou nakonfigurováni tak, aby používal úložiště zajištěné SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e0d55-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="e0d55-113">Připojovací řetězec a různé možnosti jsou zadány v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="e0d55-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="e0d55-114">Zprostředkovateli členství je uveden název `SqlMembershipProvider` , zatímco poskytovatel role má název. `SqlRoleProvider`</span><span class="sxs-lookup"><span data-stu-id="e0d55-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
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
  
 <span data-ttu-id="e0d55-115">Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, která je definována pomocí konfiguračního souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="e0d55-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="e0d55-116">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e0d55-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="e0d55-117">Vazba je nakonfigurována se standardem `wsHttpBinding`, který používá ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e0d55-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="e0d55-118">Tato ukázka nastavuje standard `wsHttpBinding` pro použití ověřování uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="e0d55-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="e0d55-119">Chování určuje, že se má certifikát serveru použít k ověřování služby.</span><span class="sxs-lookup"><span data-stu-id="e0d55-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="e0d55-120">Certifikát serveru musí obsahovat stejnou hodnotu `SubjectName` `findValue` jako atribut v [ \<prvku konfigurace > serviceCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="e0d55-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="e0d55-121">Kromě toho chování určuje, že zprostředkovatel členství v ASP.NET a mapování rolí provádí zprostředkovatel rolí ASP.NET zadáním názvů definovaných pro tyto dva zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="e0d55-121">In addition the behavior specifies that authentication of username-password pairs is performed by the ASP.NET membership provider and role mapping is performed by the ASP.NET role provider by specifying the names defined for the two providers.</span></span>  
  
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
  
 <span data-ttu-id="e0d55-122">Když spustíte ukázku, klient zavolá různé operace služby za tři různé uživatelské účty: Alice, Bob a Charlie.</span><span class="sxs-lookup"><span data-stu-id="e0d55-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="e0d55-123">Požadavky na operace a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="e0d55-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e0d55-124">Všechna čtyři volání vytvořená jako uživatel "Alice" by měla být úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e0d55-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="e0d55-125">Uživatel Bob by měl při pokusu o volání metody dělení získat chybu odepření přístupu.</span><span class="sxs-lookup"><span data-stu-id="e0d55-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="e0d55-126">Při pokusu o volání metody násobení by uživatel Charlie měl získat chybu odepření přístupu.</span><span class="sxs-lookup"><span data-stu-id="e0d55-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="e0d55-127">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="e0d55-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e0d55-128">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="e0d55-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e0d55-129">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0d55-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="e0d55-130">Ujistěte se, že jste nakonfigurovali [databázi ASP.NET aplikační služby](https://go.microsoft.com/fwlink/?LinkId=94997).</span><span class="sxs-lookup"><span data-stu-id="e0d55-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0d55-131">Pokud používáte edici SQL Server Express, název serveru je .\SQLEXPRESS.</span><span class="sxs-lookup"><span data-stu-id="e0d55-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="e0d55-132">Tento server by měl být použit při konfiguraci databáze ASP.NET Aplikační služby a také v připojovacím řetězci Web. config.</span><span class="sxs-lookup"><span data-stu-id="e0d55-132">This server should be used when configuring the ASP.NET Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0d55-133">Účet pracovního procesu ASP.NET musí mít oprávnění pro databázi, která je vytvořena v tomto kroku.</span><span class="sxs-lookup"><span data-stu-id="e0d55-133">The ASP.NET worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="e0d55-134">Provedete to pomocí nástroje Sqlcmd nebo SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="e0d55-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="e0d55-135">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="e0d55-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="e0d55-136">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="e0d55-136">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="e0d55-137">Ujistěte se, že cesta obsahuje složku, ve které se nachází nástroj Makecert. exe.</span><span class="sxs-lookup"><span data-stu-id="e0d55-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="e0d55-138">Spusťte Setup. bat z ukázkové instalační složky ve Developer Command Prompt pro Visual Studio spusťte s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="e0d55-138">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="e0d55-139">Tím se nainstaluje certifikát služby vyžadovaný pro spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="e0d55-139">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="e0d55-140">Spustit soubor Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="e0d55-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="e0d55-141">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="e0d55-141">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="e0d55-142">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e0d55-142">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="e0d55-143">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="e0d55-143">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="e0d55-144">Vytvořte adresář na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="e0d55-144">Create a directory on the service computer.</span></span> <span data-ttu-id="e0d55-145">Vytvořte virtuální aplikaci s názvem ServiceModelSamples pro tento adresář pomocí nástroje pro správu služby Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="e0d55-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="e0d55-146">Zkopírujte programové soubory služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="e0d55-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="e0d55-147">Ujistěte se, že jste zkopírovali soubory do podadresáře \Bin.</span><span class="sxs-lookup"><span data-stu-id="e0d55-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="e0d55-148">Zkopírujte také soubory Setup. bat, GetComputerName. vbs a Cleanup. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="e0d55-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="e0d55-149">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="e0d55-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="e0d55-150">Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="e0d55-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="e0d55-151">Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="e0d55-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="e0d55-152">Na serveru otevřete Developer Command Prompt pro Visual Studio s oprávněními správce a spusťte `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="e0d55-152">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="e0d55-153">Při `setup.bat` spuštění`service` s argumentem se vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.</span><span class="sxs-lookup"><span data-stu-id="e0d55-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="e0d55-154">Upravte soubor Web. config tak, aby odrážel nový název certifikátu ( `findValue` v atributu [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), který je stejný jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="e0d55-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="e0d55-155">Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="e0d55-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="e0d55-156">V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="e0d55-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="e0d55-157">V klientovi otevřete Developer Command Prompt pro Visual Studio s oprávněními správce a spusťte ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="e0d55-157">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="e0d55-158">Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="e0d55-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="e0d55-159">V klientském počítači spusťte z příkazového řádku soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="e0d55-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="e0d55-160">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e0d55-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="e0d55-161">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="e0d55-161">To clean up after the sample</span></span>  
  
- <span data-ttu-id="e0d55-162">Po dokončení ukázky Spusťte Cleanup. bat ve složce Samples.</span><span class="sxs-lookup"><span data-stu-id="e0d55-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0d55-163">Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi.</span><span class="sxs-lookup"><span data-stu-id="e0d55-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="e0d55-164">Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="e0d55-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="e0d55-165">K tomu použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="e0d55-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="e0d55-166">Instalační dávkový soubor</span><span class="sxs-lookup"><span data-stu-id="e0d55-166">The Setup Batch File</span></span>  
 <span data-ttu-id="e0d55-167">Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s příslušnými certifikáty pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="e0d55-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="e0d55-168">Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.</span><span class="sxs-lookup"><span data-stu-id="e0d55-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="e0d55-169">Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e0d55-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
- <span data-ttu-id="e0d55-170">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="e0d55-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="e0d55-171">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="e0d55-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="e0d55-172">Proměnná% Název_serveru% Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="e0d55-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="e0d55-173">Změňte tuto proměnnou tak, aby určovala vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="e0d55-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="e0d55-174">Tato dávková soubor se nastaví jako výchozí hodnota localhost.</span><span class="sxs-lookup"><span data-stu-id="e0d55-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="e0d55-175">Certifikát je uložený v osobním úložišti (osobní) v umístění úložiště LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="e0d55-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="e0d55-176">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="e0d55-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="e0d55-177">Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="e0d55-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="e0d55-178">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="e0d55-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="e0d55-179">Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="e0d55-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
