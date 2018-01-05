---
title: "Používání více schémat ověřování u WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e570185b7df06a47e8c7fb3319328e760079415d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="023b3-102">Používání více schémat ověřování u WCF</span><span class="sxs-lookup"><span data-stu-id="023b3-102">Using Multiple Authentication Schemes with WCF</span></span>
<span data-ttu-id="023b3-103">WCF teď umožňuje zadat více schémat ověřování v jednom koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="023b3-103">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="023b3-104">Kromě toho hostovaná na webu služby může dědit vlastnosti jejich nastavení ověřování přímo ze služby IIS.</span><span class="sxs-lookup"><span data-stu-id="023b3-104">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="023b3-105">Samoobslužné hostované služby můžete určit, jaké ověřování můžete použít schémata.</span><span class="sxs-lookup"><span data-stu-id="023b3-105">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="023b3-106">Další informace o nastavení ověřování ve službě IIS najdete v tématu [ověřování služby IIS](http://go.microsoft.com/fwlink/?LinkId=232458)</span><span class="sxs-lookup"><span data-stu-id="023b3-106">For more information about setting authentication settings in IIS, see [IIS Authentication](http://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="023b3-107">Služba IIS hostované služby</span><span class="sxs-lookup"><span data-stu-id="023b3-107">IIS-Hosted Services</span></span>  
 <span data-ttu-id="023b3-108">Pro službu IIS hostované služby nastavte schémat ověřování, který si přejete použít ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="023b3-108">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="023b3-109">V souboru web.config vaší služby, v konfiguraci vazby zadejte typ clientCredential jako "InheritedFromHost" jak je znázorněno v následujícím fragmentu kódu XML:</span><span class="sxs-lookup"><span data-stu-id="023b3-109">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
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
  
 <span data-ttu-id="023b3-110">Můžete zadat, že chcete pouze podmnožinu schémat ověřování pro použití s služby pomocí ServiceAuthenticationBehavior nebo \<serviceAuthenticationManager > elementu.</span><span class="sxs-lookup"><span data-stu-id="023b3-110">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="023b3-111">Když tato konfigurace v kódu pomocí ServiceAuthenticationBehavior, jak je znázorněno v následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="023b3-111">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="023b3-112">Při konfiguraci v konfiguračním souboru, použijte \<serviceAuthenticationManager > elementu, jak je znázorněno v následujícím fragmentu kódu XML.</span><span class="sxs-lookup"><span data-stu-id="023b3-112">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="023b3-113">Tím bude zajištěno, že budou považovány za jenom podmnožinu schémat ověřování, které jsou zde uvedeny pro použití na koncový bod služby, v závislosti na tom, co je vybrané v IIS.</span><span class="sxs-lookup"><span data-stu-id="023b3-113">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="023b3-114">To znamená, které můžete vyloučit vývojář vyslovení základní ověřování ze seznamu vynecháním ze seznamu serviceAuthenticationManager a i v případě, že je povolena ve službě IIS, nebudou použity na koncový bod služby</span><span class="sxs-lookup"><span data-stu-id="023b3-114">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="023b3-115">Samoobslužné hostované služby</span><span class="sxs-lookup"><span data-stu-id="023b3-115">Self-Hosted Services</span></span>  
 <span data-ttu-id="023b3-116">Vlastním hostováním služby jsou nakonfigurovány trochu jinak, protože neexistuje žádné služby IIS pro dědění nastavení z.</span><span class="sxs-lookup"><span data-stu-id="023b3-116">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="023b3-117">Tady můžete použít \<serviceAuthenticationManager > elementu nebo ServiceAuthenticationBehavior a zadejte nastavení ověřování, které zdědí.</span><span class="sxs-lookup"><span data-stu-id="023b3-117">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="023b3-118">V kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="023b3-118">In code it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="023b3-119">V konfiguraci vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="023b3-119">In config, it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="023b3-120">A můžete pak určit InheritFromHost v nastaveních vazby, jak je znázorněno v následujícím fragmentu kódu XML.</span><span class="sxs-lookup"><span data-stu-id="023b3-120">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="023b3-121">Alternativně můžete zadat schémat ověřování v vlastní vazby, nastavením schémat ověřování v HTTP přenosu prvku vazby, jak je znázorněno v následujícím fragmentu kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="023b3-121">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="023b3-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="023b3-122">See Also</span></span>  
 [<span data-ttu-id="023b3-123">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="023b3-123">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="023b3-124">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="023b3-124">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="023b3-125">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="023b3-125">Configuring System-Provided Bindings</span></span>](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="023b3-126">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="023b3-126">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="023b3-127">Vazby</span><span class="sxs-lookup"><span data-stu-id="023b3-127">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="023b3-128">Vazby</span><span class="sxs-lookup"><span data-stu-id="023b3-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="023b3-129">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="023b3-129">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)
