---
title: '&lt;behaviorExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: d025497956715913923e839cb6c482f44f96babb
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078666"
---
# <a name="ltbehaviorextensionsgt"></a><span data-ttu-id="1e1c1-102">&lt;behaviorExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="1e1c1-102">&lt;behaviorExtensions&gt;</span></span>
<span data-ttu-id="1e1c1-103">Rozšíření chování povolují uživateli vytvořit uživatelem definované chování elementů.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-103">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="1e1c1-104">Tyto prvky lze použít společně s standardní prvky chování Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1e1c1-104">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="1e1c1-105">`behaviorExtensions` Oddíl definuje element tak, že je možné v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-105">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="1e1c1-106">Tady je příklad obvyklé chování rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-106">Here is an example of a typical behavior extension.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="myBehavior" type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
       </behaviorExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="1e1c1-107">Chcete-li přidat možnosti konfigurace na prvek, budete muset zápisu a registrace konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-107">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="1e1c1-108">Další informace najdete v článku <xref:System.Configuration> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="1e1c1-109">Po definování elementu a jeho typ konfigurace rozšíření je možné, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-109">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
```xml  
<behaviors>  
    <behavior configurationName="testChannelBehavior">  
        <myBehavior />  
        <channelSecurity cacheCookies="false" detectReplays="false" maxCachedNonces="9"  
            maxClockSkew="00:00:03" maxCookieCachingTime="00:07:24" replayWindow="00:07:22.2190000" />  
    </behavior>  
</behaviors>  
```  
  
## <a name="security"></a><span data-ttu-id="1e1c1-110">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1e1c1-110">Security</span></span>  
 <span data-ttu-id="1e1c1-111">Důrazně doporučujeme použít plně kvalifikované názvy sestavení při registraci typů v `machine.config` a `app.config` soubory.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-111">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="1e1c1-112">Pokud typ není jednoznačně definována, zavaděč modulu CLR typu prohledá v následujících umístěních v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="1e1c1-112">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="1e1c1-113">Pokud je sestavení typu je známo, prohledá zavaděč konfiguračního souboru přesměrování umístění mezipaměti GAC, aktuální sestavení s využitím informací o konfiguraci a základní adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-113">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="1e1c1-114">Pokud sestavení není znám, vyhledá zavaděč aktuální sestavení mscorlib a umístění vrácené `TypeResolve` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-114">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="1e1c1-115">Toto pořadí hledání CLR se dají upravovat pomocí háky například mechanismus předávání typu a AppDomain.TypeResolve událostí.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-115">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="1e1c1-116">Útočník může zneužít pořadí hledání modulu CLR a spustit neoprávněný kód.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-116">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="1e1c1-117">Pomocí plně kvalifikované názvy (silnou) jednoznačně identifikuje typ a ještě zvyšuje zabezpečení vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-117">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="1e1c1-118">Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](https://go.microsoft.com/fwlink/?LinkId=95336) a <xref:System.AppDomain.TypeResolve>.</span><span class="sxs-lookup"><span data-stu-id="1e1c1-118">For more information, see [How the Runtime Locates Assemblies](https://go.microsoft.com/fwlink/?LinkId=95336) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e1c1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e1c1-119">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>  
 [<span data-ttu-id="1e1c1-120">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="1e1c1-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
