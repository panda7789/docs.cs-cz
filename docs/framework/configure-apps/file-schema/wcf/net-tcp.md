---
title: '&lt;net.tcp&gt;'
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 9e44ddcc3a3e983abe6e36d4b6095c5c4a67529f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349880"
---
# <a name="ltnettcpgt"></a><span data-ttu-id="42449-102">&lt;net.tcp&gt;</span><span class="sxs-lookup"><span data-stu-id="42449-102">&lt;net.tcp&gt;</span></span>
<span data-ttu-id="42449-103">Určuje nastavení konfigurace sítě. TCP Port sdílení služby, která umožňuje více procesů sdílet stejný port TCP.</span><span class="sxs-lookup"><span data-stu-id="42449-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="42449-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="42449-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="42449-105">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="42449-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42449-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42449-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="Integer"  
          maxPendingAccepts="Integer"  
          maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan"  
          teredoEnabled="Boolean">  
          <allowAccounts>  
             <!-- LocalSystem account -->   
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->   
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->   
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->   
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only)-->   
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="42449-107">Typ</span><span class="sxs-lookup"><span data-stu-id="42449-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42449-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="42449-108">Attributes and Elements</span></span>  
 <span data-ttu-id="42449-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="42449-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42449-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="42449-110">Attributes</span></span>  
  
|<span data-ttu-id="42449-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="42449-111">Attribute</span></span>|<span data-ttu-id="42449-112">Popis</span><span class="sxs-lookup"><span data-stu-id="42449-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="42449-113">Celé číslo, které určuje maximální počet nezpracovaných připojení, které přijímají sdíleného připojení, ale nejsou ještě odeslaných do služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="42449-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="42449-114">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="42449-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="42449-115">Celé číslo, které určuje maximální počet nezpracovaných souběžných přijímá vláken pro naslouchání koncový bod pro službu sdílení.</span><span class="sxs-lookup"><span data-stu-id="42449-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="42449-116">Výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="42449-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="42449-117">Maximální počet připojení, která naslouchací proces může mít čeká se na aplikace akceptovat.</span><span class="sxs-lookup"><span data-stu-id="42449-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="42449-118">Při překročení této hodnoty kvóty na nový příchozí připojení zahozených místo čekání na přijmout.</span><span class="sxs-lookup"><span data-stu-id="42449-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="42449-119">Funkce připojení jako zabezpečení zpráv může způsobit klienta otevřít víc než jedno připojení.</span><span class="sxs-lookup"><span data-stu-id="42449-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="42449-120">Správci služeb by měl účet pro tyto další připojení při nastavování této hodnoty kvóty.</span><span class="sxs-lookup"><span data-stu-id="42449-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="42449-121">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="42449-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="42449-122">A `TimeSpan` který určuje časový limit pro čtení dat rámcovacích a provádění připojení odeslání od připojení podtržení.</span><span class="sxs-lookup"><span data-stu-id="42449-122">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="42449-123">Výchozí hodnota je "00: 00:10".</span><span class="sxs-lookup"><span data-stu-id="42449-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="42449-124">Logická hodnota, která označuje, zda služby Sdílení portů používá službu Microsoft Teredo tak, aby naslouchala na portech TCP jménem služby WCF.</span><span class="sxs-lookup"><span data-stu-id="42449-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="42449-125">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="42449-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42449-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="42449-126">Child Elements</span></span>  
  
|<span data-ttu-id="42449-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="42449-127">Element</span></span>|<span data-ttu-id="42449-128">Popis</span><span class="sxs-lookup"><span data-stu-id="42449-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42449-129">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="42449-129">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="42449-130">Kolekci elementů konfigurace, které obsahují `securityIdentifier` atribut zadejte uživatelské účty pro procesy, které hostování služby WCF a je uděleno oprávnění k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="42449-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="42449-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="42449-131">Parent Elements</span></span>  
  
|<span data-ttu-id="42449-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="42449-132">Element</span></span>|<span data-ttu-id="42449-133">Popis</span><span class="sxs-lookup"><span data-stu-id="42449-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42449-134">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="42449-134">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="42449-135">Obsahuje nastavení konfigurace pro proces naslouchání SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="42449-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42449-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42449-136">Remarks</span></span>  
 <span data-ttu-id="42449-137">Další informace o sdílení portů najdete v tématu [sdílení portů Net.TCP](http://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded).</span><span class="sxs-lookup"><span data-stu-id="42449-137">For more information on port sharing, see [Net.TCP Port Sharing](http://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded).</span></span> <span data-ttu-id="42449-138">Chcete-li pochopit, jak nakonfigurovat služby Sdílení portů, přečtěte si téma [konfigurace služby Sdílení portů Net.TCP](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span><span class="sxs-lookup"><span data-stu-id="42449-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42449-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="42449-139">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [<span data-ttu-id="42449-140">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="42449-140">Net.TCP Port Sharing</span></span>](http://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded)  
 [<span data-ttu-id="42449-141">Konfigurace služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="42449-141">Configuring the Net.TCP Port Sharing Service</span></span>](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)
