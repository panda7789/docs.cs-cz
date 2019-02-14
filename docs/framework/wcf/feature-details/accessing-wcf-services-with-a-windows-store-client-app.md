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
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="54ab6-102">Přístup ke službám WCF pomocí klientské aplikace pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="54ab6-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="54ab6-103">Systém Windows 8 zavádí nový typ aplikace s názvem aplikace Windows Store.</span><span class="sxs-lookup"><span data-stu-id="54ab6-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="54ab6-104">Tyto aplikace jsou navržené s ohledem dotykové obrazovce rozhraní.</span><span class="sxs-lookup"><span data-stu-id="54ab6-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="54ab6-105">Rozhraní .NET framework 4.5 umožňuje aplikacím Windows Store pro volání služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="54ab6-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="54ab6-106">Podpora WCF v aplikacích Windows Store</span><span class="sxs-lookup"><span data-stu-id="54ab6-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="54ab6-107">Podmnožinu funkcí WCF je k dispozici z aplikace pro Windows Store, naleznete v následujících částech Další informace.</span><span class="sxs-lookup"><span data-stu-id="54ab6-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="54ab6-108">Místo nastavení WCF vystavené pomocí syndikace WinRT rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="54ab6-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="54ab6-109">Další informace najdete v tématu [API WinRT syndikace](https://go.microsoft.com/fwlink/?LinkId=236265)</span><span class="sxs-lookup"><span data-stu-id="54ab6-109">For more information see, [WinRT Syndication API](https://go.microsoft.com/fwlink/?LinkId=236265)</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="54ab6-110">Použití přidat odkaz na službu přidat odkaz webové služby ke komponentě ve Windows Runtime není podporováno.</span><span class="sxs-lookup"><span data-stu-id="54ab6-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="54ab6-111">Podporované vazby</span><span class="sxs-lookup"><span data-stu-id="54ab6-111">Supported Bindings</span></span>  
 <span data-ttu-id="54ab6-112">Podporují se následující vazby WCF v aplikacích Windows Store:</span><span class="sxs-lookup"><span data-stu-id="54ab6-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1.  <xref:System.ServiceModel.BasicHttpBinding>  
  
2.  <xref:System.ServiceModel.NetTcpBinding>  
  
3.  <xref:System.ServiceModel.NetHttpBinding>  
  
