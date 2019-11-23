---
title: Funkce zjednodušení WCF
ms.date: 03/30/2017
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
ms.openlocfilehash: 85c50e5939a5e63202d57bca08393b9b79308f57
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321218"
---
# <a name="wcf-simplification-features"></a>Funkce zjednodušení WCF

Toto téma popisuje nové funkce, které zjednodušují psaní aplikací WCF.

## <a name="simplified-generated-configuration-files"></a>Zjednodušené generované konfigurační soubory

Když přidáte odkaz na službu v aplikaci Visual Studio nebo použijete nástroj SvcUtil. exe, vygeneruje se konfigurační soubor klienta. V předchozích verzích služby WCF tyto konfigurační soubory obsahovaly hodnotu každé vlastnosti vazby, a to i v případě, že její hodnota je výchozí hodnota. Ve WCF 4,5 generované konfigurační soubory obsahují pouze vlastnosti vazby, které jsou nastaveny na hodnotu, která není výchozí.

Následuje příklad konfiguračního souboru vygenerovaného službou WCF 3,0.

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

Následuje příklad stejného konfiguračního souboru generovaného službou WCF 4,5.

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

## <a name="contract-first-development"></a>Vývoj pro první smlouvu

WCF teď podporuje vývoj pro první smlouvu. Nástroj Svcutil. exe má přepínač/serviceContract, který umožňuje vygenerovat kontrakty služeb a dat z dokumentu WSDL.

## <a name="add-service-reference-from-a-portable-subset-project"></a>Přidat odkaz na službu z přenositelné podmnožiny projektu

Přenositelné podmnožiny projektů umožňují programátorům sestavení .NET udržovat jeden zdrojový strom a systém sestavení a přitom stále podporovat více implementací .NET (Desktop, Silverlight, Windows Phone a XBOX). Přenositelné Podmnožinové projekty odkazují pouze na přenosné knihovny .NET, které jsou sestavením rozhraní .NET Framework, které lze použít v jakékoli implementaci rozhraní .NET. Prostředí pro vývojáře je stejné jako přidání odkazu na službu do jakékoli jiné klientské aplikace WCF. Další informace naleznete v tématu [Přidat odkaz na službu v přenositelné podmnožině projektu](add-service-reference-in-a-portable-subset-project.md).

## <a name="aspnet-compatibility-mode-default-changed"></a>Režim kompatibility ASP.NET se ve výchozím nastavení změnil

Služba WCF poskytuje ASP.NET režim kompatibility pro udělení přístupu vývojářům úplný přístup k funkcím v kanálu HTTP ASP.NET při psaní služeb WCF. Chcete-li použít tento režim, je nutné nastavit atribut `aspNetCompatibilityEnabled` na hodnotu true v části [\<serviceHostingEnvironment >](../configure-apps/file-schema/wcf/servicehostingenvironment.md) souboru Web. config. Kromě toho musí mít kterákoli služba v této doméně appDomain vlastnost `RequirementsMode` v <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> nastavená na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> nebo <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Ve výchozím nastavení je <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> nyní nastaveno na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> a výchozí šablona aplikace služby WCF nastaví atribut `aspNetCompatibilityEnabled` na `true`. Další informace najdete v tématu [co je nového v Windows Communication Foundation 4,5](whats-new.md) a [službách WCF a ASP.NET](./feature-details/wcf-services-and-aspnet.md).

## <a name="streaming-improvements"></a>Vylepšení streamování

- Do WCF se přidala nová podpora pro asynchronní streamování. Pokud chcete povolit asynchronní streamování, přidejte do hostitele služby chování koncového bodu <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> a nastavte jeho vlastnost <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> na `true`. Tato možnost může přinést škálovatelnost, když služba odesílá streamované zprávy více klientům, které se čtou pomalu. WCF již neblokuje jedno vlákno na klienta a uvolní vlákno pro obsluhu jiného klienta.

