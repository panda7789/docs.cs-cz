---
title: Zabezpečení klientů
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: bfb980e629ffb8f8543937a1850430c9bf6e9199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183136"
---
# <a name="securing-clients"></a>Zabezpečení klientů
V systému Windows Communication Foundation (WCF) služba určuje požadavky na zabezpečení klientů. To znamená, že služba určuje, jaký režim zabezpečení použít a zda klient musí poskytnout pověření. Proces zabezpečení klienta je proto jednoduchý: použijte metadata získaná ze služby (pokud je publikována) a vytvořte klienta. Metadata určují způsob konfigurace klienta. Pokud služba vyžaduje, aby klient zadat pověření, potom je nutné získat pověření, které odpovídá požadavku. Toto téma podrobněji popisuje proces. Další informace o vytvoření zabezpečené služby naleznete v tématu [Zabezpečení služeb](securing-services.md).  
  
## <a name="the-service-specifies-security"></a>Služba určuje zabezpečení.  
 Ve výchozím nastavení mají vazby WCF povolené funkce zabezpečení. (Výjimkou je <xref:System.ServiceModel.BasicHttpBinding>.) Proto pokud služba byla vytvořena pomocí WCF, je větší pravděpodobnost, že bude implementovat zabezpečení k zajištění ověřování, důvěrnost i integritu. V takovém případě metadata poskytuje bude uvádět, co vyžaduje k vytvoření zabezpečeného komunikačního kanálu. Pokud metadata služby neobsahuje žádné požadavky na zabezpečení, neexistuje žádný způsob, jak uložit schéma zabezpečení, jako je například ssl (Secure Sockets Layer) přes HTTP, na službu. Pokud však služba vyžaduje, aby klient zadával pověření, musí vývojář klienta, nasazovač nebo správce zadat skutečné pověření, které klient použije k ověření služby.  
  
## <a name="obtaining-metadata"></a>Získání metadat  
 Při vytváření klienta je prvním krokem získání metadat pro službu, se kterou bude klient komunikovat. To lze provést dvěma způsoby. Za prvé, pokud služba publikuje koncový bod výměny metadat (MEX) nebo zpřístupní jeho metadata prostřednictvím protokolu HTTP nebo HTTPS, můžete stáhnout metadata pomocí [nástroje ServiceModel Metadata Utility Tool (Svcutil.exe),](servicemodel-metadata-utility-tool-svcutil-exe.md)který generuje soubory kódu pro klienta i konfigurační soubor. (Další informace o použití nástroje naleznete [v tématu Přístup ke službám pomocí klienta WCF](accessing-services-using-a-wcf-client.md).) Pokud služba nepublikuje koncový bod MEX a také nezpřístupňuje jeho metadata prostřednictvím protokolu HTTP nebo HTTPS, musíte kontaktovat tvůrce služby pro dokumentaci, která popisuje požadavky na zabezpečení a metadata.  
  
> [!IMPORTANT]
> Doporučuje se, aby metadata pocházejí z důvěryhodného zdroje a aby s nimi nebylo manipulováno. Metadata načtená pomocí protokolu HTTP jsou odesílána ve prostém textu a lze s nimi manipulovat. Pokud služba používá <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnosti a, použijte adresu URL, kterou tvůrce služby dodal, ke stažení dat pomocí protokolu HTTPS.  
  
## <a name="validating-security"></a>Ověření zabezpečení  
 Zdroje metadat lze rozdělit do dvou širokých kategorií: zdroje důvěryhodnosti a nedůvěryhodné zdroje. Pokud důvěřujete zdroji a stáhli jste kód klienta a další metadata z zabezpečeného koncového bodu MEX tohoto zdroje, můžete klienta sestavit, zadat mu správná pověření a spustit bez dalších obav.  
  
 Pokud se však rozhodnete stáhnout klienta a metadata ze zdroje, o kterém víte málo, nezapomeňte ověřit bezpečnostní opatření, která kód používá. Nesmíte například jednoduše vytvořit klienta, který odešle vaše osobní nebo finanční informace službě, pokud služba nevyžaduje důvěrnost a integritu (přinejmenším). Měli byste důvěřovat vlastníkovi služby v rozsahu, v jakém jste ochotni tyto informace zveřejnit, protože tyto informace budou viditelné pro ně.  
  
 Je pravidlem, že při použití kódu a metadat z nedůvěryhodného zdroje, zkontrolujte kód a metadata, aby bylo zajištěno, že splňuje úroveň zabezpečení, kterou požadujete.  
  
## <a name="setting-a-client-credential"></a>Nastavení pověření klienta  
 Nastavení pověření klienta v klientovi se skládá ze dvou kroků:  
  
1. Určete *typ pověření klienta,* který služba vyžaduje. Toho je dosaženo jednou ze dvou metod. Za prvé, pokud máte dokumentaci od tvůrce služby, měl by určit typ pověření klienta (pokud existuje) služba vyžaduje. Za druhé, pokud máte pouze konfigurační soubor generovaný nástrojem Svcutil.exe, můžete prozkoumat jednotlivé vazby k určení, jaký typ pověření je požadováno.  
  
2. Zadejte skutečné pověření klienta. Skutečné pověření klienta se nazývá *hodnota pověření klienta* odlišit od typu. Pokud například typ pověření klienta určuje certifikát, musíte zadat certifikát X.509 vydaný certifikačním úřadem, kterému služba důvěřuje.  
  
