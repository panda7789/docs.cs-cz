---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: f9def3004b116afdc629de136cdfe0b0eb6e75c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102619"
---
# <a name="allowaccounts"></a><span data-ttu-id="69f52-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="69f52-101">\<allowAccounts></span></span>
<span data-ttu-id="69f52-102">Obsahuje kolekci prvků konfigurace, které určují uživatelské účty pro procesy, které hostují služby Windows Communication Foundation (WCF) a jímž je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="69f52-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="69f52-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="69f52-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69f52-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69f52-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="69f52-105">Attributes and Elements</span></span>  
 <span data-ttu-id="69f52-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="69f52-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69f52-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="69f52-107">Attributes</span></span>  
 <span data-ttu-id="69f52-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="69f52-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69f52-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="69f52-109">Child Elements</span></span>  
  
|<span data-ttu-id="69f52-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="69f52-110">Attribute</span></span>|<span data-ttu-id="69f52-111">Popis</span><span class="sxs-lookup"><span data-stu-id="69f52-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="69f52-112">\<add></span><span class="sxs-lookup"><span data-stu-id="69f52-112">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="69f52-113">Přidá uživatelský účet pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě Sdílení</span><span class="sxs-lookup"><span data-stu-id="69f52-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69f52-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="69f52-114">Parent Elements</span></span>  
  
|<span data-ttu-id="69f52-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="69f52-115">Element</span></span>|<span data-ttu-id="69f52-116">Popis</span><span class="sxs-lookup"><span data-stu-id="69f52-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="69f52-117">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) nebo [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="69f52-117">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="69f52-118">Určuje nastavení konfigurace pro Net kanálu nebo služby Sdílení TCP.</span><span class="sxs-lookup"><span data-stu-id="69f52-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69f52-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69f52-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
