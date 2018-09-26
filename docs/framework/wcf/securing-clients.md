---
title: Zabezpečení klientů
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
author: BrucePerlerMS
ms.openlocfilehash: 4ddf6f4ac5decd2637299c54a31a7a96eaab0648
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088175"
---
# <a name="securing-clients"></a>Zabezpečení klientů
Ve Windows Communication Foundation (WCF), služba určuje požadavky na zabezpečení pro klienty. To znamená služba určuje, jaké režim zabezpečení, a určuje, jestli klient musí poskytnout přihlašovací údaje. Zabezpečení klienta, proto se tento proces je prostý: pomocí metadat získaných ze služby (je-li publikován) a vytvořit klienta. Metadata Určuje, jak nakonfigurovat klienta. Pokud služba vyžaduje, aby, že klient zadat přihlašovací údaje, je nutné získat pověření, která odpovídá požadavku. Toto téma popisuje proces podrobněji. Další informace o vytváření zabezpečených služeb, naleznete v tématu [zabezpečení služby](../../../docs/framework/wcf/securing-services.md).  
  
## <a name="the-service-specifies-security"></a>Tato služba určuje zabezpečení  
 Vazby WCF mají ve výchozím nastavení povolena funkce zabezpečení. (Výjimkou je <xref:System.ServiceModel.BasicHttpBinding>.) Proto pokud byla služba vytvořena pomocí technologie WCF, je větší pravděpodobnost, že se implementovat zabezpečení zajistit ověřování, důvěrnost a integrita. V takovém případě metadat, které služba poskytuje, označí ji vyžaduje vytvořit zabezpečený komunikační kanál. Pokud metadata služby neobsahuje žádné požadavky na zabezpečení, neexistuje žádný způsob, jak ukládat schéma zabezpečení, jako je například vrstvy SSL (Secure Sockets) přes protokol HTTP, ve službě. Pokud však služba vyžaduje, aby klient k zadání přihlašovacích údajů, pak vývojáře klienta, nástroje pro nasazení nebo správce musíte zadat skutečné přihlašovací údaje, které klient použije ke svému ověření ke službě.  
  
## <a name="obtaining-metadata"></a>Získávání metadat  
 Při vytváření klienta, prvním krokem je získání metadat pro službu, která bude klient komunikovat s. To lze provést dvěma způsoby. Nejprve, pokud služba zveřejňuje koncový bod metadat exchange (MEX) nebo jeho metadata zpřístupní prostřednictvím protokolu HTTP nebo HTTPS, si můžete stáhnout pomocí metadat [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), který generuje obojí soubory s kódem pro klienta, stejně jako konfigurační soubor. (Další informace o používání nástroje najdete v tématu [přístup ke službám pomocí klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).) Pokud služba nebude publikován koncový bod MEX a také neprovede jeho metadata k dispozici prostřednictvím protokolu HTTP nebo HTTPS, musí kontaktujte autora služby pro dokumentaci, která popisuje požadavky na zabezpečení a metadata.  
  
> [!IMPORTANT]
>  Doporučuje se, že metadata pocházejí z důvěryhodného zdroje a že nesmí být manipulováno. Metadata načten pomocí protokolu HTTP se odesílá ve formátu prostého textu a mohou být změněny. Pokud služba používá <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnosti, použijte adresu URL služby Tvůrce zadaný pro stahování dat pomocí protokolu HTTPS.  
  
