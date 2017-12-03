---
title: "Postupy: Konfigurace služby WCF hostované IIS pomocí protokolu SSL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e43aca439ee354557cac42ba88599b6ea105b097
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="7b5e8-102">Postupy: Konfigurace služby WCF hostované IIS pomocí protokolu SSL</span><span class="sxs-lookup"><span data-stu-id="7b5e8-102">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="7b5e8-103">Toto téma popisuje postup nastavení služby WCF hostované IIS pro použití zabezpečení přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-103">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="7b5e8-104">Zabezpečení přenosu HTTP vyžaduje certifikát SSL zaregistrovat u služby IIS.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-104">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="7b5e8-105">Pokud není certifikát SSL, že které lze použít k vygenerování testu certifikátu služby IIS.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-105">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="7b5e8-106">Dále musíte přidání vazby SSL na web a nakonfigurovat vlastnosti ověřování na webu.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-106">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="7b5e8-107">Nakonec budete muset konfigurovat službu WCF pro použití protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-107">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="7b5e8-108">Vytvořit certifikát podepsaný svým držitelem</span><span class="sxs-lookup"><span data-stu-id="7b5e8-108">Creating a Self-Signed Certificate</span></span>  
  
1.  <span data-ttu-id="7b5e8-109">Otevřete Správce Internetové informační služby (inetmgr.exe) a vyberte v levé stromovém zobrazení názvu vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-109">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="7b5e8-110">Na pravé straně obrazovky vyberte certifikáty serveru</span><span class="sxs-lookup"><span data-stu-id="7b5e8-110">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="7b5e8-111">![Správce služby IIS domovské obrazovce](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="7b5e8-111">![IIS Manager Home Screen](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2.  <span data-ttu-id="7b5e8-112">V okně certifikáty serveru klikněte na **vytvořit certifikát podepsaný svým držitelem...**</span><span class="sxs-lookup"><span data-stu-id="7b5e8-112">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="7b5e8-113">Odkaz.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-113">Link.</span></span>  
  
     <span data-ttu-id="7b5e8-114">![Vytváření svým & č. 45; podepsaný certifikát se službou IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="7b5e8-114">![Creating a self&#45;signed certificate with IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3.  <span data-ttu-id="7b5e8-115">Zadejte popisný název certifikátu podepsaného svým držitelem a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-115">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="7b5e8-116">![Vytvoření vlastního & č. 45; Dialogové okno certifikát podepsaný](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="7b5e8-116">![Create Self&#45;Signed Certificate Dialog](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="7b5e8-117">Podrobnosti o nově vytvořený certifikát podepsaný svým držitelem se teď zobrazují v **certifikáty serveru** okno.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-117">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="7b5e8-118">![Okno certifikát serveru](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="7b5e8-118">![Server Certificate Window](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="7b5e8-119">Vygenerovaný certifikát nainstalován v důvěryhodné kořenové certifikační autority uložit.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-119">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="7b5e8-120">Přidat vazbu SSL</span><span class="sxs-lookup"><span data-stu-id="7b5e8-120">Add SSL Binding</span></span>  
  
1.  <span data-ttu-id="7b5e8-121">Stále v Správce Internetové informační služby, rozbalte **lokality** složku a potom **Default Web Site** složky ve stromovém zobrazení na levé straně obrazovky.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-121">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2.  <span data-ttu-id="7b5e8-122">Klikněte **vazby...**</span><span class="sxs-lookup"><span data-stu-id="7b5e8-122">Click the **Bindings….**</span></span> <span data-ttu-id="7b5e8-123">Odkaz **akce** část v pravé horní části okna.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-123">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="7b5e8-124">![Přidání vazby SSL](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="7b5e8-124">![Adding an SSL binding](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3.  <span data-ttu-id="7b5e8-125">V okně vazby serveru klikněte na **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-125">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="7b5e8-126">![Dialogové okno vazby webu](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="7b5e8-126">![Site Bindings Dialog](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4.  <span data-ttu-id="7b5e8-127">V **přidat vazbu webu** dialogovém okně, vyberte https pro typ a popisný název certifikátu podepsaného svým držitelem jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-127">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="7b5e8-128">![Příklad vazby webu](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="7b5e8-128">![Site binding example](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="7b5e8-129">Nakonfigurujte virtuální adresář pro protokol SSL</span><span class="sxs-lookup"><span data-stu-id="7b5e8-129">Configure Virtual Directory for SSL</span></span>  
  
1.  <span data-ttu-id="7b5e8-130">Stále v Správce Internetové informační služby vyberte virtuálního adresáře, který obsahuje zabezpečené služby WCF.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-130">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2.  <span data-ttu-id="7b5e8-131">V prostředním podokně okna vyberte **nastavení SSL** v části služby IIS.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-131">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="7b5e8-132">![Nastavení SSL pro virtuální adresář](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="7b5e8-132">![SSL Settings for virtual directory](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3.  <span data-ttu-id="7b5e8-133">V podokně nastavení protokolu SSL, vyberte **požadovat protokol SSL** zaškrtávací políčko a klikněte na tlačítko **použít** na odkaz v **akce** části na pravé straně obrazovky.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-133">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="7b5e8-134">![Nastavení SSL virtuální adresář](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="7b5e8-134">![Virtual directory SSL settings](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="7b5e8-135">Konfigurace služby WCF pro zabezpečení přenosu HTTP</span><span class="sxs-lookup"><span data-stu-id="7b5e8-135">Configure WCF Service for HTTP Transport Security</span></span>  
  
1.  <span data-ttu-id="7b5e8-136">Ve WCF web.config služby konfiguraci vazby HTTP pro použití zabezpečení přenosu, jak je znázorněno v následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-136">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
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
  
2.  <span data-ttu-id="7b5e8-137">Zadejte službu a koncový bod služby, jak je znázorněno v následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="7b5e8-137">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="7b5e8-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b5e8-138">Example</span></span>  
 <span data-ttu-id="7b5e8-139">Úplný příklad souboru web.config pro službu WCF pomocí zabezpečení přenosu HTTP</span><span class="sxs-lookup"><span data-stu-id="7b5e8-139">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7b5e8-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b5e8-140">See Also</span></span>  
 [<span data-ttu-id="7b5e8-141">Hostování v Internetové informační službě</span><span class="sxs-lookup"><span data-stu-id="7b5e8-141">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="7b5e8-142">Internetové informace o pokyny k hostování služby</span><span class="sxs-lookup"><span data-stu-id="7b5e8-142">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [<span data-ttu-id="7b5e8-143">Doporučené postupy hostování internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="7b5e8-143">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [<span data-ttu-id="7b5e8-144">Hostování IIS pomocí vloženého kódu</span><span class="sxs-lookup"><span data-stu-id="7b5e8-144">IIS Hosting Using Inline Code</span></span>](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
