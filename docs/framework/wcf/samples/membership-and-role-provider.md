---
title: Členství a poskytovatel rolí
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: 117be783c2d4a72ff9d1c4509566274b1043a43d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144458"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="0dd44-102">Členství a poskytovatel rolí</span><span class="sxs-lookup"><span data-stu-id="0dd44-102">Membership and Role Provider</span></span>
<span data-ttu-id="0dd44-103">Ukázka členství a zprostředkovatele rolí ukazuje, jak může služba používat ASP.NET poskytovatele členství a rolí k ověřování a autorizaci klientů.</span><span class="sxs-lookup"><span data-stu-id="0dd44-103">The Membership and Role Provider sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="0dd44-104">V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="0dd44-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0dd44-105">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0dd44-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0dd44-106">Vzorek ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="0dd44-106">The sample demonstrates how:</span></span>  
  
- <span data-ttu-id="0dd44-107">Klient se může ověřit pomocí kombinace uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="0dd44-107">A client can authenticate by using the username-password combination.</span></span>  
  
- <span data-ttu-id="0dd44-108">Server může ověřit pověření klienta vůči poskytovateli členství ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0dd44-108">The server can validate the client credentials against the ASP.NET membership provider.</span></span>  
  
- <span data-ttu-id="0dd44-109">Server lze ověřit pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="0dd44-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
- <span data-ttu-id="0dd44-110">Server může namapovat ověřeného klienta na roli pomocí ASP.NET zprostředkovatele rolí.</span><span class="sxs-lookup"><span data-stu-id="0dd44-110">The server can map the authenticated client to a role by using the ASP.NET role provider.</span></span>  
  
