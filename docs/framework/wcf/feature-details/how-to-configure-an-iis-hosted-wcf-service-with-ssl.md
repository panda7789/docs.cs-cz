---
title: 'Postupy: Konfigurace služby WCF hostované v IIS se SSL'
description: Přečtěte si, jak nastavit službu WCF hostovanou službou IIS pro použití zabezpečení přenosu HTTP, což vyžaduje certifikát zaregistrovaný ve službě IIS.
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 8dc4692863d93e407a122c0ba93ae38323b8b213
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245255"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="e653e-103">Postupy: Konfigurace služby WCF hostované v IIS se SSL</span><span class="sxs-lookup"><span data-stu-id="e653e-103">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="e653e-104">Toto téma popisuje, jak nastavit službu WCF hostovanou službou IIS pro použití zabezpečení přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e653e-104">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="e653e-105">Zabezpečení přenosu HTTP vyžaduje, aby byl certifikát SSL zaregistrován ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="e653e-105">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="e653e-106">Pokud nemáte certifikát SSL, můžete k vygenerování testovacího certifikátu použít službu IIS.</span><span class="sxs-lookup"><span data-stu-id="e653e-106">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="e653e-107">Dále musíte přidat vazbu SSL na web a nakonfigurovat vlastnosti ověřování webu.</span><span class="sxs-lookup"><span data-stu-id="e653e-107">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="e653e-108">Nakonec musíte nakonfigurovat službu WCF tak, aby používala protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e653e-108">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="e653e-109">Vytvoření certifikátu podepsaného svým držitelem</span><span class="sxs-lookup"><span data-stu-id="e653e-109">Creating a Self-Signed Certificate</span></span>  
  
1. <span data-ttu-id="e653e-110">Otevřete Internetová informační služba Manager (inetmgr.exe) a v levém stromovém zobrazení vyberte název vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="e653e-110">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="e653e-111">Na pravé straně obrazovky výběr certifikátů serveru</span><span class="sxs-lookup"><span data-stu-id="e653e-111">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="e653e-112">![Domovská obrazovka Správce služby IIS](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="e653e-112">![IIS Manager Home Screen](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2. <span data-ttu-id="e653e-113">V okně certifikáty serveru klikněte na **vytvořit certifikát podepsaný svým držitelem....**</span><span class="sxs-lookup"><span data-stu-id="e653e-113">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="e653e-114">Propojit.</span><span class="sxs-lookup"><span data-stu-id="e653e-114">Link.</span></span>  
  
     <span data-ttu-id="e653e-115">![Vytvoření certifikátu podepsaného svým&#45;m pomocí služby IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="e653e-115">![Creating a self&#45;signed certificate with IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3. <span data-ttu-id="e653e-116">Zadejte popisný název certifikátu podepsaného svým držitelem a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="e653e-116">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="e653e-117">![Dialog vytvořit certifikát podepsaný svým&#45;](media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="e653e-117">![Create Self&#45;Signed Certificate Dialog](media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="e653e-118">Nově vytvořený certifikát podepsaný svým držitelem se teď zobrazí v okně **certifikáty serveru** .</span><span class="sxs-lookup"><span data-stu-id="e653e-118">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="e653e-119">![Okno certifikát serveru](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="e653e-119">![Server Certificate Window](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="e653e-120">Vygenerovaný certifikát je nainstalovaný v úložišti důvěryhodných kořenových certifikačních autorit.</span><span class="sxs-lookup"><span data-stu-id="e653e-120">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="e653e-121">Přidat vazbu SSL</span><span class="sxs-lookup"><span data-stu-id="e653e-121">Add SSL Binding</span></span>  
  
1. <span data-ttu-id="e653e-122">Pořád v Internetová informační služba Manageru rozbalte složku **lokality** a pak ve stromovém zobrazení na levé straně obrazovky vyberte **výchozí webovou** složku.</span><span class="sxs-lookup"><span data-stu-id="e653e-122">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2. <span data-ttu-id="e653e-123">Klikněte na **vazby....**</span><span class="sxs-lookup"><span data-stu-id="e653e-123">Click the **Bindings….**</span></span> <span data-ttu-id="e653e-124">Odkaz v části **Actions (akce** ) v pravé horní části okna.</span><span class="sxs-lookup"><span data-stu-id="e653e-124">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="e653e-125">![Přidání vazby SSL](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="e653e-125">![Adding an SSL binding](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3. <span data-ttu-id="e653e-126">V okně vazby webu klikněte na tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="e653e-126">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="e653e-127">![Dialogové okno vazby webu](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="e653e-127">![Site Bindings Dialog](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4. <span data-ttu-id="e653e-128">V dialogu **Přidat vazbu webu** vyberte HTTPS pro typ a popisný název certifikátu podepsaného svým držitelem, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="e653e-128">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="e653e-129">![Příklad vazby webu](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="e653e-129">![Site binding example](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="e653e-130">Konfigurace virtuálního adresáře pro SSL</span><span class="sxs-lookup"><span data-stu-id="e653e-130">Configure Virtual Directory for SSL</span></span>  
  
1. <span data-ttu-id="e653e-131">Pořád v Internetová informační služba Manageru vyberte virtuální adresář, který obsahuje vaši zabezpečenou službu WCF.</span><span class="sxs-lookup"><span data-stu-id="e653e-131">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2. <span data-ttu-id="e653e-132">V prostředním podokně okna vyberte **Nastavení SSL** v části IIS.</span><span class="sxs-lookup"><span data-stu-id="e653e-132">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="e653e-133">![Nastavení SSL pro virtuální adresář](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="e653e-133">![SSL Settings for virtual directory](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3. <span data-ttu-id="e653e-134">V podokně nastavení SSL zaškrtněte políčko **vyžadovat protokol SSL** a klikněte na odkaz **použít** v části **Akce** na pravé straně obrazovky.</span><span class="sxs-lookup"><span data-stu-id="e653e-134">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="e653e-135">![Nastavení SSL virtuálního adresáře](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="e653e-135">![Virtual directory SSL settings](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="e653e-136">Konfigurace služby WCF pro zabezpečení přenosu HTTP</span><span class="sxs-lookup"><span data-stu-id="e653e-136">Configure WCF Service for HTTP Transport Security</span></span>  
  
1. <span data-ttu-id="e653e-137">Ve web.config služby WCF Nakonfigurujte vazbu HTTP tak, aby používala zabezpečení přenosu, jak je znázorněno v následujícím kódu XML.</span><span class="sxs-lookup"><span data-stu-id="e653e-137">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
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
  
2. <span data-ttu-id="e653e-138">Zadejte službu a koncový bod služby, jak je znázorněno v následujícím kódu XML.</span><span class="sxs-lookup"><span data-stu-id="e653e-138">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="e653e-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="e653e-139">Example</span></span>  
 <span data-ttu-id="e653e-140">Následuje kompletní příklad souboru web.config pro službu WCF pomocí zabezpečení přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e653e-140">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e653e-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="e653e-141">See also</span></span>

- [<span data-ttu-id="e653e-142">Hostování v Internetové informační službě</span><span class="sxs-lookup"><span data-stu-id="e653e-142">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="e653e-143">Pokyny k hostování služby IIS</span><span class="sxs-lookup"><span data-stu-id="e653e-143">Internet Information Service Hosting Instructions</span></span>](../samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="e653e-144">Doporučené postupy hostování Internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="e653e-144">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="e653e-145">Hostování IIS pomocí vloženého kódu</span><span class="sxs-lookup"><span data-stu-id="e653e-145">IIS Hosting Using Inline Code</span></span>](../samples/iis-hosting-using-inline-code.md)
