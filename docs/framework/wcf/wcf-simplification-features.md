---
title: Funkce zjednodušení WCF
ms.date: 03/30/2017
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
ms.openlocfilehash: 010f941850dedd73e9cc203ea2b180dae7d4742c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526350"
---
# <a name="wcf-simplification-features"></a>Funkce zjednodušení WCF
Toto téma popisuje nové funkce, které usnadňují zápis WCF aplikací jednodušší.  
  
## <a name="simplified-generated-configuration-files"></a>Zjednodušená generovaných konfiguračních souborů  
 Při přidání odkazu na službu v sadě Visual Studio nebo pomocí nástroje SvcUtil.exe je vygenerován soubor konfigurace klienta. V předchozích verzích technologie WCF tyto konfigurační soubory obsahují hodnotu každé vlastnosti vazby i v případě, že její hodnota je výchozí hodnota. Ve WCF 4.5 generovaných konfiguračních souborů obsahují pouze vlastnosti vazby, které jsou nastaveny na jiné než výchozí hodnotu.  
  
 Následuje příklad konfiguračního souboru generovaných WCF 3.0.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="BasicHttpBinding_IService1" closeTimeout="00:01:00"  
                    openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00"  
                    allowCookies="false" bypassProxyOnLocal="false"   
                    hostNameComparisonMode="StrongWildcard" maxBufferSize="65536"   
                    maxBufferPoolSize="524288" maxReceivedMessageSize="65536"  
                    messageEncoding="Text" textEncoding="utf-8" transferMode="Buffered"  
                    useDefaultWebProxy="true">  
                    <readerQuotas maxDepth="32" maxStringContentLength="8192"   
                        maxArrayLength="16384" maxBytesPerRead="4096"  
                        maxNameTableCharCount="16384" />  
                    <security mode="None">  
                        <transport clientCredentialType="None" proxyCredentialType="None"  
                            realm="" />  
                        <message clientCredentialType="UserName" algorithmSuite="Default" />  
                    </security>  
                </binding>  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"  
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"  
                name="BasicHttpBinding_IService1" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
 Následuje příklad konfiguračního souboru stejné generovaných WCF 4.5.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="BasicHttpBinding_IService1" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"  
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"  
                name="BasicHttpBinding_IService1" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="contract-first-development"></a>Rozvoje prvního kontraktu  
 WCF teď obsahují podporu pro rozvoje prvního kontraktu. Nástroj svcutl.exe má /serviceContract přepínač, který vám umožní generovat kontrakty služby a dat z dokumentu WSDL.  
  
## <a name="add-service-reference-from-a-portable-subset-project"></a>Přidání odkazu na službu v přenosném dílčím projektu  
 Přenosném dílčím projekty povolit programátorům sestavení .NET udržovat stromu jednoho zdrojového kódu a sestavovací systém. současně podporuje více implementací rozhraní .NET (desktop, Silverlight, Windows Phone a XBOX). Projekty v přenosném dílčím odkazovat pouze na přenosné knihovny .NET, které jsou sestavení rozhraní .NET framework, který lze použít v jakékoli implementaci rozhraní .NET. Prostředí pro vývojáře je stejné jako přidávání odkazů na služby v rámci jakékoli jiné aplikace klienta WCF. Další informace najdete v tématu [přidat odkaz na službu v projektu přenosná podmnožina](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).  
  
