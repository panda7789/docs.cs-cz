---
title: Používání více schémat ověřování u WCF
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: 9f2c9944b424ba527fb20562706d5ad7fc3f8359
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465487"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="d306e-102">Používání více schémat ověřování u WCF</span><span class="sxs-lookup"><span data-stu-id="d306e-102">Using Multiple Authentication Schemes with WCF</span></span>
<span data-ttu-id="d306e-103">WCF umožňuje zadat více schémat ověřování v jednom koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="d306e-103">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="d306e-104">Kromě toho hostovaná na webu služby může dědit jejich nastavení ověřování přímo ze služby IIS.</span><span class="sxs-lookup"><span data-stu-id="d306e-104">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="d306e-105">V místním prostředí služby můžete zadat ověření je možné schémata.</span><span class="sxs-lookup"><span data-stu-id="d306e-105">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="d306e-106">Další informace o nastavení ověřování ve službě IIS najdete v tématu [ověřování služby IIS](https://go.microsoft.com/fwlink/?LinkId=232458)</span><span class="sxs-lookup"><span data-stu-id="d306e-106">For more information about setting authentication settings in IIS, see [IIS Authentication](https://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="d306e-107">IIS-Hosted Services</span><span class="sxs-lookup"><span data-stu-id="d306e-107">IIS-Hosted Services</span></span>  
 <span data-ttu-id="d306e-108">Služby hostované v IIS nastavte ověřovací schémata, které chcete použít ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="d306e-108">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="d306e-109">V souboru web.config vaší služby v konfiguraci vazby zadejte typ clientcredential systému jako "InheritedFromHost" jak je znázorněno v následující fragment kódu XML:</span><span class="sxs-lookup"><span data-stu-id="d306e-109">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="d306e-110">Můžete určit, že chcete pouze podmnožinu schémata ověřování, který se má použít ve vaší službě pomocí ServiceAuthenticationBehavior nebo \<serviceAuthenticationManager > element.</span><span class="sxs-lookup"><span data-stu-id="d306e-110">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="d306e-111">Když tato konfigurace v kódu pomocí ServiceAuthenticationBehavior, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="d306e-111">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="d306e-112">Při konfiguraci v konfiguračním souboru, použijte \<serviceAuthenticationManager > jak ukazuje následující fragment kódu XML.</span><span class="sxs-lookup"><span data-stu-id="d306e-112">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="d306e-113">Tím se zajistí, že pouze podmnožinu ověřovací schémata tady se budou považovat za pro použití u koncového bodu služby v závislosti na tom, co je vybrané v IIS.</span><span class="sxs-lookup"><span data-stu-id="d306e-113">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="d306e-114">To znamená, že, které se můžete vyloučit vývojář Řekněme, že základní ověřování ze seznamu vynecháním v třídě serviceAuthenticationManager výpisu a i když je povolená ve službě IIS, nebude použita na koncový bod služby</span><span class="sxs-lookup"><span data-stu-id="d306e-114">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="d306e-115">V místním prostředí služby</span><span class="sxs-lookup"><span data-stu-id="d306e-115">Self-Hosted Services</span></span>  
 <span data-ttu-id="d306e-116">V místním prostředí služby se konfigurují trochu jinak, protože neexistuje žádná služba IIS dědit nastavení z.</span><span class="sxs-lookup"><span data-stu-id="d306e-116">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="d306e-117">Zde použijete \<serviceAuthenticationManager > element nebo ServiceAuthenticationBehavior k určení, které se budou dědit nastavení ověřování.</span><span class="sxs-lookup"><span data-stu-id="d306e-117">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="d306e-118">V kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="d306e-118">In code it looks like this:</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="d306e-119">V konfiguraci vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="d306e-119">In config, it looks like this:</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="d306e-120">A můžete pak určit InheritFromHost v nastaveních vazbu, jak je znázorněno v následující fragment kódu XML.</span><span class="sxs-lookup"><span data-stu-id="d306e-120">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="d306e-121">Alternativně můžete zadat ověřovací schémata v vlastní vazby, nastavením schémat ověřování v HTTP přenosu element vazby, jak je znázorněno v následujícím fragmentu kódu config.</span><span class="sxs-lookup"><span data-stu-id="d306e-121">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d306e-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d306e-122">See also</span></span>
- [<span data-ttu-id="d306e-123">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d306e-123">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [<span data-ttu-id="d306e-124">Koncové body: Adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="d306e-124">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="d306e-125">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="d306e-125">Configuring System-Provided Bindings</span></span>](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d306e-126">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="d306e-126">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="d306e-127">Vazby</span><span class="sxs-lookup"><span data-stu-id="d306e-127">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)
- [<span data-ttu-id="d306e-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d306e-128">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)
