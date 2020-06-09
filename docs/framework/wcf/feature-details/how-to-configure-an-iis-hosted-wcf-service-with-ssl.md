---
title: 'Postupy: Konfigurace služby WCF hostované v IIS se SSL'
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: fb3e87021c3dce1172250f33fd302916920af74d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597225"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="32b7e-102">Postupy: Konfigurace služby WCF hostované v IIS se SSL</span><span class="sxs-lookup"><span data-stu-id="32b7e-102">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="32b7e-103">Toto téma popisuje, jak nastavit službu WCF hostovanou službou IIS pro použití zabezpečení přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="32b7e-103">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="32b7e-104">Zabezpečení přenosu HTTP vyžaduje, aby byl certifikát SSL zaregistrován ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="32b7e-104">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="32b7e-105">Pokud nemáte certifikát SSL, můžete k vygenerování testovacího certifikátu použít službu IIS.</span><span class="sxs-lookup"><span data-stu-id="32b7e-105">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="32b7e-106">Dále musíte přidat vazbu SSL na web a nakonfigurovat vlastnosti ověřování webu.</span><span class="sxs-lookup"><span data-stu-id="32b7e-106">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="32b7e-107">Nakonec musíte nakonfigurovat službu WCF tak, aby používala protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="32b7e-107">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="32b7e-108">Vytvoření certifikátu podepsaného svým držitelem</span><span class="sxs-lookup"><span data-stu-id="32b7e-108">Creating a Self-Signed Certificate</span></span>  
  
