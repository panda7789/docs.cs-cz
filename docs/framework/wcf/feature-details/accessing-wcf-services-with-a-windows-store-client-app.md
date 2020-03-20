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
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="c2cec-102">Přístup ke službám WCF pomocí klientské aplikace pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="c2cec-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="c2cec-103">Windows 8 zavádí nový typ aplikace s názvem Windows Store aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2cec-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="c2cec-104">Tyto aplikace jsou navrženy kolem rozhraní dotykové obrazovky.</span><span class="sxs-lookup"><span data-stu-id="c2cec-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="c2cec-105">Rozhraní .NET Framework 4.5 umožňuje aplikacím pro Windows Store volat služby WCF.</span><span class="sxs-lookup"><span data-stu-id="c2cec-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="c2cec-106">Podpora WCF v aplikacích pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="c2cec-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="c2cec-107">Podmnožina funkcí WCF je k dispozici v rámci aplikace pro Windows Store, další podrobnosti najdete v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="c2cec-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c2cec-108">Použijte winrt syndikace API namísto těch vystavených WCF.</span><span class="sxs-lookup"><span data-stu-id="c2cec-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="c2cec-109">Další informace naleznete v tématu [WinRT Syndication API](xref:Windows.Web.Syndication)</span><span class="sxs-lookup"><span data-stu-id="c2cec-109">For more information see, [WinRT Syndication API](xref:Windows.Web.Syndication)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="c2cec-110">Přidání odkazu na službu k přidání odkazu webové služby na součást prostředí Windows Runtime není podporováno.</span><span class="sxs-lookup"><span data-stu-id="c2cec-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="c2cec-111">Podporovaná vazby</span><span class="sxs-lookup"><span data-stu-id="c2cec-111">Supported Bindings</span></span>  
 <span data-ttu-id="c2cec-112">V aplikacích pro Windows Store jsou podporovány následující vazby WCF:</span><span class="sxs-lookup"><span data-stu-id="c2cec-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="c2cec-113">V aplikacích pro Windows Store jsou podporovány následující elementy vazby</span><span class="sxs-lookup"><span data-stu-id="c2cec-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="c2cec-114">Jsou podporovány kódování Text i Binární.</span><span class="sxs-lookup"><span data-stu-id="c2cec-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="c2cec-115">Všechny režimy přenosu WCF jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="c2cec-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="c2cec-116">Další informace naleznete v tématu [Streamování přenosu zpráv](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="c2cec-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="c2cec-117">Přidání odkazu na službu</span><span class="sxs-lookup"><span data-stu-id="c2cec-117">Add Service Reference</span></span>  
 <span data-ttu-id="c2cec-118">Chcete-li volat službu WCF z aplikace pro Windows Store, použijte funkci Přidat odkaz na službu v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="c2cec-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="c2cec-119">Pokud se provede v aplikaci pro Windows Store, všimnete si několika změn ve funkcích přidat odkaz na službu.</span><span class="sxs-lookup"><span data-stu-id="c2cec-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="c2cec-120">Nejprve není generován žádný konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="c2cec-120">First no configuration file is generated.</span></span> <span data-ttu-id="c2cec-121">Aplikace pro Windows Store nepoužívají konfigurační soubory, takže musí být nakonfigurovány v kódu.</span><span class="sxs-lookup"><span data-stu-id="c2cec-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="c2cec-122">Tento konfigurační kód naleznete v souboru References.cs generovaném nástrojem Přidat odkaz na službu.</span><span class="sxs-lookup"><span data-stu-id="c2cec-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="c2cec-123">Chcete-li zobrazit tento soubor, ujistěte se, že v průzkumníku řešení vyberete možnost Zobrazit všechny soubory.</span><span class="sxs-lookup"><span data-stu-id="c2cec-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="c2cec-124">Soubor bude umístěn pod odkazy na služby a potom Reference.svcmap uzly v rámci projektu.</span><span class="sxs-lookup"><span data-stu-id="c2cec-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="c2cec-125">Všechny operace generované pro služby WCF v rámci aplikace pro Windows Store budou asynchronní pomocí asynchronního vzoru založeného na úlohách.</span><span class="sxs-lookup"><span data-stu-id="c2cec-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="c2cec-126">Další informace naleznete [v tématu Asynchronní úlohy – zjednodušení asynchronního programování pomocí úloh](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span><span class="sxs-lookup"><span data-stu-id="c2cec-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span></span>  
  
 <span data-ttu-id="c2cec-127">Vzhledem k tomu, že konfigurace je nyní generována v kódu, všechny změny provedené v souboru Reference.cs by být přepsány při každé aktualizaci odkazu na službu.</span><span class="sxs-lookup"><span data-stu-id="c2cec-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="c2cec-128">K nápravě této situace je konfigurační kód generován v rámci částečné metody, kterou můžete implementovat ve třídě proxy klienta.</span><span class="sxs-lookup"><span data-stu-id="c2cec-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="c2cec-129">Částečná metoda se deklaruje takto:</span><span class="sxs-lookup"><span data-stu-id="c2cec-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="c2cec-130">Potom můžete implementovat tuto částečnou metodu a změnit vazbu nebo koncový bod ve třídě proxy klienta takto:</span><span class="sxs-lookup"><span data-stu-id="c2cec-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
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
  
### <a name="serialization"></a><span data-ttu-id="c2cec-131">Serializace</span><span class="sxs-lookup"><span data-stu-id="c2cec-131">Serialization</span></span>  
 <span data-ttu-id="c2cec-132">V aplikacích pro Windows Store jsou podporovány následující serializátory:</span><span class="sxs-lookup"><span data-stu-id="c2cec-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="c2cec-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="c2cec-133">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="c2cec-134">Datacontractjsonserializer</span><span class="sxs-lookup"><span data-stu-id="c2cec-134">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="c2cec-135">Xmlserializer</span><span class="sxs-lookup"><span data-stu-id="c2cec-135">XmlSerializer</span></span>  
  
> [!WARNING]
> <span data-ttu-id="c2cec-136">XmlDictionaryWriter.Write(DateTime) nyní zapíše objekt DateTime jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="c2cec-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="c2cec-137">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c2cec-137">Security</span></span>  

<span data-ttu-id="c2cec-138">V aplikacích pro Windows Store jsou podporovány následující režimy zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="c2cec-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="c2cec-139">V aplikacích pro Windows Store jsou podporovány následující typy pověření klienta:</span><span class="sxs-lookup"><span data-stu-id="c2cec-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="c2cec-140">Žádný</span><span class="sxs-lookup"><span data-stu-id="c2cec-140">None</span></span>  
  
2. <span data-ttu-id="c2cec-141">Basic</span><span class="sxs-lookup"><span data-stu-id="c2cec-141">Basic</span></span>  
  
3. <span data-ttu-id="c2cec-142">Digest</span><span class="sxs-lookup"><span data-stu-id="c2cec-142">Digest</span></span>  
  
4. <span data-ttu-id="c2cec-143">Negotiate</span><span class="sxs-lookup"><span data-stu-id="c2cec-143">Negotiate</span></span>  
  
5. <span data-ttu-id="c2cec-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="c2cec-144">NTLM</span></span>  
  
6. <span data-ttu-id="c2cec-145">Windows</span><span class="sxs-lookup"><span data-stu-id="c2cec-145">Windows</span></span>  
  
7. <span data-ttu-id="c2cec-146">Uživatelské jméno (Zabezpečení zpráv)</span><span class="sxs-lookup"><span data-stu-id="c2cec-146">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="c2cec-147">Windows (zabezpečení přenosu)</span><span class="sxs-lookup"><span data-stu-id="c2cec-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="c2cec-148">Aby aplikace pro Windows Store mohly přistupovat k výchozím přihlašovacím údajům systému Windows a odesílat je, musíte tuto funkci povolit v souboru Package.appmanifest.</span><span class="sxs-lookup"><span data-stu-id="c2cec-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="c2cec-149">Otevřete tento soubor a vyberte kartu Možnosti a vyberte "Výchozí pověření systému Windows".</span><span class="sxs-lookup"><span data-stu-id="c2cec-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="c2cec-150">To umožňuje aplikaci připojit se k prostředkům intranetu, které vyžadují pověření domény.</span><span class="sxs-lookup"><span data-stu-id="c2cec-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c2cec-151">Aby aplikace pro Windows Store mohly volat mezi počítači, musíte povolit další funkci nazvanou "Domácí/pracovní síť".</span><span class="sxs-lookup"><span data-stu-id="c2cec-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="c2cec-152">Toto nastavení je také v souboru Package.appmanifest na kartě Možnosti.</span><span class="sxs-lookup"><span data-stu-id="c2cec-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="c2cec-153">To poskytuje aplikaci příchozí a odchozí přístup k sítím důvěryhodných míst uživatele, jako je domov a práce.</span><span class="sxs-lookup"><span data-stu-id="c2cec-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="c2cec-154">Příchozí kritické porty jsou vždy blokovány.</span><span class="sxs-lookup"><span data-stu-id="c2cec-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="c2cec-155">Pro přístup ke službám na Internetu musíte také povolit možnost i pro připojení k Internetu (Client).</span><span class="sxs-lookup"><span data-stu-id="c2cec-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="c2cec-156">Různé</span><span class="sxs-lookup"><span data-stu-id="c2cec-156">Misc</span></span>  
 <span data-ttu-id="c2cec-157">Pro aplikace pro Windows Store je podporováno použití následujících tříd:</span><span class="sxs-lookup"><span data-stu-id="c2cec-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="c2cec-158">Definování servisních smluv</span><span class="sxs-lookup"><span data-stu-id="c2cec-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="c2cec-159">Doporučujeme pouze definování asynchronních operací služby pomocí asynchronního vzoru založeného na úlohách.</span><span class="sxs-lookup"><span data-stu-id="c2cec-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="c2cec-160">Tím zajistíte, že aplikace pro Windows Store zůstanou responzivní při volání operace služby.</span><span class="sxs-lookup"><span data-stu-id="c2cec-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="c2cec-161">Zatímco žádná výjimka bude vyvolána, pokud definujete synchronní operaci, důrazně doporučujeme definovat pouze asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="c2cec-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="c2cec-162">Volání služeb WCF z aplikací pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="c2cec-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="c2cec-163">Jak již bylo zmíněno dříve všechny konfigurace musí být provedeno v kódu v GetBindingForEndpoint metoda v generované proxy třídy.</span><span class="sxs-lookup"><span data-stu-id="c2cec-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="c2cec-164">Volání operace služby se provádí stejně jako volání jakékoli asynchronní metody založené na úlohách, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="c2cec-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="c2cec-165">Všimněte si použití asynchronní ho klíčovéslovo na metodu, která asynchronní volání a await klíčové slovo při volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="c2cec-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2cec-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2cec-166">See also</span></span>

- [<span data-ttu-id="c2cec-167">WCF v blogu o aplikacích pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="c2cec-167">WCF in Windows Store Apps Blog</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/wcf-in-windows-8-metro-styled-apps-absolutely-supported)
- [<span data-ttu-id="c2cec-168">Klienti a zabezpečení wCF Windows Store</span><span class="sxs-lookup"><span data-stu-id="c2cec-168">WCF Windows Store Clients and Security</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-adding-security)
- [<span data-ttu-id="c2cec-169">Aplikace pro Windows Store a volání napříč počítači</span><span class="sxs-lookup"><span data-stu-id="c2cec-169">Windows Store Apps and Cross Machine Calls</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="c2cec-170">Volání služby WCF nasazené v Azure z aplikace pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="c2cec-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="c2cec-171">Programování zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="c2cec-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [<span data-ttu-id="c2cec-172">Vazby</span><span class="sxs-lookup"><span data-stu-id="c2cec-172">Bindings</span></span>](../../../../docs/framework/wcf/bindings.md)
