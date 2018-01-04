---
title: "Zprostředkovatel tokenu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 975014007ed57cc7e4b1035972923f61753c6d4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="token-provider"></a><span data-ttu-id="691e6-102">Zprostředkovatel tokenu</span><span class="sxs-lookup"><span data-stu-id="691e6-102">Token Provider</span></span>
<span data-ttu-id="691e6-103">Tento příklad znázorňuje způsob implementace vlastního zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="691e6-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="691e6-104">Zprostředkovatel tokenu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] slouží k poskytnutí přihlašovacích údajů k zabezpečení infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="691e6-104">A token provider in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="691e6-105">Zprostředkovatel tokenu obecně prozkoumá cíl a problémy vhodné přihlašovací údaje, aby infrastruktura zabezpečení můžete zabezpečit zprávy.</span><span class="sxs-lookup"><span data-stu-id="691e6-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="691e6-106">se dodává s výchozí zprostředkovatel tokenu správce přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="691e6-106"> ships with the default Credential Manager Token Provider.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="691e6-107">také se dodává s [!INCLUDE[infocard](../../../../includes/infocard-md.md)] zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="691e6-107"> also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="691e6-108">Vlastní poskytovatele tokenů jsou užitečné v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="691e6-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="691e6-109">Pokud máte úložiště přihlašovacích údajů, která tyto poskytovatele tokenů nemůže pracovat s.</span><span class="sxs-lookup"><span data-stu-id="691e6-109">If you have a credential store that these token providers cannot operate with.</span></span>  
  
-   <span data-ttu-id="691e6-110">Pokud chcete zadat vlastní vlastní mechanismus pro transformaci přihlašovací údaje z bodu, když uživatel nabízí podrobné informace do kdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta používá přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="691e6-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework uses the credentials.</span></span>  
  
-   <span data-ttu-id="691e6-111">Pokud vytváříte vlastní token.</span><span class="sxs-lookup"><span data-stu-id="691e6-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="691e6-112">Tento příklad ukazuje, jak vytvořit vlastní zprostředkovatele tokenů, který transformuje vstup od uživatele do jiného formátu.</span><span class="sxs-lookup"><span data-stu-id="691e6-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>  
  
 <span data-ttu-id="691e6-113">Tento příklad znázorňuje to Shrneme, následující:</span><span class="sxs-lookup"><span data-stu-id="691e6-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="691e6-114">Jak klienta můžete ověřit pomocí pár uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="691e6-114">How a client can authenticate using a username/password pair.</span></span>  
  
-   <span data-ttu-id="691e6-115">Jak klienta můžete nakonfigurovat vlastní zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="691e6-115">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="691e6-116">Jak server můžete ověřit pomocí vlastní heslo pověření klienta <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , ověří, zda se shodují uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="691e6-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>  
  
-   <span data-ttu-id="691e6-117">Jak server ověření klienta pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="691e6-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="691e6-118">Tento příklad také ukazuje, jak identitu volajícího je dostupné po dokončení procesu vlastních tokenů ověřování.</span><span class="sxs-lookup"><span data-stu-id="691e6-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>  
  
 <span data-ttu-id="691e6-119">Službu zpřístupní jeden koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="691e6-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="691e6-120">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="691e6-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="691e6-121">Vazba je nakonfigurována s standardní `wsHttpBinding`, který používá zabezpečení zpráv ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="691e6-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="691e6-122">Tato ukázka nastaví standardní `wsHttpBinding` používat uživatelské jméno ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="691e6-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="691e6-123">Služba nakonfiguruje taky certifikát služby pomocí – serviceCredentials chování.</span><span class="sxs-lookup"><span data-stu-id="691e6-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="691e6-124">Chování – serviceCredentials umožňuje nakonfigurovat certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="691e6-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="691e6-125">Certifikát služby se používá klient k ověření služby a zajištění ochrany zprávy.</span><span class="sxs-lookup"><span data-stu-id="691e6-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="691e6-126">Následující konfigurace odkazuje localhost certifikát nainstalovat během instalace ukázka, jak je popsáno v následujících pokynů pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="691e6-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- configure base address provided by host -->  
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="691e6-127">Konfigurace klienta koncový bod se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="691e6-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="691e6-128">Klient vazba je konfigurován s odpovídající `Mode` a zpráva `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="691e6-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="http://localhost:8000/servicemodelsamples/service"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator">  
    </endpoint>  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="691e6-129">Následující kroky ukazují, jak vyvíjet vlastní zprostředkovatele tokenu a integrovat s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="691e6-129">The following steps show how to develop a custom token provider and integrate it with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security framework:</span></span>  
  
