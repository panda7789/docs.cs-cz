---
title: "Přístup ke službám WCF pomocí klientské aplikace pro Windows Store"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df5e05b1896ee272e286102a6c9433fad51b3c98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>Přístup ke službám WCF pomocí klientské aplikace pro Windows Store
Windows 8 zavádí nový typ aplikace s názvem aplikace pro Windows Store. Tyto aplikace jsou uspořádaná kolem rozhraní, které je dotykovou obrazovku. Rozhraní .NET framework 4.5 umožňuje aplikace pro Windows Store pro volání služby WCF.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Podpora WCF v aplikacích pro Windows Store  
 Podmnožinu funkcí WCF je k dispozici v aplikaci pro Windows Store, najdete v následujících částech Další podrobnosti.  
  
> [!IMPORTANT]
>  Syndikace WinRT rozhraní API použijte místo nastavení vystavené WCF. Další informace najdete v tématu [WinRT syndikace API](http://go.microsoft.com/fwlink/?LinkId=236265)  
  
> [!WARNING]
>  Použití přidat odkaz na službu přidat odkaz na webovou službu komponent prostředí Windows Runtime není podporováno.  
  
### <a name="supported-bindings"></a>Podporované vazby  
 Podporovány jsou následující vazby WCF v aplikacích Windows Store:  
  
1.  <xref:System.ServiceModel.BasicHttpBinding>  
  
2.  <xref:System.ServiceModel.NetTcpBinding>  
  
3.  <xref:System.ServiceModel.NetHttpBinding>  
  
4.  <xref:System.ServiceModel.Channels.CustomBinding>
  
 Následující prvky vazby jsou podporovány v aplikacích Windows Store  
  
1.  <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2.  <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3.  <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4.  <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5.  <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6.  <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7.  <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8.  <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Textové a binární kódování jsou podporovány. Jsou podporovány všechny režimy přenosu WCF. Další informace najdete v tématu [streamování přenosu zpráv](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Přidání odkazu na službu  
 Chcete-li volání služby WCF z aplikace Windows Store, použijte funkci Přidat odkaz na službu sady Visual Studio 2012. Ve funkci Přidat odkaz na službu po dokončení v aplikaci Windows Store si všimněte několik změn. Nejprve se generuje žádný konfigurační soubor. Aplikace pro Windows Store se nedoporučuje používat konfigurační soubory, musí být nakonfigurované v kódu. Tento kód konfigurace naleznete v souboru References.cs generované přidat odkaz na službu. Pokud chcete zobrazit tento soubor, je nutné vybrat "Zobrazit všechny soubory" v Průzkumníku řešení. Soubor se nachází pod odkazy na službu a pak Reference.svcmap uzlů v rámci projektu. Všechny operace vygenerované služby WCF v aplikaci Windows Store budou asynchronní pomocí asynchronní vzor založený na úlohách. Další informace najdete v tématu [Task-based Asynchronous Pattern](http://msdn.microsoft.com/magazine/ff959203.aspx).  
  
 Vzhledem k tomu, že konfigurace je nyní generování v kódu, veškeré změny provedené v souboru Reference.cs budou přepsána pokaždé, když se aktualizuje odkaz na službu. Chcete-li opravit tuto situaci vygenerování kódu konfigurace v rámci částečné metody, které můžete zavést ve třídě proxy serveru klienta. Částečné metody je deklarovaná následujícím způsobem:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Potom můžete Implementujte tuto metodu, částečné a změnit vazby nebo koncový bod v třídě proxy serveru klienta následujícím způsobem:  
  
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
 Podporovány jsou následující serializátorů v aplikace pro Windows Store:  
  
1.  DataContractSerializer  
  
2.  DataContractJsonSerializer  
  
3.  Třídy XmlSerializer  
  
> [!WARNING]
>  XmlDictionaryWriter.Write(DateTime) nyní zapíše data a času objekt jako řetězec.  
  
### <a name="security"></a>Zabezpečení  
 V následujících režimech zabezpečení jsou podporovány v aplikace pro Windows Store  
  
1.  <xref:System.ServiceModel.SecurityMode.None>  
  
2.  <xref:System.ServiceModel.SecurityMode.Transport>  
  
3.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredentials> --> `System.ServiceModel.SecurityMode.TransportWithMessageCredentials`
  
4.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportCredentialOnly>  --> `System.ServiceModel.SecurityMode.TransportCredentialOnly`
  
 Jsou podporovány následující typy pověření klienta v aplikace pro Windows Store  
  
1.  Žádné  
  
2.  Základní  
  
3.  Ověřování algoritmem Digest  
  
4.  Vyjednávání  
  
5.  NTLM  
  
6.  Windows  
  
7.  Uživatelské jméno (zabezpečení zpráv)  
  
8.  Windows (zabezpečení přenosu)  
  
 Aby aplikace pro Windows Store pro přístup k a odeslat výchozí pověření systému Windows je nutné povolit tuto funkci v souboru Package.appmanifest. Umožňuje otevřít tento soubor a vyberte kartu Možnosti a vyberte "Výchozí pověření systému Windows". To umožňuje aplikaci připojovat k intranetovým prostředkům, které vyžadují přihlašovací údaje do domény.  
  
> [!IMPORTANT]
>  V pořadí pro aplikace pro Windows Store volání mezi počítači je třeba povolit další funkce s názvem "Domů a do práce sítě". Toto nastavení je také v souboru Package.appmanifest na kartě Možnosti. Zaškrtněte políčko síť domů a do práce. Díky tomu, které příchozí a odchozí přístup k sítím uživatele je důvěryhodné místech, jako třeba domácí a pracovní aplikace. Vždy jsou blokovány příchozí kritické porty. Pro přístup ke službám v síti internet, musíte zároveň povolit funkce Internet (klient).  
  
### <a name="misc"></a>Různé  
 Pro aplikace pro Windows Store je podporováno použití následující třídy:  
  
1.  <xref:System.ServiceModel.ChannelFactory>  
  
2.  <!--zz <xref:System.ServiceModel.DuplexChannelFactory> --> `System.ServiceModel.DuplexChannelFactory`
  
3.  <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Definování kontraktů mezi službami  
 Doporučujeme, abyste pouze definování operace asynchronní služby pomocí vzoru async založený na úlohách. Tím se zajistí, že při volání operace služby zůstanou reaguje aplikace pro Windows Store.  
  
> [!WARNING]
>  Zatímco bude vyvolána žádná výjimka, pokud definujete synchronní operace, důrazně doporučujeme pouze definovat asynchronní operace.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>Volání služby WCF z aplikace pro Windows Store  
 Jak je uvedeno nahoře všechny konfigurace je třeba provést v kódu v metodě GetBindingForEndpoint ve třídě vygenerovaný proxy server. Volání operace služby, se provádí stejný jako voláním jakékoli asynchronní metody založené na úlohách, jak je znázorněno v následující fragment kódu.  
  
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
  
 Všimněte si použití async – klíčové slovo na metodě provedení asynchronní volání a klíčové slovo await při volání asynchronní metody.  
  
## <a name="see-also"></a>Viz také  
 [WCF v blogu aplikace Windows Store](http://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)  
 [Klienti WCF Windows Store a zabezpečení](http://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)  
 [Aplikace pro Windows Store a křížové počítač volání](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [Volání služby WCF nasazené v Azure z aplikace pro Windows Store](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [Programování zabezpečení WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [Vazby](../../../../docs/framework/wcf/bindings.md)