## <a name="validating-security"></a>Ověřování zabezpečení  
 Metadata zdrojů je možné rozdělit do dvou rozsáhlých kategorií: důvěřovat zdrojů a nedůvěryhodných zdrojů. Pokud nedůvěřujete zdroji a jste stáhli kód klienta a další metadata z tohoto zdroje zabezpečeného koncového bodu MEX, pak můžete sestavit klienta, poskytne správné přihlašovací údaje a spustit s žádné obavy.  
  
 Pokud se rozhodnete pro stažení klienta a metadata ze zdroje, trochu znáte, ale je potřeba ověřit bezpečnostní opatření, které kód používá. Například můžete nesmí jednoduše vytvořit klienta, který se odešle službě svoje osobní nebo finanční informace, pokud služba vyžaduje důvěrnost a integrita (minimálně). Vlastník služby by měla důvěřovat rozsahu, chcete-li zpřístupnit tyto informace, protože tyto informace budou viditelné můžete nového zaměstnance odkázat.  
  
 Jako pravidlo proto se při použití kódu a metadata z nedůvěryhodného zdroje, zkontrolujte kód a metadata zajistit, aby splňoval úroveň zabezpečení, která požadujete.  
  
## <a name="setting-a-client-credential"></a>Nastavení přihlašovacích údajů klienta  
 Nastavení přihlašovacích údajů klienta v klientském počítači se skládá ze dvou kroků:  
  
1.  Určit, *typu pověření klienta* služba vyžaduje, aby. To lze provést jedním ze dvou způsobů. Nejprve, pokud máte dokumentace z Tvůrce služby, měla by obsahovat pověření klienta vyžaduje služba typu (pokud existuje). Za druhé Pokud máte pouze se vygenerovat pomocí nástroje Svcutil.exe konfigurační soubor, můžete zkoumat jednotlivé vazeb k určení, jaký typ přihlašovacích údajů se vyžaduje.  
  
2.  Zadejte pověření skutečný klienta. Přihlašovací údaje, které skutečným klientem se volá *hodnoty přihlašovacích údajů klienta* ho odlišuje od typu. Například pokud typ přihlašovacích údajů klienta Určuje certifikát, je nutné zadat certifikát X.509, který je vydaný certifikační autoritou služby vztahy důvěryhodnosti.  
  
### <a name="determining-the-client-credential-type"></a>Určení typu pověření klienta  
 Pokud máte konfigurační soubor nástroje Svcutil.exe vygenerována, zkontrolujte [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) části a zjistěte, jaký typ pověření klienta je povinný. V rámci oddílu jsou elementy vazby, které určují požadavky na zabezpečení. Konkrétně zkontrolujte \<security > – Element pro každou vazbu. Tento prvek obsahuje `mode` atribut, který můžete nastavit na jedno ze tří možných hodnot (`Message`, `Transport`, nebo `TransportWithMessageCredential`). Hodnota atributu určuje režim a režim určuje, který z podřízených prvků je důležité.  
  
 `<security>` Element může obsahovat buď `<transport>` nebo `<message>` element, nebo obojí. Důležitý prvek je ten, který odpovídá režim zabezpečení. Například následující kód určuje, že je režim zabezpečení `"Message"`a pro typ přihlašovacích údajů klienta `<message>` element je `"Certificate"`. V takovém případě `<transport>` element můžete ignorovat. Ale `<message>` element určuje, že je nutné zadat certifikát X.509.  
  