- Odebrala se omezení týkající se ukládání zpráv do vyrovnávací paměti, když je služba IIS hostovaná. V předchozích verzích služby WCF při přijímání zprávy pro službu hostovanou službou IIS, která používala přenos zpráv, ASP.NET by mohla celou zprávu ukládat do vyrovnávací paměti před odesláním do WCF. To by způsobilo velkou spotřebu paměti. Toto ukládání do vyrovnávací paměti se odebralo v .NET 4,5 a teď můžou služby WCF hostované službou IIS začít zpracovávat příchozí datový proud před přijetím celé zprávy a tím umožnit skutečné streamování. Díky tomu může WCF reagovat okamžitě na zprávy a povolit Vylepšený výkon. Navíc už nemusíte zadávat hodnotu pro `maxRequestLength`, omezení velikosti ASP.NET příchozích požadavků. Je-li tato vlastnost nastavena, je ignorována. Další informace o `maxRequestLength` naleznete v části [\<httpRuntime > elementu konfigurace](https://go.microsoft.com/fwlink/?LinkId=223344). Pořád budete muset nakonfigurovat maxAllowedContentLength. Další informace najdete v tématu [omezení požadavků služby IIS](https://go.microsoft.com/fwlink/?LinkId=225908).

## <a name="new-transport-default-values"></a>Nové výchozí hodnoty přenosu

Následující tabulka popisuje nastavení, která se změnila a kde najít další informace.

|Vlastnost|Zapnuto|Nové výchozí|Další informace|
|--------------|--------|-----------------|----------------------|
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 sekund|Tato vlastnost určuje, jak dlouho může připojení TCP trvat při ověřování pomocí protokolu rámců .NET. Klient potřebuje odeslat některá počáteční data předtím, než server bude mít dostatek informací k provedení ověření. Tento časový limit je úmyslně menší než ReceiveTimeout (10 min), aby škodlivé neověřené klienty neudržovaly připojení na server po dlouhou dobu. Výchozí hodnota je 30 sekund. Další informace o <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * počet procesorů|Tato vlastnost na úrovni soketu popisuje počet požadavků čekajících na přijetí k zařazení do fronty. Pokud nevyřízená fronta nevyřízených položek vyplní, budou nové požadavky na soket odmítnuty. Další informace o <xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * počet procesorů pro přenos<br /><br /> 4 \* počet procesorů pro SMSvcHost. exe|Tato vlastnost omezuje počet kanálů, které server může čekat na naslouchací proces. Pokud je MaxPendingAccepts příliš nízké, bude existovat malý časový interval, ve kterém budou všechny čekající kanály začali obsluhovat připojení, ale nezačaly naslouchat žádné nové kanály. Připojení může být doručeno během tohoto intervalu a selže, protože na serveru nebude nic čekat. Tuto vlastnost lze nakonfigurovat nastavením vlastnosti <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> na větší číslo. Další informace najdete v tématu <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> a [Konfigurace služby sdílení portů Net. TCP.](./feature-details/configuring-the-net-tcp-port-sharing-service.md)|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * počet procesorů|Tato vlastnost určuje, kolik připojení bylo přenosu přijato, ale nebyl vyzvednuta dispečerem ServiceModel. Chcete-li nastavit tuto hodnotu, použijte `MaxConnections` ve vazbě nebo `maxOutboundConnectionsPerEndpoint` elementu vazby. Další informace o <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|
|receiveTimeout|SMSvcHost.exe|30 sekund|Tato vlastnost určuje časový limit pro čtení dat rámců TCP a provádění odesílání připojení ze základních připojení. To znamená, že v době, kdy se služba SMSvcHost. exe zachová, je potřeba si přečíst data preambule z příchozího připojení. Další informace najdete v tématu [Konfigurace služby sdílení portů Net. TCP](./feature-details/configuring-the-net-tcp-port-sharing-service.md).|

> [!NOTE]
> Tyto nové výchozí hodnoty se použijí pouze v případě, že nasadíte službu WCF do počítače s .NET Framework 4,5. Pokud nasadíte stejnou službu do počítače s .NET Framework 4,0, použijí se výchozí hodnoty .NET Framework 4,0. V takových případech se doporučuje nakonfigurovat tato nastavení explicitně.

## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas

<xref:System.Xml.XmlDictionaryReaderQuotas> obsahuje konfigurovatelné hodnoty kvóty pro čtečky slovníku XML, které omezují velikost paměti využívané kodérem při vytváření zprávy. I když jsou tyto kvóty konfigurovatelné, výchozí hodnoty se změní tak, aby se minimalizovala možnost, že ji vývojář bude muset explicitně nastavit. kvóta `MaxReceivedMessageSize` se nezměnila, takže může stále omezit spotřebu paměti, takže nemusíte řešit složitost <xref:System.Xml.XmlDictionaryReaderQuotas>. V následující tabulce jsou uvedeny kvóty, jejich nové výchozí hodnoty a stručné vysvětlení toho, jaká kvóta se používá pro.

|Název kvóty|Výchozí hodnota|Popis|
|----------------|-------------------|-----------------|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Int32.MaxValue|Získá a nastaví maximální povolenou délku pole. Tato kvóta omezuje maximální velikost pole primitivních elementů, které vrátí čtecí modul XML, včetně bajtových polí. Tato kvóta neomezuje spotřebu paměti v samotném čtecím modulu XML, ale v jakékoli součásti, která používá čtecí modul. Například pokud <xref:System.Runtime.Serialization.DataContractSerializer> používá čtecí modul zabezpečený s <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, neprovádí deserializaci polí bajtů větší než tato kvóta.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Int32.MaxValue|Získá a nastaví maximální povolené bajty vracené pro každou přečtenou. Tato kvóta omezuje počet bajtů, které jsou čteny při jedné operaci čtení při čtení značky začátek elementu a jeho atributů. (V nestreamované případech se název elementu sám nepočítá s kvótou). Příliš mnoho atributů XML může použít neúměrný čas zpracování, protože názvy atributů musí být zkontrolovány pro jedinečnost. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> snižuje riziko této hrozby.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|128 uzlů na hloubku|Tato kvóta omezuje maximální hloubku vnořování prvků XML. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> komunikuje s <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>: čtecí modul vždy uchovává data v paměti pro aktuální prvek a všechny jeho nadřazené prvky, takže maximální spotřeba paměti čtecího zařízení je úměrná produktu těchto dvou nastavení. Při deserializaci diagramu hluboko vnořeného objektu je pro deserializaci nucen přístup k celému zásobníku a vyvolat neobnovitelné <xref:System.StackOverflowException>. Mezi vnořeným kódem XML a vnořeným objektem pro <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer>existuje přímá korelace. pro zmírnění této hrozby se používá <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Int32.MaxValue|Tato kvóta omezuje maximální povolený počet znaků NameTable. NameTable obsahuje určité řetězce (například obory názvů a předpony), které byly zjištěny při zpracování dokumentu XML. Vzhledem k tomu, že jsou tyto řetězce uloženy do vyrovnávací paměti, se tato kvóta používá k zamezení nadměrnému ukládání do vyrovnávací paměti, když se očekává streamování.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Int32.MaxValue|Tato kvóta omezuje maximální velikost řetězce, kterou čtecí modul XML vrátí. Tato kvóta neomezuje spotřebu paměti v samotném čtecím modulu XML, ale v komponentě, která používá čtecí modul. Například pokud <xref:System.Runtime.Serialization.DataContractSerializer> používá čtecí modul zabezpečený s <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, neprovádí deserializaci řetězců větší než tato kvóta.|

> [!IMPORTANT]
> Další informace o zabezpečení dat najdete v tématu věnovaném bezpečnému používání XML v tématu [požadavky na zabezpečení pro data](./feature-details/security-considerations-for-data.md) .

> [!NOTE]
> Tyto nové výchozí hodnoty se použijí pouze v případě, že nasadíte službu WCF do počítače s .NET Framework 4,5. Pokud nasadíte stejnou službu do počítače s .NET Framework 4,0, použijí se výchozí hodnoty .NET Framework 4,0. V takových případech se doporučuje nakonfigurovat tato nastavení explicitně.

## <a name="wcf-configuration-validation"></a>Ověřování konfigurace WCF

V rámci procesu sestavení v sadě Visual Studio jsou nyní ověřovány konfigurační soubory služby WCF. V aplikaci Visual Studio se zobrazí seznam chyb nebo upozornění ověřování, pokud se ověření nepovede.

## <a name="xml-editor-tooltips"></a>Popisy editoru XML

Editor XML sady Visual Studio nyní poskytuje popisy pro každý prvek konfigurace a jeho vlastnosti, které jsou součástí konfiguračního souboru služby, aby bylo možné pomáhat novým a stávajícím vývojářům služby WCF konfigurovat své služby.

## <a name="basichttpbinding-improvements"></a>Vylepšení BasicHttpBinding

1. Umožňuje jednomu koncovému bodu WCF reagovat na různé režimy ověřování.

2. Umožňuje řídit nastavení zabezpečení služby WCF pomocí služby IIS.
