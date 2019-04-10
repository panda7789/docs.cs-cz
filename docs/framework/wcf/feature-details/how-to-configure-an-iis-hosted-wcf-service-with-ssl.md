---
title: 'Postupy: Konfigurace služby WCF hostované v IIS se SSL'
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 336c3800fc033cc12bd9c3fe168ae219b72cab91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214115"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="09561-102">Postupy: Konfigurace služby WCF hostované v IIS se SSL</span><span class="sxs-lookup"><span data-stu-id="09561-102">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="09561-103">Toto téma popisuje postup nastavení služby WCF hostované IIS pro použití zabezpečení přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="09561-103">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="09561-104">Zabezpečení přenosu HTTP vyžaduje certifikát SSL pro službu IIS zaregistrovat.</span><span class="sxs-lookup"><span data-stu-id="09561-104">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="09561-105">Pokud není certifikát SSL služby IIS můžete vygenerovat zkušební certifikát.</span><span class="sxs-lookup"><span data-stu-id="09561-105">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="09561-106">Dále musíte přidat vazbu SSL na webovou stránku a nakonfigurovat vlastnosti ověřování na webu.</span><span class="sxs-lookup"><span data-stu-id="09561-106">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="09561-107">Nakonec musíte nakonfigurovat službu WCF pro použití protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="09561-107">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="09561-108">Vytváří se certifikát podepsaný svým držitelem</span><span class="sxs-lookup"><span data-stu-id="09561-108">Creating a Self-Signed Certificate</span></span>  
  
