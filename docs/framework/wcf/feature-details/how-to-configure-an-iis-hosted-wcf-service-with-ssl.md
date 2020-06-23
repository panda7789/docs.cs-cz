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
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>Postupy: Konfigurace služby WCF hostované v IIS se SSL
Toto téma popisuje, jak nastavit službu WCF hostovanou službou IIS pro použití zabezpečení přenosu HTTP. Zabezpečení přenosu HTTP vyžaduje, aby byl certifikát SSL zaregistrován ve službě IIS. Pokud nemáte certifikát SSL, můžete k vygenerování testovacího certifikátu použít službu IIS. Dále musíte přidat vazbu SSL na web a nakonfigurovat vlastnosti ověřování webu. Nakonec musíte nakonfigurovat službu WCF tak, aby používala protokol HTTPS.  
  
### <a name="creating-a-self-signed-certificate"></a>Vytvoření certifikátu podepsaného svým držitelem  
  
1. Otevřete Internetová informační služba Manager (inetmgr.exe) a v levém stromovém zobrazení vyberte název vašeho počítače. Na pravé straně obrazovky výběr certifikátů serveru  
  
     ![Domovská obrazovka Správce služby IIS](media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2. V okně certifikáty serveru klikněte na **vytvořit certifikát podepsaný svým držitelem....** Propojit.  
  
     ![Vytvoření certifikátu podepsaného svým&#45;m pomocí služby IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3. Zadejte popisný název certifikátu podepsaného svým držitelem a klikněte na **OK**.  
  
     ![Dialog vytvořit certifikát podepsaný svým&#45;](media/mg-mycert.jpg "mg_MyCert")  
  
     Nově vytvořený certifikát podepsaný svým držitelem se teď zobrazí v okně **certifikáty serveru** .  
  
     ![Okno certifikát serveru](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     Vygenerovaný certifikát je nainstalovaný v úložišti důvěryhodných kořenových certifikačních autorit.  
  
### <a name="add-ssl-binding"></a>Přidat vazbu SSL  
  
1. Pořád v Internetová informační služba Manageru rozbalte složku **lokality** a pak ve stromovém zobrazení na levé straně obrazovky vyberte **výchozí webovou** složku.  
  
2. Klikněte na **vazby....** Odkaz v části **Actions (akce** ) v pravé horní části okna.  
  
     ![Přidání vazby SSL](media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3. V okně vazby webu klikněte na tlačítko **Přidat** .  
  
     ![Dialogové okno vazby webu](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4. V dialogu **Přidat vazbu webu** vyberte HTTPS pro typ a popisný název certifikátu podepsaného svým držitelem, který jste právě vytvořili.  
  
     ![Příklad vazby webu](media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>Konfigurace virtuálního adresáře pro SSL  
  
1. Pořád v Internetová informační služba Manageru vyberte virtuální adresář, který obsahuje vaši zabezpečenou službu WCF.  
  
2. V prostředním podokně okna vyberte **Nastavení SSL** v části IIS.  
  
     ![Nastavení SSL pro virtuální adresář](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3. V podokně nastavení SSL zaškrtněte políčko **vyžadovat protokol SSL** a klikněte na odkaz **použít** v části **Akce** na pravé straně obrazovky.  
  
     ![Nastavení SSL virtuálního adresáře](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>Konfigurace služby WCF pro zabezpečení přenosu HTTP  
  
1. Ve web.config služby WCF Nakonfigurujte vazbu HTTP tak, aby používala zabezpečení přenosu, jak je znázorněno v následujícím kódu XML.  
  
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
  
2. Zadejte službu a koncový bod služby, jak je znázorněno v následujícím kódu XML.  
  
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
  
## <a name="example"></a>Příklad  
 Následuje kompletní příklad souboru web.config pro službu WCF pomocí zabezpečení přenosu HTTP.  
  
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
  
## <a name="see-also"></a>Viz také

- [Hostování v Internetové informační službě](hosting-in-internet-information-services.md)
- [Pokyny k hostování služby IIS](../samples/internet-information-service-hosting-instructions.md)
- [Doporučené postupy hostování Internetové informační služby](internet-information-services-hosting-best-practices.md)
- [Hostování IIS pomocí vloženého kódu](../samples/iis-hosting-using-inline-code.md)
