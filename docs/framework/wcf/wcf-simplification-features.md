---
title: Funkce zjednodušení WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e465713fb33d438ef6e4a508fc5192ce731b46b5
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="wcf-simplification-features"></a>Funkce zjednodušení WCF
Toto téma popisuje nové funkce, které zápis WCF aplikace jednodušší.  
  
## <a name="simplified-generated-configuration-files"></a>Zjednodušená generované konfigurační soubory  
 Při přidání odkazu služby v sadě Visual Studio nebo pomocí nástroje SvcUtil.exe generuje soubor konfigurace klienta. V předchozích verzích služby WCF tyto konfigurační soubory obsažené hodnotu každé vlastnosti vazby, i když její hodnota je výchozí hodnota. Ve WCF 4.5 generované konfigurační soubory, které obsahují pouze vazby vlastnosti, které jsou nastaveny na jiné než výchozí hodnotu.  
  
 Následuje příklad konfiguračního souboru generované WCF 3.0.  
  
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
  
 Následuje příklad stejného souboru konfigurace generované WCF 4.5.  
  
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
  
## <a name="contract-first-development"></a>Vývoj s včasným kontraktu  
 WCF nyní obsahuje podporu pro vývoj s včasným kontrakt. Nástroj svcutl.exe má /serviceContract přepínač, který vám umožní generovat kontraktů služby a data z dokumentu WSDL.  
  
## <a name="add-service-reference-from-a-portable-subset-project"></a>Přidat odkaz na službu z přenosném dílčím projektu  
 Projekty přenosném dílčím povolit programátorům sestavení .NET udržovat stromu jednoho zdroje a sestavení systému, přičemž musí zároveň podporovat více implementace rozhraní .NET (plochy, Silverlight, Windows Phone a XBOX). Projekty přenosném dílčím odkazovat pouze na přenosné knihovny .NET, které jsou sestavení rozhraní .NET framework, který lze použít na žádnou implementaci rozhraní .NET. Možnosti vývojáře je stejný jako přidání odkazu na službu v rámci žádnou jinou aplikaci klienta WCF. Další informace najdete v tématu [přidat odkaz na službu v přenosných dílčím projektu](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).  
  
