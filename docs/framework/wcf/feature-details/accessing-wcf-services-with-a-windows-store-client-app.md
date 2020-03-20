---
title: Přístup ke službám WCF pomocí klientské aplikace pro Windows Store
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: b4b91c103aa91e3b2c9e811c642a8347c7db1a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185486"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>Přístup ke službám WCF pomocí klientské aplikace pro Windows Store
Windows 8 zavádí nový typ aplikace s názvem Windows Store aplikace. Tyto aplikace jsou navrženy kolem rozhraní dotykové obrazovky. Rozhraní .NET Framework 4.5 umožňuje aplikacím pro Windows Store volat služby WCF.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Podpora WCF v aplikacích pro Windows Store  
 Podmnožina funkcí WCF je k dispozici v rámci aplikace pro Windows Store, další podrobnosti najdete v následujících částech.  
  
> [!IMPORTANT]
> Použijte winrt syndikace API namísto těch vystavených WCF. Další informace naleznete v tématu [WinRT Syndication API](xref:Windows.Web.Syndication)  
  
> [!WARNING]
> Přidání odkazu na službu k přidání odkazu webové služby na součást prostředí Windows Runtime není podporováno.  
  
### <a name="supported-bindings"></a>Podporovaná vazby  
 V aplikacích pro Windows Store jsou podporovány následující vazby WCF:  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 V aplikacích pro Windows Store jsou podporovány následující elementy vazby  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Jsou podporovány kódování Text i Binární. Všechny režimy přenosu WCF jsou podporovány. Další informace naleznete v tématu [Streamování přenosu zpráv](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Přidání odkazu na službu  
 Chcete-li volat službu WCF z aplikace pro Windows Store, použijte funkci Přidat odkaz na službu v sadě Visual Studio 2012. Pokud se provede v aplikaci pro Windows Store, všimnete si několika změn ve funkcích přidat odkaz na službu. Nejprve není generován žádný konfigurační soubor. Aplikace pro Windows Store nepoužívají konfigurační soubory, takže musí být nakonfigurovány v kódu. Tento konfigurační kód naleznete v souboru References.cs generovaném nástrojem Přidat odkaz na službu. Chcete-li zobrazit tento soubor, ujistěte se, že v průzkumníku řešení vyberete možnost Zobrazit všechny soubory. Soubor bude umístěn pod odkazy na služby a potom Reference.svcmap uzly v rámci projektu. Všechny operace generované pro služby WCF v rámci aplikace pro Windows Store budou asynchronní pomocí asynchronního vzoru založeného na úlohách. Další informace naleznete [v tématu Asynchronní úlohy – zjednodušení asynchronního programování pomocí úloh](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).  
  
 Vzhledem k tomu, že konfigurace je nyní generována v kódu, všechny změny provedené v souboru Reference.cs by být přepsány při každé aktualizaci odkazu na službu. K nápravě této situace je konfigurační kód generován v rámci částečné metody, kterou můžete implementovat ve třídě proxy klienta. Částečná metoda se deklaruje takto:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Potom můžete implementovat tuto částečnou metodu a změnit vazbu nebo koncový bod ve třídě proxy klienta takto:  
  
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
 V aplikacích pro Windows Store jsou podporovány následující serializátory:  
  
1. DataContractSerializer  
  
2. Datacontractjsonserializer  
  
3. Xmlserializer  
  
> [!WARNING]
> XmlDictionaryWriter.Write(DateTime) nyní zapíše objekt DateTime jako řetězec.  
  
### <a name="security"></a>Zabezpečení  

V aplikacích pro Windows Store jsou podporovány následující režimy zabezpečení:
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
V aplikacích pro Windows Store jsou podporovány následující typy pověření klienta:
  
1. Žádný  
  
2. Basic  
  
3. Digest  
  
4. Negotiate  
  
5. NTLM  
  
6. Windows  
  
7. Uživatelské jméno (Zabezpečení zpráv)  
  
8. Windows (zabezpečení přenosu)  
  
 Aby aplikace pro Windows Store mohly přistupovat k výchozím přihlašovacím údajům systému Windows a odesílat je, musíte tuto funkci povolit v souboru Package.appmanifest. Otevřete tento soubor a vyberte kartu Možnosti a vyberte "Výchozí pověření systému Windows". To umožňuje aplikaci připojit se k prostředkům intranetu, které vyžadují pověření domény.  
  
> [!IMPORTANT]
> Aby aplikace pro Windows Store mohly volat mezi počítači, musíte povolit další funkci nazvanou "Domácí/pracovní síť". Toto nastavení je také v souboru Package.appmanifest na kartě Možnosti. To poskytuje aplikaci příchozí a odchozí přístup k sítím důvěryhodných míst uživatele, jako je domov a práce. Příchozí kritické porty jsou vždy blokovány. Pro přístup ke službám na Internetu musíte také povolit možnost i pro připojení k Internetu (Client).  
  
### <a name="misc"></a>Různé  
 Pro aplikace pro Windows Store je podporováno použití následujících tříd:  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Definování servisních smluv  
 Doporučujeme pouze definování asynchronních operací služby pomocí asynchronního vzoru založeného na úlohách. Tím zajistíte, že aplikace pro Windows Store zůstanou responzivní při volání operace služby.  
  
> [!WARNING]
> Zatímco žádná výjimka bude vyvolána, pokud definujete synchronní operaci, důrazně doporučujeme definovat pouze asynchronní operace.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>Volání služeb WCF z aplikací pro Windows Store  
 Jak již bylo zmíněno dříve všechny konfigurace musí být provedeno v kódu v GetBindingForEndpoint metoda v generované proxy třídy. Volání operace služby se provádí stejně jako volání jakékoli asynchronní metody založené na úlohách, jak je znázorněno v následujícím fragmentu kódu.  
  
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
  
 Všimněte si použití asynchronní ho klíčovéslovo na metodu, která asynchronní volání a await klíčové slovo při volání asynchronní metody.  
  
## <a name="see-also"></a>Viz také

- [WCF v blogu o aplikacích pro Windows Store](https://docs.microsoft.com/archive/blogs/piyushjo/wcf-in-windows-8-metro-styled-apps-absolutely-supported)
- [Klienti a zabezpečení wCF Windows Store](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-adding-security)
- [Aplikace pro Windows Store a volání napříč počítači](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [Volání služby WCF nasazené v Azure z aplikace pro Windows Store](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [Programování zabezpečení WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Vazby](../../../../docs/framework/wcf/bindings.md)
