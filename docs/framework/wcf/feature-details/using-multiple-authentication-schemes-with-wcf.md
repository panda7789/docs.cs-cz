---
title: Používání více schémat ověřování u WCF
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: 1874963573a6ec12939bd12b79574f1e2c889bfd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600215"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="e73ea-102">Používání více schémat ověřování u WCF</span><span class="sxs-lookup"><span data-stu-id="e73ea-102">Using Multiple Authentication Schemes with WCF</span></span>
<span data-ttu-id="e73ea-103">WCF teď umožňuje zadat pro jeden koncový bod několik schémat ověřování.</span><span class="sxs-lookup"><span data-stu-id="e73ea-103">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="e73ea-104">Webové hostované služby navíc můžou dědit nastavení ověřování přímo ze služby IIS.</span><span class="sxs-lookup"><span data-stu-id="e73ea-104">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="e73ea-105">Služby v místním prostředí můžou určovat, která schémata ověřování se dají použít.</span><span class="sxs-lookup"><span data-stu-id="e73ea-105">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="e73ea-106">Další informace o nastavení ověřování ve službě IIS najdete v tématu [ověřování služby IIS](https://go.microsoft.com/fwlink/?LinkId=232458) .</span><span class="sxs-lookup"><span data-stu-id="e73ea-106">For more information about setting authentication settings in IIS, see [IIS Authentication](https://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="e73ea-107">Služby hostované službou IIS</span><span class="sxs-lookup"><span data-stu-id="e73ea-107">IIS-Hosted Services</span></span>  
 <span data-ttu-id="e73ea-108">Pro služby hostované službou IIS nastavte schémata ověřování, která chcete používat ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="e73ea-108">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="e73ea-109">Potom v souboru Web. config vaší služby v konfiguraci vazby zadejte typ clientCredential jako "InheritedFromHost", jak je znázorněno v následujícím fragmentu kódu XML:</span><span class="sxs-lookup"><span data-stu-id="e73ea-109">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
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
  
 <span data-ttu-id="e73ea-110">Můžete určit, že chcete použít jenom podmnožinu ověřovacích schémat s vaší službou pomocí ServiceAuthenticationBehavior nebo \<serviceAuthenticationManager> elementu.</span><span class="sxs-lookup"><span data-stu-id="e73ea-110">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="e73ea-111">Při konfiguraci tohoto v kódu použijte ServiceAuthenticationBehavior, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="e73ea-111">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="e73ea-112">Při konfiguraci v konfiguračním souboru použijte \<serviceAuthenticationManager> prvek, jak je znázorněno v následujícím fragmentu kódu XML.</span><span class="sxs-lookup"><span data-stu-id="e73ea-112">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="e73ea-113">Tím se zajistí, že se na koncový bod služby považuje jenom podmnožina schémat ověřování, v závislosti na tom, co je ve službě IIS vybrané.</span><span class="sxs-lookup"><span data-stu-id="e73ea-113">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="e73ea-114">To znamená, že vývojář může ze seznamu vyloučit základní ověřování vyřazením ze seznamu serviceAuthenticationManager a dokonce i v případě, že je povolený ve službě IIS, nebude ho použít na koncovém bodu služby.</span><span class="sxs-lookup"><span data-stu-id="e73ea-114">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="e73ea-115">Samoobslužné služby</span><span class="sxs-lookup"><span data-stu-id="e73ea-115">Self-Hosted Services</span></span>  
 <span data-ttu-id="e73ea-116">Samoobslužné služby jsou nakonfigurovány trochu odlišně, protože neexistují žádné služby IIS, ze kterých by bylo možné dědit nastavení.</span><span class="sxs-lookup"><span data-stu-id="e73ea-116">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="e73ea-117">V tomto případě použijete \<serviceAuthenticationManager> prvek nebo ServiceAuthenticationBehavior k určení nastavení ověřování, které bude děděno.</span><span class="sxs-lookup"><span data-stu-id="e73ea-117">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="e73ea-118">V kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="e73ea-118">In code it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="e73ea-119">V konfiguraci vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="e73ea-119">In config, it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="e73ea-120">A pak můžete zadat InheritFromHost v nastaveních vazby, jak je znázorněno v následujícím fragmentu kódu XML.</span><span class="sxs-lookup"><span data-stu-id="e73ea-120">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="e73ea-121">Alternativně můžete určit schémata ověřování ve vlastní vazbě nastavením schémat ověřování na elementu vazby přenosu HTTP, jak je znázorněno v následujícím fragmentu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e73ea-121">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e73ea-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e73ea-122">See also</span></span>

- [<span data-ttu-id="e73ea-123">Vazby a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e73ea-123">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="e73ea-124">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="e73ea-124">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="e73ea-125">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="e73ea-125">Configuring System-Provided Bindings</span></span>](configuring-system-provided-bindings.md)
- [<span data-ttu-id="e73ea-126">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="e73ea-126">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="e73ea-127">Vazby</span><span class="sxs-lookup"><span data-stu-id="e73ea-127">Bindings</span></span>](bindings.md)
- [<span data-ttu-id="e73ea-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="e73ea-128">Custom Bindings</span></span>](../extending/custom-bindings.md)
