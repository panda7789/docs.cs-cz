---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c1c4630e6191dbbe02688a4e4a9db9e18b8d36d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508412"
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="f4a28-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="f4a28-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="f4a28-103">Obsahuje kolekci prvků konfigurace, které určují uživatelské účty pro procesy, které hostují služby Windows Communication Foundation (WCF) a jímž je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="f4a28-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="f4a28-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="f4a28-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4a28-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4a28-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4a28-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f4a28-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f4a28-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f4a28-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4a28-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="f4a28-108">Attributes</span></span>  
 <span data-ttu-id="f4a28-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="f4a28-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f4a28-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f4a28-110">Child Elements</span></span>  
  
|<span data-ttu-id="f4a28-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f4a28-111">Attribute</span></span>|<span data-ttu-id="f4a28-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f4a28-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="f4a28-113">\<add></span><span class="sxs-lookup"><span data-stu-id="f4a28-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="f4a28-114">Přidá uživatelský účet pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě Sdílení</span><span class="sxs-lookup"><span data-stu-id="f4a28-114">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4a28-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f4a28-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f4a28-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="f4a28-116">Element</span></span>|<span data-ttu-id="f4a28-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f4a28-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4a28-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) nebo [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="f4a28-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="f4a28-119">Určuje nastavení konfigurace pro Net kanálu nebo služby Sdílení TCP.</span><span class="sxs-lookup"><span data-stu-id="f4a28-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4a28-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4a28-120">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
