---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: bbfe0d5d531cf61c01f95d0e82ce0f894031d6f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="0ddcc-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="0ddcc-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="0ddcc-103">Obsahuje kolekci elementů konfigurace, které určují uživatelské účty pro procesy na tomto hostiteli služby Windows Communication Foundation (WCF) a je uděleno oprávnění k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="0ddcc-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="0ddcc-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="0ddcc-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ddcc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ddcc-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ddcc-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0ddcc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="0ddcc-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0ddcc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ddcc-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="0ddcc-108">Attributes</span></span>  
 <span data-ttu-id="0ddcc-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="0ddcc-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0ddcc-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0ddcc-110">Child Elements</span></span>  
  
|<span data-ttu-id="0ddcc-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="0ddcc-111">Attribute</span></span>|<span data-ttu-id="0ddcc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddcc-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="0ddcc-113">\<add></span><span class="sxs-lookup"><span data-stu-id="0ddcc-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="0ddcc-114">Přidá uživatelský účet pro procesy na tomto hostiteli [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a je uděleno oprávnění k připojení ke službě Sdílení</span><span class="sxs-lookup"><span data-stu-id="0ddcc-114">Adds a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0ddcc-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0ddcc-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0ddcc-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="0ddcc-116">Element</span></span>|<span data-ttu-id="0ddcc-117">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddcc-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ddcc-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) nebo [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="0ddcc-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="0ddcc-119">Určuje nastavení konfigurace pro Net kanálu nebo TCP služby sdílení.</span><span class="sxs-lookup"><span data-stu-id="0ddcc-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ddcc-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ddcc-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