1.  <span data-ttu-id="09561-109">Otevřete Správce Internetové informační služby (inetmgr.exe) a vyberte název počítače v zobrazení stromu vlevo.</span><span class="sxs-lookup"><span data-stu-id="09561-109">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="09561-110">Na pravé straně obrazovky vyberte certifikáty serveru</span><span class="sxs-lookup"><span data-stu-id="09561-110">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="09561-111">![Správce služby IIS domovské obrazovce](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="09561-111">![IIS Manager Home Screen](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2.  <span data-ttu-id="09561-112">V okně certifikáty serveru klikněte na tlačítko **vytvořit certifikát podepsaný svým držitelem...**</span><span class="sxs-lookup"><span data-stu-id="09561-112">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="09561-113">odkaz.</span><span class="sxs-lookup"><span data-stu-id="09561-113">Link.</span></span>  
  
     <span data-ttu-id="09561-114">![Vytváří se svým&#45;podepsaný certifikát s IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="09561-114">![Creating a self&#45;signed certificate with IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3.  <span data-ttu-id="09561-115">Zadejte popisný název certifikátu podepsaného svým držitelem a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="09561-115">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="09561-116">![Create Self&#45;Signed Certificate Dialog](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="09561-116">![Create Self&#45;Signed Certificate Dialog](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="09561-117">Podrobnosti nově vytvořeného certifikátu podepsaného svým držitelem se teď zobrazují v **certifikáty serveru** okna.</span><span class="sxs-lookup"><span data-stu-id="09561-117">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="09561-118">![Okno certifikátu serveru](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="09561-118">![Server Certificate Window](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="09561-119">Vygenerovaný certifikát nainstalován v důvěryhodné kořenové certifikační autority úložiště.</span><span class="sxs-lookup"><span data-stu-id="09561-119">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="09561-120">Add SSL Binding</span><span class="sxs-lookup"><span data-stu-id="09561-120">Add SSL Binding</span></span>  
  
1.  <span data-ttu-id="09561-121">Stále v Správce Internetové informační služby, rozbalte **lokality** složku a potom **výchozí webový server** složky ve stromovém zobrazení na levé straně obrazovky.</span><span class="sxs-lookup"><span data-stu-id="09561-121">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2.  <span data-ttu-id="09561-122">Klikněte na tlačítko **vazby...**</span><span class="sxs-lookup"><span data-stu-id="09561-122">Click the **Bindings….**</span></span> <span data-ttu-id="09561-123">Propojit **akce** části v pravé horní části okna.</span><span class="sxs-lookup"><span data-stu-id="09561-123">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="09561-124">![Přidání vazby SSL](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="09561-124">![Adding an SSL binding](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3.  <span data-ttu-id="09561-125">V okně vazby webu klikněte na tlačítko **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="09561-125">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="09561-126">![Dialogové okno vazby webu](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="09561-126">![Site Bindings Dialog](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4.  <span data-ttu-id="09561-127">V **přidat vazbu webu** dialogového okna, vyberte https pro typ a popisný název certifikátu podepsaného svým držitelem, jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="09561-127">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="09561-128">![Příklad vazby webu](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="09561-128">![Site binding example](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="09561-129">Nakonfigurujte virtuální adresář pro protokol SSL</span><span class="sxs-lookup"><span data-stu-id="09561-129">Configure Virtual Directory for SSL</span></span>  
  
1.  <span data-ttu-id="09561-130">Stále v Správce Internetové informační služby vyberte virtuální adresář, který obsahuje vaše zabezpečenou službu WCF.</span><span class="sxs-lookup"><span data-stu-id="09561-130">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2.  <span data-ttu-id="09561-131">V prostředním podokně okna, vyberte **nastavení SSL** v části služby IIS.</span><span class="sxs-lookup"><span data-stu-id="09561-131">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="09561-132">![Nastavení SSL pro virtuální adresář](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="09561-132">![SSL Settings for virtual directory](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3.  <span data-ttu-id="09561-133">V podokně nastavení protokolu SSL, vyberte **požadovat protokol SSL** zaškrtávací políčko a klikněte na tlačítko **použít** odkaz v **akce** části na pravé straně obrazovky.</span><span class="sxs-lookup"><span data-stu-id="09561-133">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="09561-134">![Nastavení SSL virtuální adresář](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="09561-134">![Virtual directory SSL settings](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="09561-135">Konfigurace služby WCF pro zabezpečení přenosu HTTP</span><span class="sxs-lookup"><span data-stu-id="09561-135">Configure WCF Service for HTTP Transport Security</span></span>  
  
1.  <span data-ttu-id="09561-136">Ve WCF služby web.config nakonfigurovat vazbu HTTP pro použití zabezpečení přenosu, jak je znázorněno v následujícím souboru XML.</span><span class="sxs-lookup"><span data-stu-id="09561-136">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
    ```xml  
    <bindings>  
          <basicHttpBinding>  
            <binding name="secureHttpBinding">  
              <security mode="Transport">  
                <transport clientCredentialType="None"/>  
              </security>  
            </binding>  
          </basicHttpBinding>  
    </bindings>  
    ```  
  
2.  <span data-ttu-id="09561-137">Zadejte vaše služby a koncového bodu služby, jak je znázorněno v následujícím souboru XML.</span><span class="sxs-lookup"><span data-stu-id="09561-137">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
    ```xml  
    <services>  
          <service name="MySecureWCFService.Service1">  
            <endpoint address=""  
                      binding="basicHttpBinding"  
                      bindingConfiguration="secureHttpBinding"  
                      contract="MySecureWCFService.IService1"/>  
  
            <endpoint address="mex"  
                      binding="mexHttpsBinding"  
                      contract="IMetadataExchange" />  
          </service>  
    </services>  
    ```  
  
## <a name="example"></a><span data-ttu-id="09561-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="09561-138">Example</span></span>  
 <span data-ttu-id="09561-139">Následuje Úplný příklad souboru web.config pro služby WCF pomocí zabezpečení přenosu HTTP</span><span class="sxs-lookup"><span data-stu-id="09561-139">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <services>  
      <service name="MySecureWCFService.Service1">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="secureHttpBinding"  
                  contract="MySecureWCFService.IService1"/>  
  
        <endpoint address="mex"  
                  binding="mexHttpsBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="secureHttpBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <!-- To avoid disclosing metadata information, set the value below to false and remove the metadata endpoint above before deployment -->  
          <serviceMetadata httpsGetEnabled="true"/>  
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
  </system.serviceModel>  
  <system.webServer>  
    <modules runAllManagedModulesForAllRequests="true"/>  
  </system.webServer>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09561-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09561-140">See also</span></span>

- [<span data-ttu-id="09561-141">Hostování v Internetové informační službě</span><span class="sxs-lookup"><span data-stu-id="09561-141">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [<span data-ttu-id="09561-142">Pokyny k hostování služby IIS</span><span class="sxs-lookup"><span data-stu-id="09561-142">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="09561-143">Doporučené postupy hostování Internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="09561-143">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="09561-144">Hostování IIS pomocí vloženého kódu</span><span class="sxs-lookup"><span data-stu-id="09561-144">IIS Hosting Using Inline Code</span></span>](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