- <span data-ttu-id="0dd44-111">Server můžete použít `PrincipalPermissionAttribute` k řízení přístupu k určité metody, které jsou vystaveny službou.</span><span class="sxs-lookup"><span data-stu-id="0dd44-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="0dd44-112">Poskytovatelé členství a rolí jsou nakonfigurováni tak, aby používali úložiště podporované sql serverem.</span><span class="sxs-lookup"><span data-stu-id="0dd44-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="0dd44-113">Připojovací řetězec a různé možnosti jsou určeny v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="0dd44-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="0dd44-114">Poskytovatel členství je uveden `SqlMembershipProvider` název, zatímco zprostředkovatel `SqlRoleProvider`role je uveden název .</span><span class="sxs-lookup"><span data-stu-id="0dd44-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
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
  
 <span data-ttu-id="0dd44-115">Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, která je definována pomocí konfiguračního souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="0dd44-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="0dd44-116">Koncový bod se skládá z adresy, vazby a smlouvy.</span><span class="sxs-lookup"><span data-stu-id="0dd44-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="0dd44-117">Vazba je konfigurována `wsHttpBinding`se standardem , který je ve výchozím nastavení nastaven na ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0dd44-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="0dd44-118">Tato ukázka `wsHttpBinding` nastaví standard pro použití ověřování uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="0dd44-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="0dd44-119">Chování určuje, že certifikát serveru má být použit pro ověřování služby.</span><span class="sxs-lookup"><span data-stu-id="0dd44-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="0dd44-120">Certifikát serveru musí obsahovat stejnou `SubjectName` hodnotu jako `findValue` atribut v prvku [ \<konfigurace serviceCertificate>.](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="0dd44-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="0dd44-121">Kromě toho chování určuje, že ověřování párů uživatelského jména a hesla provádí poskytovatel členství ASP.NET a mapování rolí provádí poskytovatel role ASP.NET zadáním názvů definovaných pro dva zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="0dd44-121">In addition the behavior specifies that authentication of username-password pairs is performed by the ASP.NET membership provider and role mapping is performed by the ASP.NET role provider by specifying the names defined for the two providers.</span></span>  
  
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
  
 <span data-ttu-id="0dd44-122">Při spuštění ukázky klient volá různé operace služby pod tři různé uživatelské účty: Alice, Bob a Charlie.</span><span class="sxs-lookup"><span data-stu-id="0dd44-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="0dd44-123">Požadavky na operaci a odpovědi jsou zobrazeny v okně klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="0dd44-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0dd44-124">Všechny čtyři volání jako uživatel "Alice" by měl být úspěšný.</span><span class="sxs-lookup"><span data-stu-id="0dd44-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="0dd44-125">Uživatel "Bob" by měl získat chybu odepřen přístup při pokusu o volání Divide metoda.</span><span class="sxs-lookup"><span data-stu-id="0dd44-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="0dd44-126">Uživatel "Charlie" by měl získat chybu odepřen přístup při pokusu o volání Multiply metoda.</span><span class="sxs-lookup"><span data-stu-id="0dd44-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="0dd44-127">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="0dd44-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0dd44-128">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="0dd44-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0dd44-129">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [spuštění windows communication foundation ukázky](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0dd44-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="0dd44-130">Ujistěte se, že jste nakonfigurovali [databázi ASP.NET aplikačních služeb](https://go.microsoft.com/fwlink/?LinkId=94997).</span><span class="sxs-lookup"><span data-stu-id="0dd44-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0dd44-131">Pokud používáte sql server Express Edition, název serveru je .\SQLEXPRESS.</span><span class="sxs-lookup"><span data-stu-id="0dd44-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="0dd44-132">Tento server by měl být použit při konfiguraci databáze ASP.NET aplikačních služeb a také v připojovacím řetězci Web.config.</span><span class="sxs-lookup"><span data-stu-id="0dd44-132">This server should be used when configuring the ASP.NET Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0dd44-133">Účet ASP.NET pracovního procesu musí mít oprávnění k databázi, která je vytvořena v tomto kroku.</span><span class="sxs-lookup"><span data-stu-id="0dd44-133">The ASP.NET worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="0dd44-134">K tomu použijte nástroj sqlcmd nebo SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="0dd44-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="0dd44-135">Chcete-li vzorek spustit v konfiguraci jednoho nebo mezi počítači, postupujte podle následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="0dd44-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="0dd44-136">Spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="0dd44-136">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="0dd44-137">Ujistěte se, že cesta obsahuje složku, kde je umístěn makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="0dd44-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="0dd44-138">Spusťte soubor Setup.bat z ukázkové instalační složky v příkazovém řádku pro vývojáře pro aplikaci Visual Studio, která je spuštěna s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="0dd44-138">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="0dd44-139">Tím nainstalujete certifikáty služby potřebné pro spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="0dd44-139">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="0dd44-140">Spusťte soubor Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="0dd44-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="0dd44-141">Aktivita klienta je zobrazena v aplikaci klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="0dd44-141">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="0dd44-142">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="0dd44-142">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="0dd44-143">Spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="0dd44-143">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="0dd44-144">Vytvořte adresář v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="0dd44-144">Create a directory on the service computer.</span></span> <span data-ttu-id="0dd44-145">Vytvořte virtuální aplikaci s názvem ServiceModelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="0dd44-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="0dd44-146">Zkopírujte soubory servisních programů ze vzorků \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="0dd44-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="0dd44-147">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="0dd44-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="0dd44-148">Zkopírujte také soubory Setup.bat, GetComputerName.vbs a Cleanup.bat do servisního počítače.</span><span class="sxs-lookup"><span data-stu-id="0dd44-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="0dd44-149">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="0dd44-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="0dd44-150">Zkopírujte soubory klientských programů do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="0dd44-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="0dd44-151">Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="0dd44-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="0dd44-152">Na serveru otevřete příkazový řádek pro vývojáře pro `setup.bat service`visual studio s oprávněními správce a spusťte .</span><span class="sxs-lookup"><span data-stu-id="0dd44-152">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="0dd44-153">Spuštění `setup.bat` s `service` argumentem vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="0dd44-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="0dd44-154">Upravte web.config tak, aby odrážel `findValue` nový název certifikátu (v atributu [ \<v serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), který je stejný jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="0dd44-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="0dd44-155">Zkopírujte soubor Service.cer z adresáře služby do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="0dd44-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="0dd44-156">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="0dd44-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="0dd44-157">Na straně klienta otevřete příkazový řádek pro vývojáře pro visual studio s oprávněními správce a spusťte soubor ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="0dd44-157">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="0dd44-158">Tím se importuje certifikát služby ze souboru Service.cer do úložiště CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="0dd44-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="0dd44-159">V klientském počítači spusťte soubor Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0dd44-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="0dd44-160">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="0dd44-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="0dd44-161">Chcete-li vyčistit po vzorku</span><span class="sxs-lookup"><span data-stu-id="0dd44-161">To clean up after the sample</span></span>  
  
- <span data-ttu-id="0dd44-162">Spusťte cleanup.bat ve složce ukázky po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="0dd44-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0dd44-163">Tento skript neodebere certifikáty služeb v klientovi při spuštění této ukázky v počítačích.</span><span class="sxs-lookup"><span data-stu-id="0dd44-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="0dd44-164">Pokud jste schovali ukázky WCF (Windows Communication Foundation), které používají certifikáty v počítačích, nezapomeňte vymazat certifikáty služeb, které byly nainstalovány v úložišti CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="0dd44-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="0dd44-165">Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` použijte následující `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`příkaz: Například: .</span><span class="sxs-lookup"><span data-stu-id="0dd44-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="0dd44-166">Dávkový soubor instalace</span><span class="sxs-lookup"><span data-stu-id="0dd44-166">The Setup Batch File</span></span>  
 <span data-ttu-id="0dd44-167">Dávkový soubor Setup.bat, který je součástí této ukázky, umožňuje nakonfigurovat server s příslušnými certifikáty tak, aby spouštěl samoobslužnou aplikaci, která vyžaduje zabezpečení založené na certifikátech serveru.</span><span class="sxs-lookup"><span data-stu-id="0dd44-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="0dd44-168">Tento dávkový soubor musí být upraven tak, aby fungoval napříč počítači nebo aby fungoval v nehostovaném případě.</span><span class="sxs-lookup"><span data-stu-id="0dd44-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="0dd44-169">Následující text poskytuje stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby byly spuštěny v příslušné konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="0dd44-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
- <span data-ttu-id="0dd44-170">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="0dd44-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="0dd44-171">Následující řádky z dávkového souboru Setup.bat vytvoří certifikát serveru, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="0dd44-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="0dd44-172">Proměnná %SERVER_NAME% určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="0dd44-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="0dd44-173">Změňte tuto proměnnou a zadejte vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="0dd44-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="0dd44-174">Tento dávkový soubor je výchozí pro localhost.</span><span class="sxs-lookup"><span data-stu-id="0dd44-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="0dd44-175">Certifikát je uložen v úložišti Moje (osobní) pod umístěním úložiště LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="0dd44-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="0dd44-176">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="0dd44-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="0dd44-177">Následující řádky v dávkovém souboru Setup.bat zkopírují certifikát serveru do úložiště důvěryhodných osob klienta.</span><span class="sxs-lookup"><span data-stu-id="0dd44-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="0dd44-178">Tento krok je vyžadován, protože certifikáty generované programem Makecert.exe nejsou klientským systémem implicitně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="0dd44-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="0dd44-179">Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem certifikátem serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="0dd44-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