### <a name="determining-the-client-credential-type"></a>Určení typu pověření klienta  
 Pokud máte konfigurační soubor, který je generován nástrojem Svcutil.exe, zkontrolujte [ \<oddíl vazby>](../configure-apps/file-schema/wcf/bindings.md) a zjistěte, jaký typ pověření klienta je vyžadován. V rámci oddílu jsou elementy vazby, které určují požadavky na zabezpečení. Konkrétně zkontrolujte \<> zabezpečení Element každé vazby. Tento prvek `mode` obsahuje atribut, který můžete nastavit na`Message`jednu ze tří možných hodnot ( , `Transport`, nebo `TransportWithMessageCredential`). Hodnota atributu určuje režim a režim určuje, který z podřízených prvků je významný.  
  
 Prvek `<security>` může obsahovat `<transport>` `<message>` buď nebo element nebo obojí. Významným prvkem je ten, který odpovídá režimu zabezpečení. Například následující kód určuje, že režim `"Message"`zabezpečení je a typ `<message>` pověření `"Certificate"`klienta pro prvek je . V tomto případě `<transport>` může být prvek ignorován. `<message>` Prvek však určuje, že musí být zadán certifikát X.509.  

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

 Všimněte si, že pokud je `clientCredentialType` atribut nastaven na `"Windows"`, jak je znázorněno v následujícím příkladu, není nutné zadat skutečnou hodnotu pověření. Důvodem je, že integrované zabezpečení systému Windows poskytuje skutečné pověření (token protokolu Kerberos) osoby, která klienta spouštějí.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>Nastavení hodnoty pověření klienta  
 Pokud je zjištěno, že klient musí zadat pověření, použijte příslušnou metodu ke konfiguraci klienta. Chcete-li například nastavit klientský <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> certifikát, použijte metodu.  
  
 Běžnou formou pověření je certifikát X.509. Pověření můžete zadat dvěma způsoby:  
  
- Naprogramováním ve vašem klientském `SetCertificate` kódu (pomocí metody).  
  
 Přidáním [ \<chování>](../configure-apps/file-schema/wcf/behaviors.md) části konfiguračního souboru `clientCredentials` pro klienta a pomocí prvku (viz níže).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Nastavení \<hodnoty> klienta Pověření v kódu  
 Chcete-li nastavit [ \<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) hodnotu <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> v kódu, musíte získat přístup k vlastnosti třídy. <xref:System.ServiceModel.ClientBase%601> Vlastnost vrátí <xref:System.ServiceModel.Description.ClientCredentials> objekt, který umožňuje přístup k různým typům pověření, jak je znázorněno v následující tabulce.  
  
|Vlastnost ClientCredential|Popis|Poznámky|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Vrátí hodnotu<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|Představuje certifikát X.509 poskytnutý klientem k ověření sám služby.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Vrátí hodnotu<xref:System.ServiceModel.Security.HttpDigestClientCredential>|Představuje pověření http digest. Pověření je hash uživatelského jména a hesla.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Vrátí hodnotu<xref:System.ServiceModel.Security.IssuedTokenClientCredential>|Představuje vlastní token zabezpečení vydaný službou tokenů zabezpečení, běžně používaný ve scénářích federace.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Vrátí hodnotu<xref:System.ServiceModel.Security.PeerCredential>|Představuje pověření partnera pro účast v síti peer v doméně systému Windows.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Vrátí hodnotu<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|Představuje certifikát X.509 poskytovaný službou v neintegrovaném vyjednávání.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Vrátí hodnotu<xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|Představuje dvojici uživatelského jména a hesla.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Vrátí hodnotu<xref:System.ServiceModel.Security.WindowsClientCredential>|Představuje pověření klienta systému Windows (pověření protokolu Kerberos). Vlastnosti třídy jsou jen pro čtení.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Nastavení \<hodnoty> klienta v konfiguraci  
 Hodnoty pověření jsou určeny pomocí chování koncového bodu jako podřízené prvky [ \<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element. Použitý prvek závisí na typu pověření klienta. Například následující příklad ukazuje konfiguraci pro nastavení certifikátu X.509 pomocí <[ \<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
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
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
 Chcete-li nastavit pověření klienta v konfiguraci, přidejte do konfiguračního souboru [ \<prvek endpointBehaviors>.](../configure-apps/file-schema/wcf/endpointbehaviors.md) Kromě toho musí být prvek přidané chování propojen s koncovým bodem služby pomocí `behaviorConfiguration` atributu [ \<koncového bodu> prvku>klienta, \<](../configure-apps/file-schema/wcf/endpoint-of-client.md) jak je znázorněno v následujícím příkladu. Hodnota atributu `behaviorConfiguration` musí odpovídat hodnotě `name` atributu behavior.  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
> Některé hodnoty pověření klienta nelze nastavit pomocí konfiguračních souborů aplikace, například uživatelského jména a hesla nebo hodnot uživatele a hesla systému Windows. Tyto hodnoty pověření lze zadat pouze v kódu.  
  
 Další informace o nastavení pověření klienta naleznete v [tématu How to: Specify Client Credential Values](how-to-specify-client-credential-values.md).  
  
> [!NOTE]
> `ClientCredentialType`je ignorována, `SecurityMode` pokud `"TransportWithMessageCredential",` je nastavena tak, jak je znázorněno v následující konfiguraci ukázky.  
  
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

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<vázání>](../configure-apps/file-schema/wcf/bindings.md)
- [Editor konfigurace (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)
- [Zabezpečení služeb](securing-services.md)
- [Přístup ke službám pomocí klienta WCF](accessing-services-using-a-wcf-client.md)
- [Postupy: Zadání hodnot přihlašovacích údajů klienta](how-to-specify-client-credential-values.md)
- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Postupy: Určení typu přihlašovacích údajů klienta](how-to-specify-the-client-credential-type.md)
