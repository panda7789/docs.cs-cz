---
title: Zabezpečení klientů
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: 988e868b1a1698d00a6d77fd715b2a76b1790132
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321269"
---
# <a name="securing-clients"></a>Zabezpečení klientů
V Windows Communication Foundation (WCF) služba Určuje požadavky na zabezpečení pro klienty. To znamená, že služba Určuje, který režim zabezpečení má být použit, a zda klient musí zadat pověření. Proces zabezpečení klienta je proto jednoduchý: použijte metadata získaná ze služby (je-li publikována) a vytvořte klienta. Metadata určují, jak nakonfigurovat klienta. Pokud služba vyžaduje, aby klient zadal přihlašovací údaje, musíte získat přihlašovací údaje, které vyhovují danému požadavku. Toto téma pojednává o procesu podrobněji. Další informace o vytváření zabezpečené služby najdete v tématu [zabezpečení služeb](securing-services.md).  
  
## <a name="the-service-specifies-security"></a>Služba určuje zabezpečení  
 Ve výchozím nastavení mají vazby WCF povolené funkce zabezpečení. (Výjimka je <xref:System.ServiceModel.BasicHttpBinding>.) Proto pokud byla služba vytvořena pomocí WCF, existuje větší pravděpodobnost, že bude implementovat zabezpečení, aby bylo zajištěno ověřování, důvěrnost a integritu. V takovém případě metadata, která služba poskytuje, indikuje, co vyžaduje k navázání zabezpečeného komunikačního kanálu. Pokud metadata služby neobsahují žádné požadavky na zabezpečení, neexistuje žádný způsob, jak do služby ukládat schéma zabezpečení, jako je například SSL (Secure Sockets Layer) (SSL) přes protokol HTTP. Pokud však služba vyžaduje, aby klient zadal přihlašovací údaje, pak musí klientský vývojář, nástroj pro nasazení nebo správce zadat skutečné přihlašovací údaje, které bude klient používat k ověření ve službě.  
  
