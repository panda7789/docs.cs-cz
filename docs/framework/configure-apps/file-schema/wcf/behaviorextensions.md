---
title: '&lt;behaviorExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c520a8a06a593d8937ca840602ba5bcc7b2d44b4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbehaviorextensionsgt"></a><span data-ttu-id="a3bd3-102">&lt;behaviorExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="a3bd3-102">&lt;behaviorExtensions&gt;</span></span>
<span data-ttu-id="a3bd3-103">Chování rozšíření zajistit, aby uživatel k vytváření prvků uživatelem definované chování.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-103">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="a3bd3-104">Tyto prvky můžete použít spolu s standardní elementy chování Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a3bd3-104">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="a3bd3-105">`behaviorExtensions` Oddíl definuje element tak, že můžete použít v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-105">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="a3bd3-106">Tady je příklad typické chování rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-106">Here is an example of a typical behavior extension.</span></span>  
  
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
  
 <span data-ttu-id="a3bd3-107">Přidat konfiguraci dalo k elementu, musíte k zápisu a zaregistrujte konfigurační prvek.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-107">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="a3bd3-108">Další informace najdete v tématu <xref:System.Configuration> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="a3bd3-109">Po elementu a jeho typ konfigurace jsou definovány, rozšíření můžete použít, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-109">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
```xml  
<behaviors>  
    <behavior configurationName="testChannelBehavior">  
        <myBehavior />  
        <channelSecurity cacheCookies="false" detectReplays="false" maxCachedNonces="9"  
            maxClockSkew="00:00:03" maxCookieCachingTime="00:07:24" replayWindow="00:07:22.2190000" />  
    </behavior>  
</behaviors>  
```  
  
## <a name="security"></a><span data-ttu-id="a3bd3-110">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a3bd3-110">Security</span></span>  
 <span data-ttu-id="a3bd3-111">Důrazně doporučujeme použít při registraci typy v sestavení plně kvalifikované názvy `machine.config` a `app.config` soubory.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-111">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="a3bd3-112">Pokud typ není definováno jednoznačně, vyhledá se zavaděč typ CLR pro něj v následujících umístěních v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="a3bd3-112">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="a3bd3-113">Pokud je znám sestavení typu zavaděč prohledá umístění konfiguračního souboru přesměrování, GAC, aktuální sestavení pomocí informace o konfiguraci a základní adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-113">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="a3bd3-114">Pokud sestavení neznámý, vyhledá zavaděč aktuální sestavení, mscorlib a umístění vrácený `TypeResolve` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-114">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="a3bd3-115">Toto pořadí hledání CLR může upravit s háky například mechanismus předávání typu a AppDomain.TypeResolve události.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-115">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="a3bd3-116">Útočník může zneužít pořadí hledání CLR a spustit neoprávněný kód.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-116">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="a3bd3-117">Pomocí plně kvalifikované názvy (silné) jednoznačně identifikuje typu a ještě zvyšuje zabezpečení vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-117">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="a3bd3-118">Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](http://go.microsoft.com/fwlink/?LinkId=95336) a <xref:System.AppDomain.TypeResolve>.</span><span class="sxs-lookup"><span data-stu-id="a3bd3-118">For more information, see [How the Runtime Locates Assemblies](http://go.microsoft.com/fwlink/?LinkId=95336) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3bd3-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3bd3-119">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>  
 [<span data-ttu-id="a3bd3-120">Konfigurace a rozšíření modulu Runtime s chováním</span><span class="sxs-lookup"><span data-stu-id="a3bd3-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
