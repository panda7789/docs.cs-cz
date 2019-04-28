---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: f9def3004b116afdc629de136cdfe0b0eb6e75c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673534"
---
# <a name="allowaccounts"></a><span data-ttu-id="fbc90-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="fbc90-101">\<allowAccounts></span></span>
<span data-ttu-id="fbc90-102">Obsahuje kolekci prvků konfigurace, které určují uživatelské účty pro procesy, které hostují služby Windows Communication Foundation (WCF) a jímž je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="fbc90-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="fbc90-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="fbc90-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbc90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbc90-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbc90-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fbc90-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fbc90-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fbc90-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbc90-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="fbc90-107">Attributes</span></span>  
 <span data-ttu-id="fbc90-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="fbc90-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fbc90-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fbc90-109">Child Elements</span></span>  
  
|<span data-ttu-id="fbc90-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="fbc90-110">Attribute</span></span>|<span data-ttu-id="fbc90-111">Popis</span><span class="sxs-lookup"><span data-stu-id="fbc90-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="fbc90-112">\<add></span><span class="sxs-lookup"><span data-stu-id="fbc90-112">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="fbc90-113">Přidá uživatelský účet pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě Sdílení</span><span class="sxs-lookup"><span data-stu-id="fbc90-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbc90-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fbc90-114">Parent Elements</span></span>  
  
|<span data-ttu-id="fbc90-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="fbc90-115">Element</span></span>|<span data-ttu-id="fbc90-116">Popis</span><span class="sxs-lookup"><span data-stu-id="fbc90-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbc90-117">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) nebo [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="fbc90-117">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="fbc90-118">Určuje nastavení konfigurace pro Net kanálu nebo služby Sdílení TCP.</span><span class="sxs-lookup"><span data-stu-id="fbc90-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbc90-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbc90-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