4.  <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="54ab6-113">Jsou podporovány následující elementy vazby v aplikacích Windows Store</span><span class="sxs-lookup"><span data-stu-id="54ab6-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1.  <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2.  <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3.  <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4.  <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5.  <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6.  <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7.  <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8.  <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="54ab6-114">Textové a binární kódování jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="54ab6-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="54ab6-115">Podporují se všechny režimy přenos WCF.</span><span class="sxs-lookup"><span data-stu-id="54ab6-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="54ab6-116">Další informace najdete v tématu [streamování přenosu zpráv](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="54ab6-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="54ab6-117">Přidání odkazu na službu</span><span class="sxs-lookup"><span data-stu-id="54ab6-117">Add Service Reference</span></span>  
 <span data-ttu-id="54ab6-118">K volání služby WCF z aplikace pro Windows Store, použijte funkci Přidat odkaz na službu sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="54ab6-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="54ab6-119">Uvidíte několik změn ve funkcionalitě přidat odkaz na službu po dokončení aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="54ab6-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="54ab6-120">Nejprve je generován žádný konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="54ab6-120">First no configuration file is generated.</span></span> <span data-ttu-id="54ab6-121">Aplikace Windows Store nepoužívejte konfiguračních souborů, takže musí být nakonfigurovány v kódu.</span><span class="sxs-lookup"><span data-stu-id="54ab6-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="54ab6-122">Tento kód konfigurace najdete v souboru References.cs generovaných přidat odkaz na službu.</span><span class="sxs-lookup"><span data-stu-id="54ab6-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="54ab6-123">Pokud chcete zobrazit tento soubor, ujistěte se, že v Průzkumníku řešení vyberte "Zobrazit všechny soubory".</span><span class="sxs-lookup"><span data-stu-id="54ab6-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="54ab6-124">Soubor se nachází v odkazy na služby a potom Reference.svcmap uzly v rámci projektu.</span><span class="sxs-lookup"><span data-stu-id="54ab6-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="54ab6-125">Všechny operace, které jsou generovány pro služby WCF v rámci aplikace Windows Store bude asynchronní pomocí asynchronní vzor založený na úlohách.</span><span class="sxs-lookup"><span data-stu-id="54ab6-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="54ab6-126">Další informace najdete v tématu [úloh s modifikátorem Async - zjednodušit Asynchronous Programming with úlohy](https://msdn.microsoft.com/magazine/ff959203.aspx).</span><span class="sxs-lookup"><span data-stu-id="54ab6-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](https://msdn.microsoft.com/magazine/ff959203.aspx).</span></span>  
  
 <span data-ttu-id="54ab6-127">Vzhledem k tomu, že konfigurace je nyní generována v kódu, všechny změny provedené v souboru Reference.cs přepsána pokaždé, když se aktualizuje odkaz na službu.</span><span class="sxs-lookup"><span data-stu-id="54ab6-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="54ab6-128">Chcete tuto situaci napravit generování kódu konfigurace v rámci částečné metody, které můžete implementovat ve své třídě proxy serveru klienta.</span><span class="sxs-lookup"><span data-stu-id="54ab6-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="54ab6-129">Částečné metody je deklarována následovně:</span><span class="sxs-lookup"><span data-stu-id="54ab6-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="54ab6-130">Potom můžete Implementujte tuto částečnou metodu a změnit vazby nebo koncový bod ve své třídě proxy serveru klienta následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="54ab6-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
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
  
### <a name="serialization"></a><span data-ttu-id="54ab6-131">Serializace</span><span class="sxs-lookup"><span data-stu-id="54ab6-131">Serialization</span></span>  
 <span data-ttu-id="54ab6-132">Podporují se následující serializátory v aplikacích Windows Store:</span><span class="sxs-lookup"><span data-stu-id="54ab6-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1.  <span data-ttu-id="54ab6-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="54ab6-133">DataContractSerializer</span></span>  
  
2.  <span data-ttu-id="54ab6-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="54ab6-134">DataContractJsonSerializer</span></span>  
  
3.  <span data-ttu-id="54ab6-135">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="54ab6-135">XmlSerializer</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="54ab6-136">XmlDictionaryWriter.Write(DateTime) nyní zapíše objekt data a času jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="54ab6-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="54ab6-137">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="54ab6-137">Security</span></span>  

<span data-ttu-id="54ab6-138">Podporují se následující režimy zabezpečení v aplikacích Windows Store:</span><span class="sxs-lookup"><span data-stu-id="54ab6-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="54ab6-139">V aplikacích Windows Store jsou podporovány následující typy přihlašovacích údajů klienta:</span><span class="sxs-lookup"><span data-stu-id="54ab6-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1.  <span data-ttu-id="54ab6-140">Žádná</span><span class="sxs-lookup"><span data-stu-id="54ab6-140">None</span></span>  
  
2.  <span data-ttu-id="54ab6-141">Základní</span><span class="sxs-lookup"><span data-stu-id="54ab6-141">Basic</span></span>  
  
3.  <span data-ttu-id="54ab6-142">ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="54ab6-142">Digest</span></span>  
  
4.  <span data-ttu-id="54ab6-143">Vyjednávání</span><span class="sxs-lookup"><span data-stu-id="54ab6-143">Negotiate</span></span>  
  
5.  <span data-ttu-id="54ab6-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="54ab6-144">NTLM</span></span>  
  
6.  <span data-ttu-id="54ab6-145">Windows</span><span class="sxs-lookup"><span data-stu-id="54ab6-145">Windows</span></span>  
  
7.  <span data-ttu-id="54ab6-146">Uživatelské jméno (zabezpečení zpráv)</span><span class="sxs-lookup"><span data-stu-id="54ab6-146">Username (Message Security)</span></span>  
  
8.  <span data-ttu-id="54ab6-147">Windows (Transport Security)</span><span class="sxs-lookup"><span data-stu-id="54ab6-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="54ab6-148">V pořadí pro aplikace Windows Store a přístup k odeslání výchozí přihlašovací údaje Windows je nutné povolit tuto funkci v rámci souboru Package.appmanifest.</span><span class="sxs-lookup"><span data-stu-id="54ab6-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="54ab6-149">Otevřete tento soubor a vyberte kartu Možnosti a vyberte "Výchozí pověření Windows".</span><span class="sxs-lookup"><span data-stu-id="54ab6-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="54ab6-150">To umožňuje aplikaci připojovat k intranetovým prostředkům, které vyžadují přihlašovací údaje domény.</span><span class="sxs-lookup"><span data-stu-id="54ab6-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="54ab6-151">V pořadí pro aplikace Windows Store pro volání napříč počítači je potřeba povolit další funkce, označované jako "Domů a do práce sítě".</span><span class="sxs-lookup"><span data-stu-id="54ab6-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="54ab6-152">Toto nastavení je také v souboru Package.appmanifest na kartě Možnosti. Zaškrtněte políčko síť domů a do práce.</span><span class="sxs-lookup"><span data-stu-id="54ab6-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="54ab6-153">Díky tomu, které příchozí a odchozí přístup k sítím uživatel vaší důvěryhodné místech, jako jsou domácí nebo pracovní aplikace.</span><span class="sxs-lookup"><span data-stu-id="54ab6-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="54ab6-154">Příchozí kritickým portům je vždycky blokovaný.</span><span class="sxs-lookup"><span data-stu-id="54ab6-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="54ab6-155">Pro přístup ke službám v Internetu musí také povolit funkci Internet (klient).</span><span class="sxs-lookup"><span data-stu-id="54ab6-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="54ab6-156">Různé</span><span class="sxs-lookup"><span data-stu-id="54ab6-156">Misc</span></span>  
 <span data-ttu-id="54ab6-157">Pro aplikace Windows Store je podporováno použití následující třídy:</span><span class="sxs-lookup"><span data-stu-id="54ab6-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1.  <xref:System.ServiceModel.ChannelFactory>  
  
2.  <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3.  <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="54ab6-158">Definování kontraktů mezi službami</span><span class="sxs-lookup"><span data-stu-id="54ab6-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="54ab6-159">Doporučujeme pouze definování operace asynchronní služby pomocí úkolově orientovanou asynchronní vzorek.</span><span class="sxs-lookup"><span data-stu-id="54ab6-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="54ab6-160">Tím se zajistí, že Windows Store aplikace nadále reagovat při volání operace služby.</span><span class="sxs-lookup"><span data-stu-id="54ab6-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="54ab6-161">Zatímco bude vyvolána žádná výjimka, pokud definujete synchronní operace, důrazně doporučujeme pouze definovat asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="54ab6-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="54ab6-162">Volání služby WCF v aplikacích Windows Store</span><span class="sxs-lookup"><span data-stu-id="54ab6-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="54ab6-163">Jak už bylo uvedeno dříve, je třeba provést všechny konfigurace v kódu v metodě GetBindingForEndpoint ve třídě vygenerovaný proxy server.</span><span class="sxs-lookup"><span data-stu-id="54ab6-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="54ab6-164">Volání operace služby se provádí stejný jako voláním jakékoli asynchronní metody založené na úlohách, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="54ab6-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="54ab6-165">Všimněte si použití async – klíčové slovo v metodě provádění asynchronního volání a klíčové slovo await při volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="54ab6-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54ab6-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54ab6-166">See also</span></span>
- [<span data-ttu-id="54ab6-167">WCF v blogu aplikace Windows Store</span><span class="sxs-lookup"><span data-stu-id="54ab6-167">WCF in Windows Store Apps Blog</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)
- [<span data-ttu-id="54ab6-168">Klienti WCF Windows Store a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="54ab6-168">WCF Windows Store Clients and Security</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)
- [<span data-ttu-id="54ab6-169">Aplikace Windows Store a volání mezi počítači</span><span class="sxs-lookup"><span data-stu-id="54ab6-169">Windows Store Apps and Cross Machine Calls</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [<span data-ttu-id="54ab6-170">Volání služby WCF nasazené v Azure z aplikace pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="54ab6-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [<span data-ttu-id="54ab6-171">Programování zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="54ab6-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [<span data-ttu-id="54ab6-172">Vazby</span><span class="sxs-lookup"><span data-stu-id="54ab6-172">Bindings</span></span>](../../../../docs/framework/wcf/bindings.md)