1.  <span data-ttu-id="691e6-130">Napište vlastního zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="691e6-130">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="691e6-131">Ukázka implementuje vlastního zprostředkovatele tokenu, který získá uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="691e6-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="691e6-132">Heslo se musí shodovat toto uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="691e6-132">The password must match this username.</span></span> <span data-ttu-id="691e6-133">Tento vlastní zprostředkovatel tokenu je pouze pro demonstrační účely a nedoporučuje se používat pro reálné nasazení.</span><span class="sxs-lookup"><span data-stu-id="691e6-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>  
  
     <span data-ttu-id="691e6-134">K provedení této úlohy, poběží vlastní zprostředkovatel tokenu odvozuje <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy a přepsání <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="691e6-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="691e6-135">Tato metoda vytvoří a vrátí novou `UserNameSecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="691e6-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
        // obtain username and password from the user using console window  
        string username = GetUserName();  
        string password = GetPassword();  
        Console.WriteLine("username: {0}", username);  
  
        // return new UserNameSecurityToken containing information obtained from user  
        return new UserNameSecurityToken(username, password);  
    }  
    ```  
  
2.  <span data-ttu-id="691e6-136">Zápis tokenu správce vlastní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="691e6-136">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="691e6-137"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Se používá k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , je do ní předán v `CreateSecurityTokenProvider` metoda.</span><span class="sxs-lookup"><span data-stu-id="691e6-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="691e6-138">Správce tokenu zabezpečení se také používá k vytvoření tokenu ověřovací data a serializátor, ale nejsou uvedené v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="691e6-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="691e6-139">V této ukázce Správce tokenů zabezpečení vlastní dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenProvider` metoda vrátí zprostředkovatele tokenu vlastní uživatelské jméno v případě předaný tokenu požadavky znamenat tohoto zprostředkovatele uživatelské jméno je požadovaná.</span><span class="sxs-lookup"><span data-stu-id="691e6-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>  
  
    ```  
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager  
    {  
        MyUserNameClientCredentials myUserNameClientCredentials;  
  
        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)  
            : base(myUserNameClientCredentials)  
        {  
            this.myUserNameClientCredentials = myUserNameClientCredentials;  
        }  
  
        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)  
        {  
            // if token requirement matches username token return custom username token provider  
            // otherwise use base implementation  
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)  
            {  
                return new MyUserNameTokenProvider();  
            }  
            else  
            {  
                return base.CreateSecurityTokenProvider(tokenRequirement);  
            }  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="691e6-140">Zápis vlastních klientských pověření.</span><span class="sxs-lookup"><span data-stu-id="691e6-140">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="691e6-141">Třída pověření klienta se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro proxy server klienta a vytvoří token správce, který slouží k získání tokenu ověřovací data, poskytovatele tokenů a serializátoru tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="691e6-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>  
  
    ```  
    public class MyUserNameClientCredentials : ClientCredentials  
    {  
        public MyUserNameClientCredentials()  
            : base()  
        {  
        }  
  
        protected override ClientCredentials CloneCore()  
        {  
            return new MyUserNameClientCredentials();  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            // return custom security token manager  
            return new MyUserNameSecurityTokenManager(this);  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="691e6-142">Konfigurace klienta pro použití vlastního klienta přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="691e6-142">Configure the client to use the custom client credential.</span></span>  
  
     <span data-ttu-id="691e6-143">Aby klientovi použít přihlašovací údaje vlastního klienta vzorek odstraní výchozí třídu pověření klienta a poskytuje novou třídu pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="691e6-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```  
    static void Main()  
    {  
        // ...  
           // Create a client with given client endpoint configuration  
          CalculatorClient client = new CalculatorClient();  
  
          // set new credentials  
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));  
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());  
       // ...  
    }  
    ```  
  
 <span data-ttu-id="691e6-144">Na službu, použijte pro zobrazení informací volajícího, <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="691e6-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="691e6-145"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Obsahuje deklarace identity informace o aktuální volajícího.</span><span class="sxs-lookup"><span data-stu-id="691e6-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
        ServiceSecurityContext.Current.PrimaryIdentity.Name);  
}  
```  
  
 <span data-ttu-id="691e6-146">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="691e6-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="691e6-147">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="691e6-147">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="691e6-148">Instalační program dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="691e6-148">Setup Batch File</span></span>  
 <span data-ttu-id="691e6-149">Dávkový soubor Setup.bat součástí této ukázky můžete nakonfigurovat server se příslušný certifikát spuštění vlastním hostováním aplikace, která vyžaduje zabezpečení na základě certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="691e6-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="691e6-150">Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.</span><span class="sxs-lookup"><span data-stu-id="691e6-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="691e6-151">Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="691e6-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="691e6-152">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="691e6-152">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="691e6-153">Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="691e6-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="691e6-154">`%SERVER_NAME%` Proměnná Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="691e6-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="691e6-155">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="691e6-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="691e6-156">Výchozí hodnota v tomto souboru batch je localhost.</span><span class="sxs-lookup"><span data-stu-id="691e6-156">The default value in this batch file is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="691e6-157">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="691e6-157">Installing the server certificate into the client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="691e6-158">Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště.</span><span class="sxs-lookup"><span data-stu-id="691e6-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="691e6-159">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="691e6-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="691e6-160">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="691e6-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="691e6-161">Dávkový soubor Setup.bat slouží ke spuštění z Windows příkazový řádek SDK.</span><span class="sxs-lookup"><span data-stu-id="691e6-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="691e6-162">Se vyžaduje, aby proměnné prostředí MSSDK bodu na adresář, kam nainstalovat sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="691e6-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="691e6-163">Tato proměnná prostředí bude automaticky nastavena v příkazovém řádku Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="691e6-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="691e6-164">Jak nastavit a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="691e6-164">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="691e6-165">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="691e6-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="691e6-166">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="691e6-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="691e6-167">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="691e6-167">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="691e6-168">Spustit Setup.bat z instalační složky ukázka uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otevřít příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="691e6-168">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="691e6-169">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="691e6-169">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="691e6-170">Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="691e6-170">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="691e6-171">Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="691e6-171">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="691e6-172">Spusťte service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="691e6-172">Launch service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="691e6-173">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="691e6-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="691e6-174">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="691e6-174">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="691e6-175">Na řádku uživatelské jméno zadejte uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="691e6-175">At the username prompt, type a user name.</span></span>  
  
