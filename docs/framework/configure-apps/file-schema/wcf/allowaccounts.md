---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 097112a8b54467843554047882e55b62d7813c0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352874"
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="b0c24-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="b0c24-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="b0c24-103">Obsahuje kolekci elementů konfigurace, které určují uživatelské účty pro procesy na tomto hostiteli služby Windows Communication Foundation (WCF) a je uděleno oprávnění k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="b0c24-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="b0c24-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="b0c24-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0c24-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0c24-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0c24-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b0c24-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b0c24-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b0c24-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0c24-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="b0c24-108">Attributes</span></span>  
 <span data-ttu-id="b0c24-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="b0c24-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b0c24-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b0c24-110">Child Elements</span></span>  
  
|<span data-ttu-id="b0c24-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="b0c24-111">Attribute</span></span>|<span data-ttu-id="b0c24-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b0c24-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="b0c24-113">\<add></span><span class="sxs-lookup"><span data-stu-id="b0c24-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="b0c24-114">Přidá uživatelský účet pro procesy, které hostování služby WCF a je uděleno oprávnění k připojení ke službě Sdílení</span><span class="sxs-lookup"><span data-stu-id="b0c24-114">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0c24-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b0c24-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b0c24-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="b0c24-116">Element</span></span>|<span data-ttu-id="b0c24-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b0c24-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0c24-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) nebo [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="b0c24-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="b0c24-119">Určuje nastavení konfigurace pro Net kanálu nebo TCP služby sdílení.</span><span class="sxs-lookup"><span data-stu-id="b0c24-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0c24-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0c24-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
