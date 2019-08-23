---
title: Přístup ke službám WCF pomocí klientské aplikace pro Windows Store
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: a2f1ef37914c932801699bb2f9c2323dd0408e7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964969"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="b2661-102">Přístup ke službám WCF pomocí klientské aplikace pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="b2661-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="b2661-103">Systém Windows 8 zavádí nový typ aplikace s názvem aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="b2661-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="b2661-104">Tyto aplikace jsou navržené kolem rozhraní dotykové obrazovky.</span><span class="sxs-lookup"><span data-stu-id="b2661-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="b2661-105">.NET Framework 4,5 umožňuje aplikacím pro Windows Store volat služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b2661-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="b2661-106">Podpora WCF v aplikacích pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="b2661-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="b2661-107">V aplikaci pro Windows Store je k dispozici podmnožina funkcí WCF, další informace najdete v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="b2661-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b2661-108">Místo těch, která služba WCF vystavuje, použijte rozhraní API syndikace WinRT.</span><span class="sxs-lookup"><span data-stu-id="b2661-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="b2661-109">Další informace najdete v tématu [rozhraní API syndikace WinRT](https://go.microsoft.com/fwlink/?LinkId=236265) .</span><span class="sxs-lookup"><span data-stu-id="b2661-109">For more information see, [WinRT Syndication API](https://go.microsoft.com/fwlink/?LinkId=236265)</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b2661-110">Přidání odkazu webové služby na prostředí Windows Runtime komponentu pomocí Přidat odkaz na službu se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="b2661-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="b2661-111">Podporované vazby</span><span class="sxs-lookup"><span data-stu-id="b2661-111">Supported Bindings</span></span>  
 <span data-ttu-id="b2661-112">Následující vazby WCF jsou podporovány v aplikacích pro Windows Store:</span><span class="sxs-lookup"><span data-stu-id="b2661-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="b2661-113">Následující prvky vazby jsou podporovány v aplikacích pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="b2661-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="b2661-114">Podporují se textové i binární kódování.</span><span class="sxs-lookup"><span data-stu-id="b2661-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="b2661-115">Podporují se všechny režimy přenosu WCF.</span><span class="sxs-lookup"><span data-stu-id="b2661-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="b2661-116">Další informace najdete v tématu [streamování přenosu zpráv](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="b2661-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="b2661-117">Přidání odkazu na službu</span><span class="sxs-lookup"><span data-stu-id="b2661-117">Add Service Reference</span></span>  
 <span data-ttu-id="b2661-118">Chcete-li volat službu WCF z aplikace pro Windows Store, použijte funkci Přidat odkaz na službu sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="b2661-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="b2661-119">V rámci aplikace pro Windows Store si všimnete několika změn ve funkcích Přidat odkaz na službu.</span><span class="sxs-lookup"><span data-stu-id="b2661-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="b2661-120">První konfigurační soubor není vygenerován.</span><span class="sxs-lookup"><span data-stu-id="b2661-120">First no configuration file is generated.</span></span> <span data-ttu-id="b2661-121">Aplikace pro Windows Store nepoužívají konfigurační soubory, takže je nutné je nakonfigurovat v kódu.</span><span class="sxs-lookup"><span data-stu-id="b2661-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="b2661-122">Tento konfigurační kód najdete v souboru References.cs generovaném pomocí Přidat odkaz na službu.</span><span class="sxs-lookup"><span data-stu-id="b2661-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="b2661-123">Tento soubor zobrazíte tak, že v Průzkumníku řešení vyberete možnost Zobrazit všechny soubory.</span><span class="sxs-lookup"><span data-stu-id="b2661-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="b2661-124">Soubor se nachází pod odkazy na služby a pak odkazuje na uzly. svcmap v rámci projektu.</span><span class="sxs-lookup"><span data-stu-id="b2661-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="b2661-125">Všechny operace generované pro služby WCF v rámci aplikace pro Windows Store budou asynchronní pomocí asynchronního vzoru založeného na úlohách.</span><span class="sxs-lookup"><span data-stu-id="b2661-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="b2661-126">Další informace najdete v tématu [asynchronní úlohy – zjednodušení asynchronního programování s úkoly](https://msdn.microsoft.com/magazine/ff959203.aspx).</span><span class="sxs-lookup"><span data-stu-id="b2661-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](https://msdn.microsoft.com/magazine/ff959203.aspx).</span></span>  
  
 <span data-ttu-id="b2661-127">Vzhledem k tomu, že konfigurace je nyní vygenerována v kódu, všechny změny provedené v souboru Reference.cs by byly přepsány při každé aktualizaci odkazu na službu.</span><span class="sxs-lookup"><span data-stu-id="b2661-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="b2661-128">Chcete-li tuto situaci napravit, je konfigurační kód generován v rámci částečné metody, kterou můžete implementovat do klientské proxy třídy.</span><span class="sxs-lookup"><span data-stu-id="b2661-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="b2661-129">Částečná metoda je deklarována takto:</span><span class="sxs-lookup"><span data-stu-id="b2661-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="b2661-130">Pak můžete implementovat tuto částečnou metodu a změnit vazbu nebo koncový bod ve vaší klientské proxy třídě následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b2661-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
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
  
### <a name="serialization"></a><span data-ttu-id="b2661-131">Serializace</span><span class="sxs-lookup"><span data-stu-id="b2661-131">Serialization</span></span>  
 <span data-ttu-id="b2661-132">Následující serializace jsou podporovány v aplikacích pro Windows Store:</span><span class="sxs-lookup"><span data-stu-id="b2661-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="b2661-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="b2661-133">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="b2661-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="b2661-134">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="b2661-135">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="b2661-135">XmlSerializer</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b2661-136">Implementace XmlDictionaryWriter. Write (DateTime) nyní zapisuje objekt DateTime jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="b2661-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="b2661-137">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b2661-137">Security</span></span>  

<span data-ttu-id="b2661-138">V aplikacích pro Windows Store jsou podporovány následující režimy zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="b2661-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="b2661-139">V aplikacích pro Windows Store jsou podporovány následující typy přihlašovacích údajů klienta:</span><span class="sxs-lookup"><span data-stu-id="b2661-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="b2661-140">Žádné</span><span class="sxs-lookup"><span data-stu-id="b2661-140">None</span></span>  
  
2. <span data-ttu-id="b2661-141">Základní</span><span class="sxs-lookup"><span data-stu-id="b2661-141">Basic</span></span>  
  
3. <span data-ttu-id="b2661-142">Otisk</span><span class="sxs-lookup"><span data-stu-id="b2661-142">Digest</span></span>  
  
4. <span data-ttu-id="b2661-143">Mluví</span><span class="sxs-lookup"><span data-stu-id="b2661-143">Negotiate</span></span>  
  
5. <span data-ttu-id="b2661-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="b2661-144">NTLM</span></span>  
  
6. <span data-ttu-id="b2661-145">Windows</span><span class="sxs-lookup"><span data-stu-id="b2661-145">Windows</span></span>  
  
7. <span data-ttu-id="b2661-146">Uživatelské jméno (zabezpečení zpráv)</span><span class="sxs-lookup"><span data-stu-id="b2661-146">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="b2661-147">Windows (zabezpečení přenosu)</span><span class="sxs-lookup"><span data-stu-id="b2661-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="b2661-148">Aby aplikace pro Windows Store měly přístup k výchozím přihlašovacím údajům systému Windows a odesílají je, musíte tuto funkci povolit v souboru Package. AppManifest.</span><span class="sxs-lookup"><span data-stu-id="b2661-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="b2661-149">Otevřete tento soubor a vyberte kartu Možnosti a vyberte možnost výchozí pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b2661-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="b2661-150">To umožňuje aplikaci připojovat se k prostředkům v intranetu, které vyžadují přihlašovací údaje domény.</span><span class="sxs-lookup"><span data-stu-id="b2661-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b2661-151">Aby se aplikace pro Windows Store daly uskutečnit mezi počítači, musíte povolit jinou funkci nazvanou "domácí/pracovní síť".</span><span class="sxs-lookup"><span data-stu-id="b2661-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="b2661-152">Toto nastavení je také v souboru Package. AppManifest na kartě Možnosti. Zaškrtněte políčko domů/pracovní sítě.</span><span class="sxs-lookup"><span data-stu-id="b2661-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="b2661-153">Tím zajistíte příchozí a odchozí přístup k sítím důvěryhodných míst uživatele, jako jsou doma a práce.</span><span class="sxs-lookup"><span data-stu-id="b2661-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="b2661-154">Příchozí kritické porty jsou vždycky blokované.</span><span class="sxs-lookup"><span data-stu-id="b2661-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="b2661-155">Pro přístup ke službám na internetu musíte povolit taky možnost Internet (klient).</span><span class="sxs-lookup"><span data-stu-id="b2661-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="b2661-156">Různé</span><span class="sxs-lookup"><span data-stu-id="b2661-156">Misc</span></span>  
 <span data-ttu-id="b2661-157">Pro aplikace pro Windows Store je podporováno použití následujících tříd:</span><span class="sxs-lookup"><span data-stu-id="b2661-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="b2661-158">Definování kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="b2661-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="b2661-159">Doporučujeme definovat pouze asynchronní operace služby pomocí asynchronního vzoru založeného na úlohách.</span><span class="sxs-lookup"><span data-stu-id="b2661-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="b2661-160">To zajistí, že aplikace pro Windows Store při volání operace služby budou reagovat.</span><span class="sxs-lookup"><span data-stu-id="b2661-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b2661-161">I když se nevyvolá žádná výjimka, pokud definujete synchronní operaci, důrazně doporučujeme definovat pouze asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="b2661-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="b2661-162">Volání služeb WCF z aplikací pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="b2661-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="b2661-163">Jak je uvedeno dříve, je nutné provést veškerou konfiguraci v kódu v metodě GetBindingForEndpoint ve vygenerované třídě proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="b2661-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="b2661-164">Volání operace služby je provedeno stejně jako volání jakékoli asynchronní metody založené na úlohách, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="b2661-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="b2661-165">Všimněte si použití klíčového slova Async v metodě umožňující asynchronní volání a klíčové slovo await při volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="b2661-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2661-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2661-166">See also</span></span>

- [<span data-ttu-id="b2661-167">Blog WCF v aplikacích pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="b2661-167">WCF in Windows Store Apps Blog</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)
- [<span data-ttu-id="b2661-168">Klienti a zabezpečení WCF Windows Store</span><span class="sxs-lookup"><span data-stu-id="b2661-168">WCF Windows Store Clients and Security</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)
- [<span data-ttu-id="b2661-169">Aplikace pro Windows Store a volání mezi počítači</span><span class="sxs-lookup"><span data-stu-id="b2661-169">Windows Store Apps and Cross Machine Calls</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [<span data-ttu-id="b2661-170">Volání služby WCF nasazené v Azure z aplikace pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="b2661-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [<span data-ttu-id="b2661-171">Programování zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="b2661-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [<span data-ttu-id="b2661-172">Vazby</span><span class="sxs-lookup"><span data-stu-id="b2661-172">Bindings</span></span>](../../../../docs/framework/wcf/bindings.md)
