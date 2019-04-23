---
title: 'Postupy: Konfigurace služby WCF hostované v IIS se SSL'
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 8d3bbb1ceab8a3bc7e5e209fda29fd574110b4f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326447"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>Postupy: Konfigurace služby WCF hostované v IIS se SSL
Toto téma popisuje postup nastavení služby WCF hostované IIS pro použití zabezpečení přenosu HTTP. Zabezpečení přenosu HTTP vyžaduje certifikát SSL pro službu IIS zaregistrovat. Pokud není certifikát SSL služby IIS můžete vygenerovat zkušební certifikát. Dále musíte přidat vazbu SSL na webovou stránku a nakonfigurovat vlastnosti ověřování na webu. Nakonec musíte nakonfigurovat službu WCF pro použití protokolu HTTPS.  
  
### <a name="creating-a-self-signed-certificate"></a>Vytváří se certifikát podepsaný svým držitelem  
  
1. Otevřete Správce Internetové informační služby (inetmgr.exe) a vyberte název počítače v zobrazení stromu vlevo. Na pravé straně obrazovky vyberte certifikáty serveru  
  
     ![Správce služby IIS domovské obrazovce](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2. V okně certifikáty serveru klikněte na tlačítko **vytvořit certifikát podepsaný svým držitelem...** odkaz.  
  
     ![Vytváří se svým&#45;podepsaný certifikát s IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3. Zadejte popisný název certifikátu podepsaného svým držitelem a klikněte na tlačítko **OK**.  
  
     ![Create Self&#45;Signed Certificate Dialog](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")  
  
     Podrobnosti nově vytvořeného certifikátu podepsaného svým držitelem se teď zobrazují v **certifikáty serveru** okna.  
  
     ![Okno certifikátu serveru](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     Vygenerovaný certifikát nainstalován v důvěryhodné kořenové certifikační autority úložiště.  
  
### <a name="add-ssl-binding"></a>Add SSL Binding  
  
1. Stále v Správce Internetové informační služby, rozbalte **lokality** složku a potom **výchozí webový server** složky ve stromovém zobrazení na levé straně obrazovky.  
  
2. Klikněte na tlačítko **vazby...** Propojit **akce** části v pravé horní části okna.  
  
     ![Přidání vazby SSL](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3. V okně vazby webu klikněte na tlačítko **přidat** tlačítko.  
  
     ![Dialogové okno vazby webu](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4. V **přidat vazbu webu** dialogového okna, vyberte https pro typ a popisný název certifikátu podepsaného svým držitelem, jste právě vytvořili.  
  
     ![Příklad vazby webu](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>Nakonfigurujte virtuální adresář pro protokol SSL  
  
1. Stále v Správce Internetové informační služby vyberte virtuální adresář, který obsahuje vaše zabezpečenou službu WCF.  
  
2. V prostředním podokně okna, vyberte **nastavení SSL** v části služby IIS.  
  
     ![Nastavení SSL pro virtuální adresář](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3. V podokně nastavení protokolu SSL, vyberte **požadovat protokol SSL** zaškrtávací políčko a klikněte na tlačítko **použít** odkaz v **akce** části na pravé straně obrazovky.  
  
     ![Nastavení SSL virtuální adresář](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>Konfigurace služby WCF pro zabezpečení přenosu HTTP  
  
1. Ve WCF služby web.config nakonfigurovat vazbu HTTP pro použití zabezpečení přenosu, jak je znázorněno v následujícím souboru XML.  
  
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
  
2. Zadejte vaše služby a koncového bodu služby, jak je znázorněno v následujícím souboru XML.  
  
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
 Následuje Úplný příklad souboru web.config pro služby WCF pomocí zabezpečení přenosu HTTP  
  
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
  
## <a name="see-also"></a>Viz také:

- [Hostování v Internetové informační službě](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [Pokyny k hostování Internetové informační služby](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
- [Osvědčené postupy hostování Internetové informační služby](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [Hostování IIS pomocí vloženého kódu](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