1. <span data-ttu-id="32b7e-109">Otevřete Správce Internetová informační služba (inetmgr. exe) a v levém stromovém zobrazení vyberte název počítače.</span><span class="sxs-lookup"><span data-stu-id="32b7e-109">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="32b7e-110">Na pravé straně obrazovky výběr certifikátů serveru</span><span class="sxs-lookup"><span data-stu-id="32b7e-110">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="32b7e-111">![Domovská obrazovka Správce služby IIS](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="32b7e-111">![IIS Manager Home Screen](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2. <span data-ttu-id="32b7e-112">V okně certifikáty serveru klikněte na **vytvořit certifikát podepsaný svým držitelem....**</span><span class="sxs-lookup"><span data-stu-id="32b7e-112">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="32b7e-113">Propojit.</span><span class="sxs-lookup"><span data-stu-id="32b7e-113">Link.</span></span>  
  
     <span data-ttu-id="32b7e-114">![Vytvoření certifikátu podepsaného svým&#45;m pomocí služby IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="32b7e-114">![Creating a self&#45;signed certificate with IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3. <span data-ttu-id="32b7e-115">Zadejte popisný název certifikátu podepsaného svým držitelem a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="32b7e-115">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="32b7e-116">![Dialog vytvořit certifikát podepsaný svým&#45;](media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="32b7e-116">![Create Self&#45;Signed Certificate Dialog](media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="32b7e-117">Nově vytvořený certifikát podepsaný svým držitelem se teď zobrazí v okně **certifikáty serveru** .</span><span class="sxs-lookup"><span data-stu-id="32b7e-117">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="32b7e-118">![Okno certifikát serveru](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="32b7e-118">![Server Certificate Window](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="32b7e-119">Vygenerovaný certifikát je nainstalovaný v úložišti důvěryhodných kořenových certifikačních autorit.</span><span class="sxs-lookup"><span data-stu-id="32b7e-119">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="32b7e-120">Přidat vazbu SSL</span><span class="sxs-lookup"><span data-stu-id="32b7e-120">Add SSL Binding</span></span>  
  
1. <span data-ttu-id="32b7e-121">Pořád v Internetová informační služba Manageru rozbalte složku **lokality** a pak ve stromovém zobrazení na levé straně obrazovky vyberte **výchozí webovou** složku.</span><span class="sxs-lookup"><span data-stu-id="32b7e-121">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2. <span data-ttu-id="32b7e-122">Klikněte na **vazby....**</span><span class="sxs-lookup"><span data-stu-id="32b7e-122">Click the **Bindings….**</span></span> <span data-ttu-id="32b7e-123">Odkaz v části **Actions (akce** ) v pravé horní části okna.</span><span class="sxs-lookup"><span data-stu-id="32b7e-123">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="32b7e-124">![Přidání vazby SSL](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="32b7e-124">![Adding an SSL binding](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3. <span data-ttu-id="32b7e-125">V okně vazby webu klikněte na tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="32b7e-125">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="32b7e-126">![Dialogové okno vazby webu](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="32b7e-126">![Site Bindings Dialog](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4. <span data-ttu-id="32b7e-127">V dialogu **Přidat vazbu webu** vyberte HTTPS pro typ a popisný název certifikátu podepsaného svým držitelem, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="32b7e-127">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="32b7e-128">![Příklad vazby webu](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="32b7e-128">![Site binding example](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="32b7e-129">Konfigurace virtuálního adresáře pro SSL</span><span class="sxs-lookup"><span data-stu-id="32b7e-129">Configure Virtual Directory for SSL</span></span>  
  
1. <span data-ttu-id="32b7e-130">Pořád v Internetová informační služba Manageru vyberte virtuální adresář, který obsahuje vaši zabezpečenou službu WCF.</span><span class="sxs-lookup"><span data-stu-id="32b7e-130">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2. <span data-ttu-id="32b7e-131">V prostředním podokně okna vyberte **Nastavení SSL** v části IIS.</span><span class="sxs-lookup"><span data-stu-id="32b7e-131">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="32b7e-132">![Nastavení SSL pro virtuální adresář](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="32b7e-132">![SSL Settings for virtual directory](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3. <span data-ttu-id="32b7e-133">V podokně nastavení SSL zaškrtněte políčko **vyžadovat protokol SSL** a klikněte na odkaz **použít** v části **Akce** na pravé straně obrazovky.</span><span class="sxs-lookup"><span data-stu-id="32b7e-133">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="32b7e-134">![Nastavení SSL virtuálního adresáře](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="32b7e-134">![Virtual directory SSL settings](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="32b7e-135">Konfigurace služby WCF pro zabezpečení přenosu HTTP</span><span class="sxs-lookup"><span data-stu-id="32b7e-135">Configure WCF Service for HTTP Transport Security</span></span>  
  
1. <span data-ttu-id="32b7e-136">V souboru Web. config služby WCF Nakonfigurujte vazbu HTTP na použití zabezpečení přenosu, jak je znázorněno v následujícím kódu XML.</span><span class="sxs-lookup"><span data-stu-id="32b7e-136">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
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
  
2. <span data-ttu-id="32b7e-137">Zadejte službu a koncový bod služby, jak je znázorněno v následujícím kódu XML.</span><span class="sxs-lookup"><span data-stu-id="32b7e-137">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="32b7e-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="32b7e-138">Example</span></span>  
 <span data-ttu-id="32b7e-139">Následuje kompletní příklad souboru Web. config pro službu WCF pomocí zabezpečení přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="32b7e-139">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32b7e-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="32b7e-140">See also</span></span>

- [<span data-ttu-id="32b7e-141">Hostování v Internetové informační službě</span><span class="sxs-lookup"><span data-stu-id="32b7e-141">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="32b7e-142">Pokyny k hostování služby IIS</span><span class="sxs-lookup"><span data-stu-id="32b7e-142">Internet Information Service Hosting Instructions</span></span>](../samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="32b7e-143">Doporučené postupy hostování Internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="32b7e-143">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="32b7e-144">Hostování IIS pomocí vloženého kódu</span><span class="sxs-lookup"><span data-stu-id="32b7e-144">IIS Hosting Using Inline Code</span></span>](../samples/iis-hosting-using-inline-code.md)