## <a name="obtaining-metadata"></a>Získání metadat  
 Při vytváření klienta je prvním krokem získání metadat pro službu, se kterou bude klient komunikovat. To lze provést dvěma způsoby. Za prvé, pokud služba publikuje koncový bod výměny metadat (MEX) nebo zpřístupňuje jeho metadata prostřednictvím protokolu HTTP nebo HTTPS, můžete si stáhnout metadata pomocí nástroje pro dodávání [metadat (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), který generuje oba soubory kódu pro klienta. i konfigurační soubor. (Další informace o použití tohoto nástroje najdete v tématu [přístup ke službám pomocí klienta WCF](accessing-services-using-a-wcf-client.md).) Pokud služba nepublikuje koncový bod MEX a zároveň nezpřístupňuje jeho metadata prostřednictvím protokolu HTTP nebo HTTPS, je nutné se obrátit na tvůrce služby, který popisuje požadavky na zabezpečení a metadata.  
  
> [!IMPORTANT]
> Doporučuje se, aby metadata pocházejí z důvěryhodného zdroje a nebyla zfalšována. Metadata získaná pomocí protokolu HTTP se odesílají ve formátu prostého textu a můžou být poškozená. Pokud služba používá vlastnosti <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>, použijte adresu URL, kterou zadal tvůrce služby ke stažení dat pomocí protokolu HTTPS.  
  
## <a name="validating-security"></a>Ověřování zabezpečení  
 Zdroje metadat lze rozdělit do dvou hlavních kategorií: důvěryhodných zdrojů a nedůvěryhodných zdrojů. Pokud zdroji důvěřujete a stáhli jste kód klienta a další metadata z zabezpečeného koncového bodu MEX tohoto zdroje, můžete vytvořit klienta, zadat ho se správnými přihlašovacími údaji a spustit ho bez dalších otázek.  
  
 Pokud se ale rozhodnete stáhnout klienta a metadata ze zdroje, u kterého víte trochu o, ujistěte se, že jste ověřili míry zabezpečení, které kód používá. Například nesmíte jednoduše vytvořit klienta, který do služby odesílá osobní nebo finanční informace, pokud služba nepožaduje důvěrnost a integritu (nejméně). Měli byste důvěřovat vlastníkovi služby v rozsahu, který jste ochotni zveřejnit tyto informace, protože k nim budou mít tyto informace viditelné.  
  
 Pokud tedy pravidlo použijete pro kód a metadata z nedůvěryhodného zdroje, zkontrolujte kód a metadata a ujistěte se, že splňuje požadovanou úroveň zabezpečení.  
  
## <a name="setting-a-client-credential"></a>Nastavení přihlašovacích údajů klienta  
 Nastavení přihlašovacích údajů klienta v klientském počítači se skládá ze dvou kroků:  
  
1. Určete *typ pověření klienta* , které služba vyžaduje. Toho je možné dosáhnout jednou ze dvou metod. V případě, že máte dokumentaci od autora služby, je třeba zadat typ přihlašovacích údajů klienta (pokud existuje), který služba vyžaduje. Za druhé, pokud máte pouze konfigurační soubor generovaný nástrojem Svcutil. exe, můžete prozkoumávat jednotlivé vazby a určit, jaký typ přihlašovacích údajů je požadován.  
  
2. Zadejte skutečné přihlašovací údaje klienta. Vlastní přihlašovací údaje klienta se nazývají *hodnoty přihlašovacích údajů klienta* , aby je bylo možné odlišit od typu. Pokud například typ přihlašovacích údajů klienta Určuje certifikát, musíte zadat certifikát X. 509, který je vydaný certifikační autoritou, vztah důvěryhodnosti služby.  
  
### <a name="determining-the-client-credential-type"></a>Určení typu pověření klienta  
 Pokud máte konfigurační soubor vygenerovaný nástrojem Svcutil. exe, Projděte si část [> \<bindings](../configure-apps/file-schema/wcf/bindings.md) a určete, co je třeba zadat typ pověření klienta. V části jsou prvky vazby, které určují požadavky na zabezpečení. Konkrétně prověřte > prvek \<security u každé vazby. Tento element zahrnuje atribut `mode`, který můžete nastavit na jednu ze tří možných hodnot (`Message`, `Transport` nebo `TransportWithMessageCredential`). Hodnota atributu určuje režim a režim určuje, které z podřízených prvků jsou významné.  
  
 Element `<security>` může obsahovat buď prvek `<transport>` nebo `<message>`, nebo obojí. Významný prvek je ten, který odpovídá režimu zabezpečení. Například následující kód určuje, že režim zabezpečení je `"Message"` a typ přihlašovacích údajů klienta pro prvek `<message>` je `"Certificate"`. V tomto případě lze prvek `<transport>` ignorovat. Element `<message>` však Určuje, že je nutné zadat certifikát X. 509.  

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

 Všimněte si, že pokud je atribut `clientCredentialType` nastaven na hodnotu `"Windows"`, jak je znázorněno v následujícím příkladu, nemusíte zadávat skutečnou hodnotu přihlašovacích údajů. Je to proto, že integrované zabezpečení systému Windows poskytuje skutečné přihlašovací údaje (token protokolu Kerberos) pro osobu, která spouští klienta.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>Nastavení hodnoty přihlašovacích údajů klienta  
 Pokud se zjistí, že klient musí zadat přihlašovací údaje, použijte ke konfiguraci klienta odpovídající metodu. Chcete-li například nastavit certifikát klienta, použijte metodu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>.  
  
 Běžným formulářem přihlašovacích údajů je certifikát X. 509. Přihlašovací údaje můžete dodat dvěma způsoby:  
  
- Programováním ve vašem klientském kódu (pomocí metody `SetCertificate`).  
  
 Přidáním oddílu [\<behaviors >](../configure-apps/file-schema/wcf/behaviors.md) konfiguračního souboru pro klienta a pomocí elementu `clientCredentials` (viz níže).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Nastavení hodnoty \<clientCredentials > v kódu  
 Chcete-li nastavit hodnotu [\<clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md) v kódu, musíte získat přístup k vlastnosti <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> třídy <xref:System.ServiceModel.ClientBase%601>. Vlastnost vrátí objekt <xref:System.ServiceModel.Description.ClientCredentials>, který umožňuje přístup k různým typům přihlašovacích údajů, jak je znázorněno v následující tabulce.  
  
|Vlastnost ClientCredential|Popis|Poznámky|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Vrátí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.|Představuje certifikát X. 509, který poskytl klient pro ověření ke službě.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Vrátí <xref:System.ServiceModel.Security.HttpDigestClientCredential>.|Představuje přihlašovací údaje protokolu HTTP Digest. Přihlašovací údaje jsou hash uživatelského jména a hesla.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Vrátí <xref:System.ServiceModel.Security.IssuedTokenClientCredential>.|Představuje vlastní token zabezpečení vydaný službou tokenů zabezpečení, který se běžně používá ve federačních scénářích.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Vrátí <xref:System.ServiceModel.Security.PeerCredential>.|Představuje přihlašovací údaje partnerského vztahu pro účast v partnerské síti v doméně systému Windows.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Vrátí <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>.|Představuje certifikát X. 509 poskytovaný službou při vzdáleném vyjednávání.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Vrátí <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>.|Představuje dvojici uživatelského jména a hesla.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Vrátí <xref:System.ServiceModel.Security.WindowsClientCredential>.|Představuje přihlašovací údaje klienta Windows (přihlašovací údaje Kerberos). Vlastnosti třídy jsou jen pro čtení.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Nastavení hodnoty \<clientCredentials > v konfiguraci  
 Hodnoty přihlašovacích údajů se zadává pomocí chování koncového bodu jako podřízené prvky [> elementu \<clientCredentials](../configure-apps/file-schema/wcf/clientcredentials.md) . Použitý prvek závisí na typu pověření klienta. Například následující příklad ukazuje konfiguraci pro nastavení certifikátu X. 509 pomocí <[\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
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
  
 Chcete-li nastavit pověření klienta v konfiguraci, přidejte do konfiguračního souboru prvek [\<endpointBehaviors >](../configure-apps/file-schema/wcf/endpointbehaviors.md) . Kromě toho musí být přidaný prvek chování propojen s koncovým bodem služby pomocí atributu `behaviorConfiguration` [\<endpoint > elementu \<client >](../configure-apps/file-schema/wcf/endpoint-of-client.md) , jak je znázorněno v následujícím příkladu. Hodnota atributu `behaviorConfiguration` se musí shodovat s hodnotou atributu Behavior `name`.  

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
> Některé hodnoty přihlašovacích údajů klienta nelze nastavit pomocí konfiguračních souborů aplikace, například uživatelské jméno a heslo nebo hodnoty uživatele a hesla systému Windows. Tyto hodnoty přihlašovacích údajů lze zadat pouze v kódu.  
  
 Další informace o nastavení přihlašovacích údajů klienta najdete v tématu [Postupy: určení hodnot přihlašovacích údajů klienta](how-to-specify-client-credential-values.md).  
  
> [!NOTE]
> `ClientCredentialType` se ignoruje, pokud je `SecurityMode` nastaveno na `"TransportWithMessageCredential",`, jak je znázorněno v následující ukázkové konfiguraci.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [@no__t – 1bindings >](../configure-apps/file-schema/wcf/bindings.md)
- [Editor konfigurace (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)
- [Zabezpečení služeb](securing-services.md)
- [Přístup ke službám pomocí klienta WCF](accessing-services-using-a-wcf-client.md)
- [Postupy: Zadání hodnot přihlašovacích údajů klienta](how-to-specify-client-credential-values.md)
- [Nástroj metadat modelu služby (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Postupy: Určení typu přihlašovacích údajů klienta](how-to-specify-the-client-credential-type.md)