```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"   
                      realm="" />  
           <message clientCredentialType="Certificate"   
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"   
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  
  
 Všimněte si, že pokud `clientCredentialType` atribut je nastaven na `"Windows"`, jak je znázorněno v následujícím příkladu, není potřeba zadat hodnotu skutečné přihlašovací údaje. Je to proto, že integrované zabezpečení Windows poskytuje skutečné přihlašovací údaje (token protokolu Kerberos) osoby, která běží klientem.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>Nastavení hodnoty přihlašovacích údajů klienta  
 Pokud je zjištěno, že klient musí poskytnout přihlašovací údaje, použijte vhodnou metodu pro konfiguraci klienta. Například pokud chcete nastavit certifikát klienta, použijte <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody.  
  
 Běžné formuláře pověření je certifikát X.509. Můžete zadat přihlašovací údaje, které dvěma způsoby:  
  
-   Tím, že je v klientském kódu (pomocí `SetCertificate` metoda).  
  
 Přidáním [ \<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) oddílu konfiguračního souboru pro klienta a použitím `clientCredentials` – element (viz dole).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Nastavení \<clientCredentials > hodnota v kódu  
 Nastavit [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) hodnotu v kódu, je nutné přejít <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> třídy. Vrátí vlastnosti <xref:System.ServiceModel.Description.ClientCredentials> objekt, který umožňuje přístup na různé typy přihlašovacích údajů, jak je znázorněno v následující tabulce.  
  
|Vlastnost clientcredential systému|Popis|Poznámky|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Vrátí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|Představuje certifikát X.509, který poskytl klient ke svému ověření ke službě.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Vrátí <xref:System.ServiceModel.Security.HttpDigestClientCredential>|Představuje pověření HTTP digest. Přihlašovací údaje jsou hodnoty hash uživatelské jméno a heslo.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Vrátí <xref:System.ServiceModel.Security.IssuedTokenClientCredential>|Představuje vlastní zabezpečení u tokenu vydaného službou služby tokenů zabezpečení, běžně se používají ve scénářích s federací.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Vrátí <xref:System.ServiceModel.Security.PeerCredential>|Představuje sdílené přihlašovací údaje pro účast v síti Peer v doméně Windows.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Vrátí <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|Představuje certifikát X.509, který poskytuje službu out-of-band vyjednávání.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Vrátí <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|Reprezentuje dvojici jména a hesla uživatele.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Vrátí <xref:System.ServiceModel.Security.WindowsClientCredential>|Představuje pověření klienta Windows (Kerberos přihlašovací údaje). Vlastnosti třídy jsou jen pro čtení.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Nastavení \<clientCredentials > hodnota v konfiguraci  
 Hodnot přihlašovacích údajů je určené vlastností chování koncového bodu jako podřízené prvky [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu. Element používá závisí na typu pověření klienta. Například následující příklad ukazuje na nastavit certifikát X.509 pomocí konfigurace <[\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"   
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>              
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Chcete-li nastavit pověření klienta v konfiguraci, přidejte [ \<endpointBehaviors >](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) prvku do konfiguračního souboru. Přidání chování element kromě toho je potřeba propojit koncového bodu služby pomocí `behaviorConfiguration` atribut [ \<koncový bod >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu, jak je znázorněno v následujícím příkladu. Hodnota `behaviorConfiguration` atributu musí odpovídat hodnotě chování `name` atribut.  
  
 `<configuration>`  
  
 `<system.serviceModel>`  
  
 `<client>`  
  
 `<endpoint address="http://localhost/servicemodelsamples/service.svc"`  
  
 `binding="wsHttpBinding"`  
  
 `bindingConfiguration="Binding1"`  
  
 `behaviorConfiguration="myEndpointBehavior"`  
  
 `contract="Microsoft.ServiceModel.Samples.ICalculator" />`  
  
 `</client>`  
  
 `</system.serviceModel>`  
  
 `</configuration>`  
  
> [!NOTE]
>  Některé z hodnot přihlašovacích údajů klienta nemůže být sada pomocí konfiguračních souborů aplikace, třeba, uživatelské jméno a heslo, nebo Windows uživatele a hodnoty hesla. Tyto přihlašovací údaje hodnot je možné zadat pouze v kódu.  
  
 Další informace o nastavení přihlašovacích údajů klienta najdete v tématu [postupy: určení hodnot přihlašovacích údajů klienta](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
> [!NOTE]
>  `ClientCredentialType` ignorováno, pokud `SecurityMode` je nastavena na `"TransportWithMessageCredential",` jak je znázorněno v následující ukázková konfigurace.  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"   
               establishSecurityContext="false"    
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [\<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
 [Editor konfigurace (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Zabezpečení služeb](../../../docs/framework/wcf/securing-services.md)  
 [Přístup ke službám pomocí klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [Postupy: Zadání hodnot přihlašovacích údajů klienta](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [Nástroj metadat modelu služby (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Postupy: Určení typu přihlašovacích údajů klienta](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
