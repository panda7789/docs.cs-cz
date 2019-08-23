---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: bcf1f1dcdba50c3e7fba8eb170132d0cf47c4271
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919818"
---
# <a name="behaviorextensions"></a><span data-ttu-id="63c89-101">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="63c89-101">\<behaviorExtensions></span></span>
<span data-ttu-id="63c89-102">Rozšíření chování umožňují uživateli vytvářet uživatelsky definované prvky chování.</span><span class="sxs-lookup"><span data-stu-id="63c89-102">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="63c89-103">Tyto prvky lze použít společně se standardními prvky chování Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="63c89-103">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="63c89-104">`behaviorExtensions` Oddíl definuje prvek tak, aby jej bylo možné použít v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="63c89-104">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="63c89-105">Tady je příklad typického rozšíření chování.</span><span class="sxs-lookup"><span data-stu-id="63c89-105">Here is an example of a typical behavior extension.</span></span>  
  
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
  
 <span data-ttu-id="63c89-106">Chcete-li přidat možnosti konfigurace elementu, je nutné zapsat a zaregistrovat prvek konfigurace.</span><span class="sxs-lookup"><span data-stu-id="63c89-106">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="63c89-107">Další informace najdete <xref:System.Configuration> v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="63c89-107">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="63c89-108">Po definování prvku a jeho typu konfigurace lze použít rozšíření, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="63c89-108">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
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
  
## <a name="security"></a><span data-ttu-id="63c89-109">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="63c89-109">Security</span></span>  
 <span data-ttu-id="63c89-110">Důrazně doporučujeme použít plně kvalifikované názvy sestavení při registraci typů v `machine.config` souborech a. `app.config`</span><span class="sxs-lookup"><span data-stu-id="63c89-110">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="63c89-111">Pokud typ není definován jednoznačně, vyhledá zavaděč typu CLR v následujících umístěních v zadaném pořadí:</span><span class="sxs-lookup"><span data-stu-id="63c89-111">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="63c89-112">Pokud je známo sestavení typu, zavaděč vyhledá umístění pro přesměrování konfiguračního souboru, GAC, aktuální sestavení s použitím informací o konfiguraci a základního adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="63c89-112">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="63c89-113">Pokud je sestavení neznámé, zavaděč vyhledá aktuální sestavení, mscorlib a umístění vrácené `TypeResolve` obslužnou rutinou události.</span><span class="sxs-lookup"><span data-stu-id="63c89-113">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="63c89-114">Toto pořadí vyhledávání CLR lze upravit pomocí háčků, jako je mechanismus předávání typů a událost AppDomain. TypeResolve.</span><span class="sxs-lookup"><span data-stu-id="63c89-114">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="63c89-115">Útočník může zneužít pořadí vyhledávání CLR a spustit neautorizovaný kód.</span><span class="sxs-lookup"><span data-stu-id="63c89-115">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="63c89-116">Použití plně kvalifikovaných (silných) názvů jednoznačně identifikuje typ a zvyšuje zabezpečení systému.</span><span class="sxs-lookup"><span data-stu-id="63c89-116">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="63c89-117">Další informace najdete v tématu [jak modul runtime vyhledává sestavení](https://go.microsoft.com/fwlink/?LinkId=95336) a <xref:System.AppDomain.TypeResolve>.</span><span class="sxs-lookup"><span data-stu-id="63c89-117">For more information, see [How the Runtime Locates Assemblies](https://go.microsoft.com/fwlink/?LinkId=95336) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c89-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63c89-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [<span data-ttu-id="63c89-119">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="63c89-119">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
