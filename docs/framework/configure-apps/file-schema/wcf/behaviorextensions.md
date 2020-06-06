---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: 39dc92d65a41d223ebd39aec3dc59871ad1fd101
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77448682"
---
# \<behaviorExtensions>
<span data-ttu-id="b65f3-101">Rozšíření chování umožňují uživateli vytvářet uživatelsky definované prvky chování.</span><span class="sxs-lookup"><span data-stu-id="b65f3-101">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="b65f3-102">Tyto prvky lze použít společně se standardními prvky chování Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b65f3-102">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="b65f3-103">`behaviorExtensions`Oddíl definuje prvek tak, aby jej bylo možné použít v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="b65f3-103">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="b65f3-104">Tady je příklad typického rozšíření chování.</span><span class="sxs-lookup"><span data-stu-id="b65f3-104">Here is an example of a typical behavior extension.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <behaviorExtensions>
      <add name="myBehavior"
           type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </behaviorExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="b65f3-105">Chcete-li přidat možnosti konfigurace elementu, je nutné zapsat a zaregistrovat prvek konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b65f3-105">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="b65f3-106">Další informace najdete v <xref:System.Configuration> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="b65f3-106">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="b65f3-107">Po definování prvku a jeho typu konfigurace lze použít rozšíření, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b65f3-107">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
```xml  
<behaviors>
  <behavior configurationName="testChannelBehavior">
    <myBehavior />
    <channelSecurity cacheCookies="false"
                     detectReplays="false"
                     maxCachedNonces="9"
                     maxClockSkew="00:00:03"
                     maxCookieCachingTime="00:07:24"
                     replayWindow="00:07:22.2190000" />
  </behavior>
</behaviors>
```  
  
## <a name="security"></a><span data-ttu-id="b65f3-108">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b65f3-108">Security</span></span>  
 <span data-ttu-id="b65f3-109">Důrazně doporučujeme použít plně kvalifikované názvy sestavení při registraci typů v `machine.config` `app.config` souborech a.</span><span class="sxs-lookup"><span data-stu-id="b65f3-109">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="b65f3-110">Pokud typ není definován jednoznačně, vyhledá zavaděč typu CLR v následujících umístěních v zadaném pořadí:</span><span class="sxs-lookup"><span data-stu-id="b65f3-110">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="b65f3-111">Pokud je známo sestavení typu, zavaděč vyhledá umístění pro přesměrování konfiguračního souboru, GAC, aktuální sestavení s použitím informací o konfiguraci a základního adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="b65f3-111">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="b65f3-112">Pokud je sestavení neznámé, zavaděč vyhledá aktuální sestavení, mscorlib a umístění vrácené `TypeResolve` obslužnou rutinou události.</span><span class="sxs-lookup"><span data-stu-id="b65f3-112">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="b65f3-113">Toto pořadí vyhledávání CLR lze upravit pomocí háčků, jako je mechanismus předávání typů a událost AppDomain. TypeResolve.</span><span class="sxs-lookup"><span data-stu-id="b65f3-113">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="b65f3-114">Útočník může zneužít pořadí vyhledávání CLR a spustit neautorizovaný kód.</span><span class="sxs-lookup"><span data-stu-id="b65f3-114">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="b65f3-115">Použití plně kvalifikovaných (silných) názvů jednoznačně identifikuje typ a zvyšuje zabezpečení systému.</span><span class="sxs-lookup"><span data-stu-id="b65f3-115">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="b65f3-116">Další informace najdete v tématu [jak modul runtime vyhledává sestavení](../../../deployment/how-the-runtime-locates-assemblies.md) a <xref:System.AppDomain.TypeResolve> .</span><span class="sxs-lookup"><span data-stu-id="b65f3-116">For more information, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b65f3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b65f3-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [<span data-ttu-id="b65f3-118">Konfigurace a rozšíření modulu runtime s chováním</span><span class="sxs-lookup"><span data-stu-id="b65f3-118">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