5.  <span data-ttu-id="691e6-176">Heslo řádku použijte stejný řetězec, který byl zadán pro výzvu uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="691e6-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6.  <span data-ttu-id="691e6-177">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="691e6-177">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="691e6-178">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="691e6-178">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="691e6-179">Vytvořte adresář na počítači se službou pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="691e6-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="691e6-180">Zkopírujte soubory programu služby do adresáře služby na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="691e6-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="691e6-181">Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="691e6-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="691e6-182">Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="691e6-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="691e6-183">Soubor Service.exe.config musí být aktualizovány tak, aby odrážela tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="691e6-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="691e6-184">Certifikát serveru můžete vytvořit úpravou Setup.bat dávkového souboru.</span><span class="sxs-lookup"><span data-stu-id="691e6-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="691e6-185">Všimněte si, že soubor setup.bat musí spouštět z příkazového řádku Visual Studia, otevřít s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="691e6-185">Note that the setup.bat file must be run from a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="691e6-186">Je nutné nastavit `%SERVER_NAME%` proměnnou hostitele plně kvalifikovaný název počítače, který se používá k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="691e6-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="691e6-187">Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="691e6-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="691e6-188">Není nutné k tomu, pokud je certifikát serveru vydána klienta důvěryhodného vystavitele.</span><span class="sxs-lookup"><span data-stu-id="691e6-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="691e6-189">V souboru Service.exe.config na počítači se službou změňte hodnotu z bázové adresy k zadání názvu počítače plně kvalifikovaný místo localhost.</span><span class="sxs-lookup"><span data-stu-id="691e6-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="691e6-190">Na počítači se službou spusťte z příkazového řádku service.exe.</span><span class="sxs-lookup"><span data-stu-id="691e6-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="691e6-191">Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.</span><span class="sxs-lookup"><span data-stu-id="691e6-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="691e6-192">V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="691e6-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="691e6-193">Na klientském počítači spusťte `Client.exe` z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="691e6-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="691e6-194">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="691e6-194">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="691e6-195">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="691e6-195">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="691e6-196">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="691e6-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691e6-197">Viz také</span><span class="sxs-lookup"><span data-stu-id="691e6-197">See Also</span></span>
