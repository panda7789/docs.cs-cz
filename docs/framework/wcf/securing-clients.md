---
title: Zabezpečení klientů
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dfbe1fcce8a3b860e88dae4f5af43adfedbe9890
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="securing-clients"></a>Zabezpečení klientů
Ve Windows Communication Foundation (WCF), služba určuje požadavky na zabezpečení pro klienty. To znamená službu určuje jakém režimu zabezpečení používat a jestli klient musí poskytnout přihlašovací údaje. Proces zabezpečení klienta, proto je jednoduchý: použijte metadata získat ze služby (Pokud je publikována) a sestavení klienta. Metadata Určuje, jak nakonfigurovat klienta. Pokud služba vyžaduje, aby klient zadejte pověření, je nutné získat přihlašovací údaje, které vyhovuje požadavku. Toto téma popisuje proces podrobněji. Další informace o vytvoření zabezpečeného služby najdete v tématu [zabezpečení služby](../../../docs/framework/wcf/securing-services.md).  
  
## <a name="the-service-specifies-security"></a>Služba určuje zabezpečení  
 Vazby WCF mají ve výchozím nastavení povolena funkce zabezpečení. (Výjimkou je <xref:System.ServiceModel.BasicHttpBinding>.) Proto pokud služba byla vytvořena pomocí WCF, existuje větší pravděpodobnost, že ji provede zabezpečení, ověřování, důvěrnost a integrita. V takovém případě metadat, které poskytuje služba označí, co vyžaduje vytvořit zabezpečený komunikační kanál. Pokud metadata služby neobsahuje žádné požadavky na zabezpečení, neexistuje žádný způsob, jak ukládat zabezpečení schématu, jako je například vrstvy SSL (Secure Sockets) prostřednictvím protokolu HTTP, ve službě. Pokud však služba vyžaduje, aby klient k zadání pověření, pak klient developer, nástroje pro nasazení nebo správce musíte zadat skutečné pověření, které bude klient používat ke svému ověření ke službě.  
  
## <a name="obtaining-metadata"></a>Získávání metadat  
 Při vytváření klienta, je použít k získání metadata pro službu, která bude klient komunikovat s prvním krokem. Tento krok můžete provést dvěma způsoby. První, pokud služba publikuje koncový bod metadat exchange (MEX) nebo jeho metadata zpřístupní protokol HTTP nebo HTTPS, si můžete stáhnout pomocí metadat [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), který generuje obě soubory kódu pro klienta, jakož i konfigurační soubor. (Další informace o použití nástroje najdete v tématu [přístup k službám pomocí klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).) Pokud službu nepublikuje koncový bod MEX a také zpřístupnění jeho metadata protokol HTTP nebo HTTPS, musí obrátíte creator služby dokumentace, která popisuje požadavky na zabezpečení a metadata.  
  
> [!IMPORTANT]
>  Doporučuje se, že metadata pocházejí z důvěryhodného zdroje a že nesmí být manipulováno. Metadata načíst pomocí protokolu HTTP je odesláno jako nezašifrovaný text a může být úmyslně poškozena. Pokud služba používá <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnosti, použijte adresu URL služby Tvůrce dodaná ke stahování dat pomocí protokolu HTTPS.  
  
## <a name="validating-security"></a>Ověřování zabezpečení  
 Metadata zdroje můžete rozdělit na dvě rozsáhlé kategorie: důvěřovat zdroje a nedůvěryhodných zdrojů. Pokud nedůvěřujete zdroji a mají stažené kód klienta a další metadata z tohoto zdroje zabezpečené MEX koncového bodu, pak můžete sestavit klienta, poskytne mu správné přihlašovací údaje a spusťte s žádné další otázky.  
  
 Pokud se rozhodnete stáhnout klienta a metadata ze zdroje, málo vědět o, je však nutné ověřit bezpečnostní opatření, která používá kód. Například nesmí vytvoříte jednoduše klienta, který odešle službě svoje osobní nebo finanční informace, pokud služba vyžaduje utajení a integrity (v každém). Vlastník služby by měla důvěřovat, pokud chcete tyto informace prozradit, protože tyto informace budou viditelné mu.  
  
 Platí pravidlo proto při použití kódu a metadata z nedůvěryhodného zdroje, zkontrolujte kód a metadata, aby kontrolovat, zda splňuje úroveň zabezpečení, které budete potřebovat.  
  
## <a name="setting-a-client-credential"></a>Nastavení přihlašovacích údajů klienta  
 Nastavení pověření klienta v klientském počítači se skládá ze dvou kroků:  
  
1.  Určení *typu pověření klienta* služba vyžaduje. To lze provést jedním ze dvou způsobů. První, pokud máte dokumentace z Tvůrce služby, se musí určovat pověření klienta vyžaduje službu typu (pokud existuje). Druhý Pokud máte pouze konfigurační soubor generované nástroje Svcutil.exe, můžete zkontrolovat jednotlivé vazby k určení, je třeba, jaký typ přihlašovacích údajů.  
  
2.  Zadejte pověření skutečné klienta. Je volána pověření skutečné klienta *hodnotu přihlašovacích údajů klienta* ho odlišuje od typu. Například pokud typu pověření klienta Určuje certifikát, je nutné zadat certifikát X.509, který je vydaný certifikační autoritou službu vztahy důvěryhodnosti.  
  
