---
title: '&lt;allowAccounts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20d411fbe052940fd8fc752e74d012f28ffa441b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="6c679-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="6c679-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="6c679-103">Obsahuje kolekci elementů konfigurace, které určují uživatelských účtů pro procesy, které hostují [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby a je uděleno oprávnění k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="6c679-103">Contains a collection of configuration elements that specify user accounts for processes that host [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="6c679-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="6c679-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c679-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c679-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c679-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6c679-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6c679-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6c679-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c679-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="6c679-108">Attributes</span></span>  
 <span data-ttu-id="6c679-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="6c679-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6c679-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6c679-110">Child Elements</span></span>  
  
|<span data-ttu-id="6c679-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="6c679-111">Attribute</span></span>|<span data-ttu-id="6c679-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6c679-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="6c679-113">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="6c679-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="6c679-114">Přidá uživatelský účet pro procesy na tomto hostiteli [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a je uděleno oprávnění k připojení ke službě Sdílení</span><span class="sxs-lookup"><span data-stu-id="6c679-114">Adds a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c679-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6c679-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6c679-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="6c679-116">Element</span></span>|<span data-ttu-id="6c679-117">Popis</span><span class="sxs-lookup"><span data-stu-id="6c679-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c679-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) nebo [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="6c679-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="6c679-119">Určuje nastavení konfigurace pro Net kanálu nebo TCP služby sdílení.</span><span class="sxs-lookup"><span data-stu-id="6c679-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c679-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c679-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
