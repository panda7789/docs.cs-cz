---
title: Přístup ke službám WCF pomocí klientské aplikace pro Windows Store
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: 484fad33614ca2b9507ed88aadfc1a41bb216c28
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261112"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>Přístup ke službám WCF pomocí klientské aplikace pro Windows Store
Systém Windows 8 zavádí nový typ aplikace s názvem aplikace Windows Store. Tyto aplikace jsou navržené s ohledem dotykové obrazovce rozhraní. Rozhraní .NET framework 4.5 umožňuje aplikacím Windows Store pro volání služeb WCF.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Podpora WCF v aplikacích Windows Store  
 Podmnožinu funkcí WCF je k dispozici z aplikace pro Windows Store, naleznete v následujících částech Další informace.  
  
> [!IMPORTANT]
>  Místo nastavení WCF vystavené pomocí syndikace WinRT rozhraní API. Další informace najdete v tématu [API WinRT syndikace](https://go.microsoft.com/fwlink/?LinkId=236265)  
  
> [!WARNING]
>  Použití přidat odkaz na službu přidat odkaz webové služby ke komponentě ve Windows Runtime není podporováno.  
  
### <a name="supported-bindings"></a>Podporované vazby  
 Podporují se následující vazby WCF v aplikacích Windows Store:  
  
1.  <xref:System.ServiceModel.BasicHttpBinding>  
  
2.  <xref:System.ServiceModel.NetTcpBinding>  
  
3.  <xref:System.ServiceModel.NetHttpBinding>  
  
4.  <xref:System.ServiceModel.Channels.CustomBinding>
  
 Jsou podporovány následující elementy vazby v aplikacích Windows Store  
  
1.  <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2.  <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3.  <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4.  <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5.  <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6.  <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7.  <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8.  <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Textové a binární kódování jsou podporovány. Podporují se všechny režimy přenos WCF. Další informace najdete v tématu [streamování přenosu zpráv](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Přidání odkazu na službu  
 K volání služby WCF z aplikace pro Windows Store, použijte funkci Přidat odkaz na službu sady Visual Studio 2012. Uvidíte několik změn ve funkcionalitě přidat odkaz na službu po dokončení aplikace pro Windows Store. Nejprve je generován žádný konfigurační soubor. Aplikace Windows Store nepoužívejte konfiguračních souborů, takže musí být nakonfigurovány v kódu. Tento kód konfigurace najdete v souboru References.cs generovaných přidat odkaz na službu. Pokud chcete zobrazit tento soubor, ujistěte se, že v Průzkumníku řešení vyberte "Zobrazit všechny soubory". Soubor se nachází v odkazy na služby a potom Reference.svcmap uzly v rámci projektu. Všechny operace, které jsou generovány pro služby WCF v rámci aplikace Windows Store bude asynchronní pomocí asynchronní vzor založený na úlohách. Další informace najdete v tématu [úloh s modifikátorem Async - zjednodušit Asynchronous Programming with úlohy](https://msdn.microsoft.com/magazine/ff959203.aspx).  
  
 Vzhledem k tomu, že konfigurace je nyní generována v kódu, všechny změny provedené v souboru Reference.cs přepsána pokaždé, když se aktualizuje odkaz na službu. Chcete tuto situaci napravit generování kódu konfigurace v rámci částečné metody, které můžete implementovat ve své třídě proxy serveru klienta. Částečné metody je deklarována následovně:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Potom můžete Implementujte tuto částečnou metodu a změnit vazby nebo koncový bod ve své třídě proxy serveru klienta následujícím způsobem:  
  
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
 Podporují se následující serializátory v aplikacích Windows Store:  
  
1.  DataContractSerializer  
  
2.  DataContractJsonSerializer  
  
3.  XmlSerializer  
  
> [!WARNING]
>  XmlDictionaryWriter.Write(DateTime) nyní zapíše objekt data a času jako řetězec.  
  
### <a name="security"></a>Zabezpečení  

Podporují se následující režimy zabezpečení v aplikacích Windows Store:
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
V aplikacích Windows Store jsou podporovány následující typy přihlašovacích údajů klienta:
  
1.  Žádná  
  
2.  Základní  
  
3.  ověřování algoritmem Digest  
  
4.  Vyjednávání  
  
5.  NTLM  
  
6.  Windows  
  
7.  Uživatelské jméno (zabezpečení zpráv)  
  
8.  Windows (Transport Security)  
  
 V pořadí pro aplikace Windows Store a přístup k odeslání výchozí přihlašovací údaje Windows je nutné povolit tuto funkci v rámci souboru Package.appmanifest. Otevřete tento soubor a vyberte kartu Možnosti a vyberte "Výchozí pověření Windows". To umožňuje aplikaci připojovat k intranetovým prostředkům, které vyžadují přihlašovací údaje domény.  
  
> [!IMPORTANT]
>  V pořadí pro aplikace Windows Store pro volání napříč počítači je potřeba povolit další funkce, označované jako "Domů a do práce sítě". Toto nastavení je také v souboru Package.appmanifest na kartě Možnosti. Zaškrtněte políčko síť domů a do práce. Díky tomu, které příchozí a odchozí přístup k sítím uživatel vaší důvěryhodné místech, jako jsou domácí nebo pracovní aplikace. Příchozí kritickým portům je vždycky blokovaný. Pro přístup ke službám v Internetu musí také povolit funkci Internet (klient).  
  
### <a name="misc"></a>Různé  
 Pro aplikace Windows Store je podporováno použití následující třídy:  
  
1.  <xref:System.ServiceModel.ChannelFactory>  
  
2.  <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3.  <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Definování kontraktů mezi službami  
 Doporučujeme pouze definování operace asynchronní služby pomocí úkolově orientovanou asynchronní vzorek. Tím se zajistí, že Windows Store aplikace nadále reagovat při volání operace služby.  
  
> [!WARNING]
>  Zatímco bude vyvolána žádná výjimka, pokud definujete synchronní operace, důrazně doporučujeme pouze definovat asynchronních operací.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>Volání služby WCF v aplikacích Windows Store  
 Jak už bylo uvedeno dříve, je třeba provést všechny konfigurace v kódu v metodě GetBindingForEndpoint ve třídě vygenerovaný proxy server. Volání operace služby se provádí stejný jako voláním jakékoli asynchronní metody založené na úlohách, jak je znázorněno v následujícím fragmentu kódu.  
  
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
  
 Všimněte si použití async – klíčové slovo v metodě provádění asynchronního volání a klíčové slovo await při volání asynchronní metody.  
  
## <a name="see-also"></a>Viz také:
- [WCF v blogu aplikace Windows Store](https://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)
- [Klienti WCF Windows Store a zabezpečení](https://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)
- [Aplikace Windows Store a volání mezi počítači](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [Volání služby WCF nasazené v Azure z aplikace pro Windows Store](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [Programování zabezpečení WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Vazby](../../../../docs/framework/wcf/bindings.md)