### <a name="determining-the-client-credential-type"></a>Určení typu pověření klienta  
 Pokud máte konfigurační soubor nástroje Svcutil.exe generované, zkontrolujte [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) zjistěte, jaký typ pověření klienta je požadovaná. V části jsou prvky vazby, které určují požadavky na zabezpečení. Konkrétně, zkontrolujte \<zabezpečení > Element každé vazby. Zahrnuje tohoto prvku `mode` atribut, který můžete nastavit na jedno ze tří možných hodnot (`Message`, `Transport`, nebo `TransportWithMessageCredential`). Hodnota atributu určuje režim a režim určí, které podřízených elementů je důležité.  
  
 `<security>` Element může obsahovat buď `<transport>` nebo `<message>` element nebo obojí. Důležitý prvek, je ten, který odpovídá režim zabezpečení. Například následující kód určuje, že režim zabezpečení je `"Message"`a klient pro typ přihlašovacích údajů `<message>` element je `"Certificate"`. V takovém případě `<transport>` element můžete ignorovat. Ale `<message>` element určuje, že je nutné zadat certifikát X.509.  
  
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
  
 Všimněte si, že pokud `clientCredentialType` je atribut nastaven na `"Windows"`, jak je znázorněno v následujícím příkladu, není potřeba zadat hodnotu skutečné přihlašovacích údajů. Je to proto, že integrované zabezpečení systému Windows poskytuje skutečné přihlašovacích údajů (token protokolu Kerberos) osoby, která běží klienta.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>Nastavení hodnoty přihlašovacích údajů klienta  
 Pokud je zjištěno, že klient musí poskytnout pověření, použijte odpovídající metodu konfigurace klienta. Například pokud chcete nastavit klientský certifikát, použijte <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metoda.  
  
 Běžnou přihlašovacích údajů je certifikát X.509. Můžete zadat přihlašovací údaje dvěma způsoby:  
  
-   Pomocí programování v klientském kódu (pomocí `SetCertificate` metoda).  
  
 Přidáním [ \<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) oddíl konfiguračního souboru pro klienta a pomocí `clientCredentials` – element (zobrazené dole).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Nastavení \<clientCredentials > hodnotu v kódu  
 Chcete-li nastavit [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) hodnotu v kódu, je nutné získat přístup <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> – třída. Vrátí vlastnosti <xref:System.ServiceModel.Description.ClientCredentials> objekt, který umožňuje přístup na různé typy přihlašovacích údajů, jak je znázorněno v následující tabulce.  
  
|Vlastnost ClientCredential|Popis|Poznámky|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Vrátí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|Představuje certifikát X.509 poskytnutý klientem ke svému ověření ke službě.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Vrátí <xref:System.ServiceModel.Security.HttpDigestClientCredential>|Představuje pověření HTTP digest. Přihlašovací údaje je hodnota hash uživatelské jméno a heslo.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Vrátí <xref:System.ServiceModel.Security.IssuedTokenClientCredential>|Představuje token vlastní zabezpečení vydané služby tokenů zabezpečení, často se používá ve scénářích federation.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Vrátí <xref:System.ServiceModel.Security.PeerCredential>|Představuje sdílené přihlašovací údaje pro účast v mřížku sdílené v doméně systému Windows.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Vrátí <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|Představuje certifikátu X.509. certifikát poskytovaný službou v out-of-band vyjednávání.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Vrátí <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|Reprezentuje dvojici uživatelské jméno a heslo.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Vrátí <xref:System.ServiceModel.Security.WindowsClientCredential>|Představuje pověření klienta systému Windows (Kerberos přihlašovací údaje). Vlastnosti třídy jsou jen pro čtení.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Nastavení \<clientCredentials > hodnota v konfiguraci  
 Přihlašovací údaje hodnoty jsou specifikované pomocí chování koncového bodu jako podřízených elementů [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element. Element používá závisí na typu pověření klienta. Například následující příklad ukazuje, konfigurace nastavení certifikát X.509 pomocí <[\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
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
  
 Chcete-li nastavit pověření klienta v konfiguraci, přidejte [ \<endpointBehaviors >](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element konfiguračního souboru. Kromě toho musí být propojena element přidané chování koncovému bodu služby pomocí `behaviorConfiguration` atribut [ \<koncový bod >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element, jak je znázorněno v následujícím příkladu. Hodnota `behaviorConfiguration` atributu musí odpovídat hodnotě chování `name` atribut.  
  
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
>  Některé z hodnot přihlašovacích údajů klienta nemůže být sada pomocí konfigurační soubory aplikace, třeba, uživatelské jméno a heslo, nebo uživatel systému Windows a hodnoty heslo. Tyto přihlašovací údaje hodnoty lze zadat pouze v kódu.  
  
 Další informace o nastavení pověření klienta najdete v tématu [postupy: určení hodnot přihlašovacích údajů klienta](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
> [!NOTE]
>  `ClientCredentialType` Když je ignorován `SecurityMode` je nastaven na `"TransportWithMessageCredential",` jak je znázorněno v následující ukázka konfigurace.  
  
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