## <a name="aspnet-compatibility-mode-default-changed"></a>Změnit výchozí režim kompatibility ASP.NET  
 WCF obsahuje režim kompatibility ASP.NET vývojáři udělit úplný přístup k funkcím v kanálu HTTP technologie ASP.NET při vytváření služeb WCF. Pro použití tohoto režimu, je nutné nastavit `aspNetCompatibilityEnabled` atribut na hodnotu true [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) části souboru Web.config. Kromě toho musí mít všechny služby v této doméně appDomain `RequirementsMode` vlastnost na jeho <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> nastavena na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> nebo <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Ve výchozím nastavení <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> je nyní nastaveno na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> a výchozí WCF služby aplikace šablony nastaví `aspNetCompatibilityEnabled` atribut `true`. Další informace najdete v tématu [co je nového ve Windows Communication Foundation 4.5](../../../docs/framework/wcf/whats-new.md) a [služby WCF a ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="streaming-improvements"></a>Vylepšení datových proudů  
  
-   Nová podpora asynchronního streamování se přidala do WCF. Pokud chcete povolit, asynchronního streamování, přidejte <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> chování koncového bodu do hostitele služby a nastavte jeho <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> vlastnost `true`.  To mohou využívat škálovatelnost, když služba odesílá proudu zpráv do více klientů, které čtou pomalu. WCF neblokuje jedno vlákno na jeden klienta už a tím uvolnit vlákno pro službu jiného klienta.  
  
-   Odebrání omezení vyrovnávací paměti zpráv, když je služba IIS hostované. V předchozích verzích služby WCF při přijetí zprávy služby hostované v IIS, který používá streamování přenosu zpráv by ASP.NET buffer celé zprávy před odesláním do WCF. To by způsobilo velké paměťové nároky. Tato ukládání do vyrovnávací paměti byla odebrána v rozhraní .NET 4.5 a služby WCF hostované v IIS teď můžete začít zpracování příchozího datového proudu před celá zpráva byla přijata, a tím umožnit true streamování. To umožňuje okamžitě reagovat na zprávy WCF a vylepšení výkonu. Kromě toho již nebude muset zadat hodnotu `maxRequestLength`, omezení velikosti technologie ASP.NET pro příchozí požadavky. Pokud je tato vlastnost nastavena, je ignorována. Další informace o `maxRequestLength` naleznete v tématu [ \<httpRuntime > element konfigurace](https://go.microsoft.com/fwlink/?LinkId=223344). Budete stále muset nakonfigurovat maxAllowedContentLength, další informace naleznete v tématu [omezení počtu požadavků služby IIS](https://go.microsoft.com/fwlink/?LinkId=225908).  
  
## <a name="new-transport-default-values"></a>Nové výchozí hodnoty přenosu  
 Následující tabulka popisuje nastavení, které se změnily a kde najít další informace.  
  
|Vlastnost|On|Nová výchozí hodnota|Další informace|  
|--------------|--------|-----------------|----------------------|  
|třídě channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 sekund|Tato vlastnost určuje, jak dlouho může trvat připojení TCP autentizaci pomocí .net Framing protokolu. Klient potřebuje k odesílání nějaká počáteční data předtím, než má server dostatek informací k provedení ověřování. Tento časový limit je záměrně provedli menší než ReceiveTimeout (10 minut) tak, aby škodlivé neověřené klienty nezachovat připojení vázané na serveru pro dlouho. Výchozí hodnota je 30 sekund. Další informace o <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|  
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * počet procesorů|Tato vlastnost úrovni soketu popisuje počet "čekající na přijmout" požadavky ve frontě. Pokud nevyřízené položky fronty naslouchání zaplní, budou odmítnuty nové žádosti o soketu. Další informace o <xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|  
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * počet procesorů pro přenos<br /><br /> 4 \* počtu procesorů pro SMSvcHost.exe|Tato vlastnost omezuje počet kanálů, které serveru může být čekání na naslouchací proces. Když MaxPendingAccepts je příliš nízké, bude existovat malý interval času, ve kterém všechny kanály čekání spustili údržby připojení, ale nové kanály, které jste začali naslouchání. Připojení můžou přijít během tohoto intervalu a selže, protože nic čeká se na serveru. Tuto vlastnost lze nastavit tak, že nastavíte <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> vlastnost většímu počtu. Další informace najdete v tématu <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> a [konfigurace služby Sdílení portů Net.TCP](https://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * počet procesorů|Tato vlastnost určuje, kolik připojení přenosu přijal, ale nebyly vyzvednou ServiceModel dispečera. Chcete-li nastavit tuto hodnotu, použijte `MaxConnections` ve vazbě nebo `maxOutboundConnectionsPerEndpoint` v elementu vazby. Další informace o <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|  
|receiveTimeout|SMSvcHost.exe|30 sekund|Tato vlastnost určuje časový limit pro vytváření datových rámců TCP a jejich odesílání z podkladové připojení. To existuje umístí limitu množství času, které se ukládají SMSvcHost.exe služby znamenají angažovaní číst data preambule z příchozí připojení. Další informace najdete v tématu [konfigurace služby Sdílení portů Net.TCP](https://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).|  
  
> [!NOTE]
>  Tyto nové výchozí hodnoty se používají pouze v případě, že nasadíte služby WCF na počítači s rozhraním .NET Framework 4.5. Pokud provádíte nasazení stejnou službu na počítači pomocí rozhraní .NET Framework 4.0, jsou použity výchozí hodnoty rozhraní .NET Framework 4.0. V takových případech se doporučuje k nakonfigurování těchto nastavení explicitně.  
  
## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas  
 <xref:System.Xml.XmlDictionaryReaderQuotas> obsahuje hodnoty konfigurovatelné kvóty pro čtenáře slovníku XML, které omezují množství paměťových prostředků využívaných kodéru při vytváření zprávy. Během těchto kvót je možné konfigurovat, výchozí hodnoty změnily snižovat, vývojář musí explicitně nastavena možnost. `MaxReceivedMessageSize` kvóta nebylo změněno tak, aby ji stále může omezit spotřebu paměti brání nutnost řešit složité <xref:System.Xml.XmlDictionaryReaderQuotas>. V následující tabulce jsou uvedeny kvóty, nové výchozí hodnoty a stručné vysvětlení, co každá kvóta slouží.  
  
|Název kvóty|Výchozí hodnota|Popis|  
|----------------|-------------------|-----------------|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Hodnota Int32.MaxValue|Získá nebo nastaví maximální povolené délky pole. Tato kvóta omezuje maximální velikost pole primitivních elementů, které vrací čtecí funkce XML, včetně pole bajtů. Tato kvóta neomezuje využití paměti v samotné čtecí funkce XML, ale v libovolné součásti, která používá čtecí modul. Například, když <xref:System.Runtime.Serialization.DataContractSerializer> použije čtečku zabezpečený pomocí <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, není ji deserializovat bajtová pole větší než tuto kvótu.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Hodnota Int32.MaxValue|Získá nebo nastaví maximální povolené bajty vrácené pro každé čtení. Tato kvóta omezuje počet bajtů, které jsou pro čtení v rámci jedné operace čtení při čtení elementu spuštění značku a její atributy. (V případech,-datovým proudem, se nepočítá samotný název elementu proti kvótu). Máte příliš mnoho atributů XML může použít nepřiměřené doba zpracování, protože názvy atributů musí být vráceny jedinečný. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> omezuje tuto hrozbu.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|hloubkové 128 uzlů|Tato kvóta omezuje maximální hloubka vnoření elementů XML.  <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> komunikuje se službou <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>: čtecí modul dat vždy udržuje v paměti pro aktuální element a všechny jeho předchůdce, tak maximální velikost paměti spotřeba čtečky je úměrný tato dvě nastavení. Při deserializaci graf objektu nejhlouběji vnořená, deserializátor musí pro přístup k celý zásobník a vyvolat neodstranitelné <xref:System.StackOverflowException>. Mezi XML vnoření a objekt vnoření pro obě existuje přímou spojitost s míněním <xref:System.Runtime.Serialization.DataContractSerializer> a <!--zz <xref:System.Runtime.Serialization.XmlSerializer>--> `System.Runtime.Serialization.XmlSerializer`. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> slouží ke zmírnění této hrozby.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Hodnota Int32.MaxValue|Tato kvóta omezuje maximální počet znaků povolených v tabulky názvů. Tabulka obsahuje některé řetězce (například obory názvů a předpony), jež byly objeveny při zpracování dokumentu XML. Protože tyto řetězce jsou ukládány do vyrovnávací paměti v paměti, tuto kvótu slouží aby se zabránilo nadměrnému ukládání do vyrovnávací paměti při streamování se očekává.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Hodnota Int32.MaxValue|Tato kvóta omezení maximální velikost řetězce, který vrací čtecí funkce XML. Tato kvóta neomezuje využití paměti v samotné čtecí funkce XML, ale v komponentě, která používá čtecí modul. Například, když <xref:System.Runtime.Serialization.DataContractSerializer> použije čtečku zabezpečený pomocí <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, to není deserializaci řetězců větší než tuto kvótu.|  
  
> [!IMPORTANT]
>  Odkazovat na "Pomocí XML bezpečně" v části [aspekty zabezpečení pro Data](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md) pro další informace o zabezpečení vašich dat.  
  
> [!NOTE]
>  Tyto nové výchozí hodnoty se používají pouze v případě, že nasadíte služby WCF na počítači s rozhraním .NET Framework 4.5. Pokud provádíte nasazení stejnou službu na počítači pomocí rozhraní .NET Framework 4.0, jsou použity výchozí hodnoty rozhraní .NET Framework 4.0. V takových případech se doporučuje k nakonfigurování těchto nastavení explicitně.  
  
## <a name="wcf-configuration-validation"></a>Ověření konfigurace WCF  
 Jako součást procesu sestavení v sadě Visual Studio se teď ověřují konfiguračních souborů WCF. Pokud se ověření nezdaří, zobrazí se seznam chyby nebo varování ověření v sadě Visual Studio.  
  
## <a name="xml-editor-tooltips"></a>Popisy tlačítek editoru XML  
 Aby pomohli se nové i stávající vývojáři služeb WCF ke konfiguraci jeho služeb, editoru XML pro Visual Studio nyní poskytuje popisky pro každý prvek konfigurace a její vlastnosti, které je součástí konfiguračního souboru služby.  
  
## <a name="basichttpbinding-improvements"></a>Vylepšení BasicHttpBinding  
  
1.  Umožňuje jednom koncovém bodu WCF na ověřování pro různé režimy.  
  
2.  Umožňuje řídit pomocí služby IIS nastavení zabezpečení služby WCF