## <a name="aspnet-compatibility-mode-default-changed"></a>Výchozí režim kompatibility ASP.NET změnit  
 WCF poskytuje režim kompatibility ASP.NET udělit vývojáři úplný přístup k funkcím v kanálu ASP.NET HTTP při zápisu služby WCF. Chcete-li použít tento režim, musíte nastavit `aspNetCompatibilityEnabled` atributu na hodnotu true v [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) části souboru Web.config. Kromě toho musí mít všechny služby v této doméně appDomain `RequirementsMode` vlastnost na jeho <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> nastavena na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> nebo <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Ve výchozím nastavení <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> je teď nastavená na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> a výchozí WCF služby sady šablony aplikace `aspNetCompatibilityEnabled` atribut `true`. Další informace najdete v tématu [co je nového ve Windows Communication Foundation 4.5](../../../docs/framework/wcf/whats-new.md) a [služby WCF a ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="streaming-improvements"></a>Streamování vylepšení  
  
-   Nová podpora pro asynchronní streamování přidala do WCF. Chcete-li povolit asynchronní streamování, přidejte <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> chování koncového bodu do hostitele služby a nastavte její <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> vlastnost `true`.  Škálovatelnost to může přinést výhody při služby odesílá proudu zpráv do více klientů, které jsou čtení pomalu. WCF neblokuje jedno vlákno na jeden klienta už a uvolní vlákno služby jiného klienta.  
  
-   Odebrané omezení kolem ukládání do vyrovnávací paměti zpráv po služby hostované služby IIS. V předchozích verzích služby WCF při přijímání zprávy pro služby hostované službou IIS, který používá streamování přenosu zpráv ASP.NET by vyrovnávací paměti celé zprávy před odesláním do WCF. To by způsobilo spotřeby velké paměti. Tato ukládání do vyrovnávací paměti byla odebrána v rozhraní .NET 4.5 a služby WCF hostované IIS můžete spustit nyní zpracování příchozí datový proud před celá zpráva byla přijata, a umožňuje true streamování. To umožňuje WCF reagovat okamžitě na zprávy a umožňuje lepší výkon. Kromě toho už muset zadat hodnotu pro `maxRequestLength`, limit velikosti ASP.NET na příchozí požadavky. Pokud je tato vlastnost nastavena, je ignorován. [!INCLUDE[crabout](../../../includes/crabout-md.md)] `maxRequestLength` v tématu [ \<httpRuntime > konfigurační prvek](http://go.microsoft.com/fwlink/?LinkId=223344). Je stále nutné nakonfigurovat maxAllowedContentLength, další informace najdete v tématu [omezení počtu požadavků služby IIS](http://go.microsoft.com/fwlink/?LinkId=225908).  
  
## <a name="new-transport-default-values"></a>Nové výchozí hodnoty přenosu  
 Následující tabulka popisuje nastavení, které se změnily a kde najít další informace.  
  
|Vlastnost|On|Nový výchozí|Další informace|  
|--------------|--------|-----------------|----------------------|  
|ChannelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 sekund|Tato vlastnost určuje, jak dlouho může trvat připojení TCP kterými se ověří pomocí .net rámců protokolu. Klient musí poslat některé počáteční data předtím, než má server dostatek informací k provedení ověřování. Tento časový limit přišla záměrně menší než ReceiveTimeout (10 min.), tak, aby se zlými úmysly neověřené klienty by neměly být připojení svázané k serveru pro dlouho. Výchozí hodnota je 30 sekund. [!INCLUDE[crdefault](../../../includes/crabout-md.md)]<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|  
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * počet procesorů|Tato vlastnost úrovni soketu popisuje "přijmout čekající na vyřízení" počet požadavků ve frontě. Pokud nevyřízených položek fronty naslouchání zaplní, budou odmítnuty nové žádosti o soketu. [!INCLUDE[crdefault](../../../includes/crabout-md.md)]<xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|  
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * počet procesorů pro přenos<br /><br /> 4 \* počet procesorů pro SMSvcHost.exe|Tato vlastnost omezuje počet kanálů, které server může mít čekání na naslouchací proces. Když MaxPendingAccepts příliš nízké, budou existovat malé interval času, ve kterém všechny kanály čekání spustili obsluhy připojení, ale nové kanály, které jste začali naslouchá. Připojení může doručení během tohoto intervalu a selže, protože nic čeká se na serveru. Tato vlastnost se dá nakonfigurovat nastavení <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> vlastnost, která má vyšší číslo. Další informace najdete v tématu <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> a [konfigurace služby Sdílení portů Net.TCP](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * počet procesorů|Tato vlastnost určuje, kolik připojení přenosu přijal ale nebyly zachyceny ServiceModel dispečera. Pokud chcete nastavit tuto hodnotu, použijte `MaxConnections` na vazby nebo `maxOutboundConnectionsPerEndpoint` u prvku vazby. [!INCLUDE[crdefault](../../../includes/crabout-md.md)]<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|  
|receiveTimeout|SMSvcHost.exe|30 sekund|Tato vlastnost určuje časový limit pro čtení dat rámcovacích TCP a provádění připojení odeslání od základní připojení. To existuje umístí cap množství času, který je ponechat službu SMSvcHost.exe aktivnější číst data preambule z příchozího připojení. Další informace najdete v tématu [konfigurace služby Sdílení portů Net.TCP](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).|  
  
> [!NOTE]
>  Tyto nové výchozí hodnoty se používají pouze v případě, že nasazení služby WCF na počítači s rozhraní .NET Framework 4.5. Pokud nasadíte stejnou službu na počítači s rozhraní .NET Framework 4.0, je použito výchozí nastavení rozhraní .NET Framework 4.0. V takových případech se doporučuje k nakonfigurování těchto nastavení explicitně.  
  
## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas  
 <xref:System.Xml.XmlDictionaryReaderQuotas> obsahuje hodnoty konfigurovat kvóty pro slovník čtečky XML, které omezit množství paměti využívaných kodér při vytváření zprávu. Při těchto kvót se dají konfigurovat, výchozí hodnoty změnili na zmírnění možnost, že vývojář potřeba explicitně nastaven. `MaxReceivedMessageSize` kvóta nebylo změněno tak, aby ho stále můžete omezit využití paměti brání potřebu zabývat složitosti <xref:System.Xml.XmlDictionaryReaderQuotas>. Následující tabulka uvádí kvóty, nové výchozí hodnoty a stručné vysvětlení každé kvóty používá pro.  
  
|Název kvóty|Výchozí hodnota|Popis|  
|----------------|-------------------|-----------------|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Int32.MaxValue|Získá nebo nastaví maximální povolená délka pole. Tato kvóta omezuje maximální velikost pole primitivních elementů, které vrací čtecí modul XML, včetně pole bajtů. Tato kvóta neomezuje využití paměti v samotné čtecí modul XML, ale v jakémkoli součásti používající čtečky. Například, když <xref:System.Runtime.Serialization.DataContractSerializer> používá čtečku zabezpečen <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, ji deserializovat není větší než tato kvóta pole bajtů.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Int32.MaxValue|Získá nebo nastaví maximální povolený počet bajtů, vrátí pro každou čtení. Tato kvóta omezí počet bajtů, které se čtou v rámci jedné operace čtení při čtení element spuštění značku a její atributy. (V případech,-streamování, není počítáno samotný název elementu proti kvóta). Má příliš mnoho atributů XML může použít až nesoustředil příliš velký doba zpracování, protože názvy atributů musí být vráceny jedinečnosti. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> omezuje tuto hrozbu.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|hloubkové 128 uzlů|Tato kvóta omezuje maximální hloubky vnoření elementů XML.  <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> komunikuje s <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>: Čtečka vždy uchovává data v paměti pro aktuální prvek a veškeré jeho předchůdců, je spotřeba maximální paměť čtečky úměrný tato dvě nastavení. Při deserializaci hluboko vnořený objekt grafu, pro přístup k celý zásobník a throw k neodstranitelné je nucen deserializátor <xref:System.StackOverflowException>. Přímá korelace mezi vnoření XML a objekt vnoření obě existuje <xref:System.Runtime.Serialization.DataContractSerializer> a <!--zz <xref:System.Runtime.Serialization.XmlSerializer>--> `System.Runtime.Serialization.XmlSerializer`. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> slouží k zmírnění této hrozby.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Int32.MaxValue|Tato kvóta omezuje maximální počet povolených znaků v tabulky názvů. Pracovat s tabulkou názvů obsahuje některé řetězce (například obory názvů a předpony), které jsou došlo při zpracování dokument XML. Jak tyto řetězce jsou uložená do vyrovnávací paměti v paměti, tato kvóta se používá při prevenci nadměrné ukládání do vyrovnávací paměti při streamování se očekává.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Int32.MaxValue|Tato kvóta omezuje velikost maximální řetězec, který vrací čtecí modul XML. Tato kvóta neomezuje využití paměti v samotné čtecí modul XML, ale v komponentě používající čtečky. Například, když <xref:System.Runtime.Serialization.DataContractSerializer> používá čtečku zabezpečen <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, ji deserializovat není větší než tato kvóta řetězce.|  
  
> [!IMPORTANT]
>  Odkazovat na "Pomocí XML bezpečně" v části [důležité informace o zabezpečení pro Data](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md) Další informace o zabezpečení vaše data.  
  
> [!NOTE]
>  Tyto nové výchozí hodnoty se používají pouze v případě, že nasazení služby WCF na počítači s rozhraní .NET Framework 4.5. Pokud nasadíte stejnou službu na počítači s rozhraní .NET Framework 4.0, je použito výchozí nastavení rozhraní .NET Framework 4.0. V takových případech se doporučuje k nakonfigurování těchto nastavení explicitně.  
  
## <a name="wcf-configuration-validation"></a>Ověření konfigurace WCF  
 Jako součást procesu sestavení v sadě Visual Studio se teď ověří WCF konfigurační soubory. Seznam chyb při ověřování nebo upozornění se zobrazí v sadě Visual Studio, pokud se ověření nezdaří.  
  
## <a name="xml-editor-tooltips"></a>Popisy tlačítek Editor XML  
 Abyste pomohli nových nebo stávajících vývojáři služeb WCF konfigurace služeb, editor souborů XML Visual Studio teď poskytuje popisy tlačítek pro každý element, konfigurace a její vlastnosti, které je součástí konfigurační soubor služby.  
  
## <a name="basichttpbinding-improvements"></a>Vylepšení BasicHttpBinding  
  
1.  Umožňuje jeden koncový bod WCF reagovat na různá ověřovací režimy.  
  
2.  Umožňuje nastavení zabezpečení služby WCF pro řízení službou IIS
