---
title: 'Postupy: Konfigurace služby WCF hostované IIS pomocí protokolu SSL'
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: e739eb47611e5b73e7f1d62191a5aa61ad77abe2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493487"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>Postupy: Konfigurace služby WCF hostované IIS pomocí protokolu SSL
Toto téma popisuje postup nastavení služby WCF hostované IIS pro použití zabezpečení přenosu HTTP. Zabezpečení přenosu HTTP vyžaduje certifikát SSL zaregistrovat u služby IIS. Pokud není certifikát SSL, že které lze použít k vygenerování testu certifikátu služby IIS. Dále musíte přidání vazby SSL na web a nakonfigurovat vlastnosti ověřování na webu. Nakonec budete muset konfigurovat službu WCF pro použití protokolu HTTPS.  
  
### <a name="creating-a-self-signed-certificate"></a>Vytvořit certifikát podepsaný svým držitelem  
  
1.  Otevřete Správce Internetové informační služby (inetmgr.exe) a vyberte v levé stromovém zobrazení názvu vašeho počítače. Na pravé straně obrazovky vyberte certifikáty serveru  
  
     ![Správce služby IIS domovské obrazovce](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2.  V okně certifikáty serveru klikněte na **vytvořit certifikát podepsaný svým držitelem...** Odkaz.  
  
     ![Vytváření svým&#45;podepsaný certifikát se službou IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3.  Zadejte popisný název certifikátu podepsaného svým držitelem a klikněte na **OK**.  
  
     ![Vytvoření vlastního&#45;podepsané dialogového okna certifikátu](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")  
  
     Podrobnosti o nově vytvořený certifikát podepsaný svým držitelem se teď zobrazují v **certifikáty serveru** okno.  
  
     ![Okno certifikát serveru](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     Vygenerovaný certifikát nainstalován v důvěryhodné kořenové certifikační autority uložit.  
  
### <a name="add-ssl-binding"></a>Přidat vazbu SSL  
  
1.  Stále v Správce Internetové informační služby, rozbalte **lokality** složku a potom **Default Web Site** složky ve stromovém zobrazení na levé straně obrazovky.  
  
2.  Klikněte **vazby...** Odkaz **akce** část v pravé horní části okna.  
  
     ![Přidání vazby SSL](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3.  V okně vazby serveru klikněte na **přidat** tlačítko.  
  
     ![Dialogové okno vazby webu](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4.  V **přidat vazbu webu** dialogovém okně, vyberte https pro typ a popisný název certifikátu podepsaného svým držitelem jste právě vytvořili.  
  
     ![Příklad vazby webu](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>Nakonfigurujte virtuální adresář pro protokol SSL  
  
1.  Stále v Správce Internetové informační služby vyberte virtuálního adresáře, který obsahuje zabezpečené služby WCF.  
  
2.  V prostředním podokně okna vyberte **nastavení SSL** v části služby IIS.  
  
     ![Nastavení SSL pro virtuální adresář](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3.  V podokně nastavení protokolu SSL, vyberte **požadovat protokol SSL** zaškrtávací políčko a klikněte na tlačítko **použít** na odkaz v **akce** části na pravé straně obrazovky.  
  
     ![Nastavení SSL virtuální adresář](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>Konfigurace služby WCF pro zabezpečení přenosu HTTP  
  
1.  Ve WCF web.config služby konfiguraci vazby HTTP pro použití zabezpečení přenosu, jak je znázorněno v následující soubor XML.  
  
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
  
2.  Zadejte službu a koncový bod služby, jak je znázorněno v následující soubor XML.  
  
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
 Úplný příklad souboru web.config pro službu WCF pomocí zabezpečení přenosu HTTP  
  
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
 [Hostování v Internetové informační službě](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Pokyny k hostování Internetové informační služby](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [Osvědčené postupy hostování Internetové informační služby](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Hostování IIS pomocí vloženého kódu](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
