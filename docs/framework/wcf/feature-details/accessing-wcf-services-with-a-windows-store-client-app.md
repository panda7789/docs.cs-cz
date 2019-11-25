---
title: Přístup ke službám WCF pomocí klientské aplikace pro Windows Store
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: f5cc18973231f327ee161946a235cb8b8b2ea5a7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978187"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>Přístup ke službám WCF pomocí klientské aplikace pro Windows Store
Systém Windows 8 zavádí nový typ aplikace s názvem aplikace pro Windows Store. Tyto aplikace jsou navržené kolem rozhraní dotykové obrazovky. .NET Framework 4,5 umožňuje aplikacím pro Windows Store volat služby WCF.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Podpora WCF v aplikacích pro Windows Store  
 V aplikaci pro Windows Store je k dispozici podmnožina funkcí WCF, další informace najdete v následujících částech.  
  
> [!IMPORTANT]
> Místo těch, která služba WCF vystavuje, použijte rozhraní API syndikace WinRT. Další informace najdete v tématu [rozhraní API syndikace WinRT](https://go.microsoft.com/fwlink/?LinkId=236265) .  
  
> [!WARNING]
> Přidání odkazu webové služby na prostředí Windows Runtime komponentu pomocí Přidat odkaz na službu se nepodporuje.  
  
### <a name="supported-bindings"></a>Podporované vazby  
 Následující vazby WCF jsou podporovány v aplikacích pro Windows Store:  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 Následující prvky vazby jsou podporovány v aplikacích pro Windows Store.  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Podporují se textové i binární kódování. Podporují se všechny režimy přenosu WCF. Další informace najdete v tématu [streamování přenosu zpráv](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Přidání odkazu na službu  
 Chcete-li volat službu WCF z aplikace pro Windows Store, použijte funkci Přidat odkaz na službu sady Visual Studio 2012. V rámci aplikace pro Windows Store si všimnete několika změn ve funkcích Přidat odkaz na službu. První konfigurační soubor není vygenerován. Aplikace pro Windows Store nepoužívají konfigurační soubory, takže je nutné je nakonfigurovat v kódu. Tento konfigurační kód najdete v souboru References.cs generovaném pomocí Přidat odkaz na službu. Tento soubor zobrazíte tak, že v Průzkumníku řešení vyberete možnost Zobrazit všechny soubory. Soubor se nachází pod odkazy na služby a pak odkazuje na uzly. svcmap v rámci projektu. Všechny operace generované pro služby WCF v rámci aplikace pro Windows Store budou asynchronní pomocí asynchronního vzoru založeného na úlohách. Další informace najdete v tématu [asynchronní úlohy – zjednodušení asynchronního programování s úkoly](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).  
  
 Vzhledem k tomu, že konfigurace je nyní vygenerována v kódu, všechny změny provedené v souboru Reference.cs by byly přepsány při každé aktualizaci odkazu na službu. Chcete-li tuto situaci napravit, je konfigurační kód generován v rámci částečné metody, kterou můžete implementovat do klientské proxy třídy. Částečná metoda je deklarována takto:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Pak můžete implementovat tuto částečnou metodu a změnit vazbu nebo koncový bod ve vaší klientské proxy třídě následujícím způsobem:  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {   
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,   
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a>Serializace  
 Následující serializace jsou podporovány v aplikacích pro Windows Store:  
  
1. DataContractSerializer  
  
2. DataContractJsonSerializer  
  
3. Objekt  
  
> [!WARNING]
> Implementace XmlDictionaryWriter. Write (DateTime) nyní zapisuje objekt DateTime jako řetězec.  
  
### <a name="security"></a>Zabezpečení  

V aplikacích pro Windows Store jsou podporovány následující režimy zabezpečení:
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
V aplikacích pro Windows Store jsou podporovány následující typy přihlašovacích údajů klienta:
  
1. Žádné  
  
2. Základní  
  
3. otisk  
  
4. Mluví  
  
5. NTLM  
  
6. Windows  
  
7. Uživatelské jméno (zabezpečení zpráv)  
  
8. Windows (zabezpečení přenosu)  
  
 Aby aplikace pro Windows Store měly přístup k výchozím přihlašovacím údajům systému Windows a odesílají je, musíte tuto funkci povolit v souboru Package. AppManifest. Otevřete tento soubor a vyberte kartu Možnosti a vyberte možnost výchozí pověření systému Windows. To umožňuje aplikaci připojovat se k prostředkům v intranetu, které vyžadují přihlašovací údaje domény.  
  
> [!IMPORTANT]
> Aby se aplikace pro Windows Store daly uskutečnit mezi počítači, musíte povolit jinou funkci nazvanou "domácí/pracovní síť". Toto nastavení je také v souboru Package. AppManifest na kartě Možnosti. zaškrtněte políčko domů/pracovní sítě. Tím zajistíte příchozí a odchozí přístup k sítím důvěryhodných míst uživatele, jako jsou doma a práce. Příchozí kritické porty jsou vždycky blokované. Pro přístup ke službám na internetu musíte povolit taky možnost Internet (klient).  
  
### <a name="misc"></a>Různé  
 Pro aplikace pro Windows Store je podporováno použití následujících tříd:  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Definování kontraktů služby  
 Doporučujeme definovat pouze asynchronní operace služby pomocí asynchronního vzoru založeného na úlohách. To zajistí, že aplikace pro Windows Store při volání operace služby budou reagovat.  
  
> [!WARNING]
> I když se nevyvolá žádná výjimka, pokud definujete synchronní operaci, důrazně doporučujeme definovat pouze asynchronní operace.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>Volání služeb WCF z aplikací pro Windows Store  
 Jak je uvedeno dříve, je nutné provést veškerou konfiguraci v kódu v metodě GetBindingForEndpoint ve vygenerované třídě proxy serveru. Volání operace služby je provedeno stejně jako volání jakékoli asynchronní metody založené na úlohách, jak je znázorněno v následujícím fragmentu kódu.  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 Všimněte si použití klíčového slova Async v metodě umožňující asynchronní volání a klíčové slovo await při volání asynchronní metody.  
  
## <a name="see-also"></a>Viz také:

- [Blog WCF v aplikacích pro Windows Store](https://blogs.msdn.microsoft.com/piyushjo/2011/09/21/wcf-in-windows-8-metro-styled-apps-absolutely-supported/)
- [Klienti a zabezpečení WCF Windows Store](https://blogs.msdn.microsoft.com/piyushjo/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security/)
- [Aplikace pro Windows Store a volání mezi počítači](https://blogs.msdn.microsoft.com/piyushjo/2011/10/21/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario/)
- [Volání služby WCF nasazené v Azure z aplikace pro Windows Store](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [Programování zabezpečení WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Vazby](../../../../docs/framework/wcf/bindings.md)
