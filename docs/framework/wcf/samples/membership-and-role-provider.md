---
title: "Členství a poskytovatel rolí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b57fbd3788d6fd040f8781325202dd86790d385
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="bc22a-102">Členství a poskytovatel rolí</span><span class="sxs-lookup"><span data-stu-id="bc22a-102">Membership and Role Provider</span></span>
<span data-ttu-id="bc22a-103">Ukázka členství a poskytovatel rolí ukazuje, jak můžete použít službu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství a rolí k ověřování a autorizaci klientů.</span><span class="sxs-lookup"><span data-stu-id="bc22a-103">The Membership and Role Provider sample demonstrates how a service can use the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="bc22a-104">V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="bc22a-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc22a-105">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="bc22a-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bc22a-106">Ukázka ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="bc22a-106">The sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="bc22a-107">Klienta můžete ověřit pomocí kombinace hesla uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="bc22a-107">A client can authenticate by using the username-password combination.</span></span>  
  
-   <span data-ttu-id="bc22a-108">Server můžete ověřit pověření klienta vůči [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství.</span><span class="sxs-lookup"><span data-stu-id="bc22a-108">The server can validate the client credentials against the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
-   <span data-ttu-id="bc22a-109">Server lze ověřit pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="bc22a-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
-   <span data-ttu-id="bc22a-110">Server můžete namapovat ověřeného klienta do role pomocí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí.</span><span class="sxs-lookup"><span data-stu-id="bc22a-110">The server can map the authenticated client to a role by using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider.</span></span>  
  
-   <span data-ttu-id="bc22a-111">Server můžete použít `PrincipalPermissionAttribute` pro řízení přístupu k některé metody, které jsou zveřejněné službou.</span><span class="sxs-lookup"><span data-stu-id="bc22a-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="bc22a-112">Zprostředkovatele členství a role jsou nakonfigurovány pro použití úložiště zajišťoval podporu systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc22a-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="bc22a-113">Připojovací řetězec a různé možnosti jsou určené v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="bc22a-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="bc22a-114">Zprostředkovatel členství je zadaný název `SqlMembershipProvider` při zprostředkovatele rolí je zadaný název `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="bc22a-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
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
  
 <span data-ttu-id="bc22a-115">Službu zpřístupní jeden koncový bod pro komunikaci se službou, která je definovaná pomocí konfiguračního souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="bc22a-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="bc22a-116">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="bc22a-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="bc22a-117">Vazba je nakonfigurována s standardní `wsHttpBinding`, který ve výchozím nastavení používá ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bc22a-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="bc22a-118">Tato ukázka nastaví standardní `wsHttpBinding` používat ověřování uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="bc22a-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="bc22a-119">Chování Určuje, zda má být použit pro ověřování služby je certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="bc22a-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="bc22a-120">Certifikát serveru musí obsahovat stejné hodnoty `SubjectName` jako `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) konfigurační prvek.</span><span class="sxs-lookup"><span data-stu-id="bc22a-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="bc22a-121">Kromě chování Určuje, že ověřování hesla uživatelské jméno páry provádí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství a role mapování provádí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí tak, že zadáte názvy definované pro dva poskytovatelé.</span><span class="sxs-lookup"><span data-stu-id="bc22a-121">In addition the behavior specifies that authentication of username-password pairs is performed by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider and role mapping is performed by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider by specifying the names defined for the two providers.</span></span>  
  
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
  
 <span data-ttu-id="bc22a-122">Při spuštění vzorového klienta volá různých operací služby v části tři různé uživatelské účty: Alici, Roberta a Karel.</span><span class="sxs-lookup"><span data-stu-id="bc22a-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="bc22a-123">Operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="bc22a-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bc22a-124">Všechny čtyři volání jako uživatel, že by měl být úspěšné "Alice".</span><span class="sxs-lookup"><span data-stu-id="bc22a-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="bc22a-125">Uživatel "Bob" měli obdržet chybu při pokusu o volání metody dělení odepření přístupu.</span><span class="sxs-lookup"><span data-stu-id="bc22a-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="bc22a-126">Uživatel "Karel" měli získat chybu při pokusu o volání odepření přístupu násobení metoda.</span><span class="sxs-lookup"><span data-stu-id="bc22a-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="bc22a-127">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="bc22a-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bc22a-128">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="bc22a-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bc22a-129">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bc22a-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="bc22a-130">Ujistěte se, že jste nakonfigurovali [databáze aplikačních služeb ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94997).</span><span class="sxs-lookup"><span data-stu-id="bc22a-130">Ensure that you have configured the [ASP.NET Application Services Database](http://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc22a-131">Pokud používáte systém SQL Server Express Edition, je název serveru. \SQLEXPRESS.</span><span class="sxs-lookup"><span data-stu-id="bc22a-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="bc22a-132">Tento server se musí použít při konfiguraci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikační služby databáze také jako připojovací řetězec souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="bc22a-132">This server should be used when configuring the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc22a-133">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Účet pracovního procesu musí mít oprávnění v databázi, který se vytvoří v tomto kroku.</span><span class="sxs-lookup"><span data-stu-id="bc22a-133">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="bc22a-134">K tomu použijte nástroj sqlcmd nebo SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="bc22a-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3.  <span data-ttu-id="bc22a-135">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, použijte následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="bc22a-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="bc22a-136">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="bc22a-136">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="bc22a-137">Ujistěte se, že cesta obsahuje složku, kde je umístěna Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="bc22a-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2.  <span data-ttu-id="bc22a-138">Spuštění Setup.bat od vzorku instalační složku v sadě Visual Studio příkazovém řádku spusťte s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="bc22a-138">Run Setup.bat from the sample install folder in a Visual Studio command prompt run with administrator privileges.</span></span> <span data-ttu-id="bc22a-139">Tím se nainstaluje potřebné ke spuštění ukázky certifikáty služeb.</span><span class="sxs-lookup"><span data-stu-id="bc22a-139">This installs the service certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="bc22a-140">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="bc22a-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="bc22a-141">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="bc22a-141">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="bc22a-142">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="bc22a-142">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="bc22a-143">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="bc22a-143">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="bc22a-144">Vytvořte adresář na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="bc22a-144">Create a directory on the service computer.</span></span> <span data-ttu-id="bc22a-145">Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="bc22a-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="bc22a-146">Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="bc22a-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="bc22a-147">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="bc22a-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="bc22a-148">Taky zkopírujte soubory Setup.bat, GetComputerName.vbs a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="bc22a-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="bc22a-149">Vytvořte adresář na klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="bc22a-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="bc22a-150">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="bc22a-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="bc22a-151">Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="bc22a-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="bc22a-152">Na serveru, otevřete příkazový řádek sady Visual Studio s oprávněními správce a spusťte `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="bc22a-152">On the server, open a Visual Studio command prompt with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="bc22a-153">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="bc22a-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="bc22a-154">Upravit soubor Web.config tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), což je stejný jako název plně kvalifikované domény počítače.</span><span class="sxs-lookup"><span data-stu-id="bc22a-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="bc22a-155">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="bc22a-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="bc22a-156">V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="bc22a-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="bc22a-157">Na klientovi otevřete příkazový řádek sady Visual Studio s oprávněními správce a spusťte ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="bc22a-157">On the client, open a Visual Studio command prompt with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="bc22a-158">Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="bc22a-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="bc22a-159">Na klientském počítači spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="bc22a-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="bc22a-160">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="bc22a-160">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="bc22a-161">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="bc22a-161">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="bc22a-162">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="bc22a-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc22a-163">Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="bc22a-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="bc22a-164">Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="bc22a-164">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="bc22a-165">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="bc22a-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="bc22a-166">Instalační program dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="bc22a-166">The Setup Batch File</span></span>  
 <span data-ttu-id="bc22a-167">Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění vlastním hostováním aplikace, která vyžaduje zabezpečení na základě certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="bc22a-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="bc22a-168">Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.</span><span class="sxs-lookup"><span data-stu-id="bc22a-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="bc22a-169">Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="bc22a-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="bc22a-170">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="bc22a-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="bc22a-171">Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="bc22a-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="bc22a-172">Proměnná % název_serveru % Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="bc22a-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="bc22a-173">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="bc22a-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="bc22a-174">Tento dávkový soubor použije se výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="bc22a-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="bc22a-175">Certifikát je uložen v tomto úložišti (osobních) v části LocalMachine umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="bc22a-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="bc22a-176">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="bc22a-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="bc22a-177">Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště.</span><span class="sxs-lookup"><span data-stu-id="bc22a-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="bc22a-178">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="bc22a-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="bc22a-179">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="bc22a-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bc22a-180">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc22a-180">See Also</span></span>
