---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c62f29c53d807cab397ff09c6163d924a71ea319
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926602"
---
# <a name="allowaccounts"></a><span data-ttu-id="94483-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="94483-101">\<allowAccounts></span></span>
<span data-ttu-id="94483-102">Obsahuje kolekci prvků konfigurace, které určují uživatelské účty pro procesy, které hostují služby Windows Communication Foundation (WCF) a kterým je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="94483-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="94483-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="94483-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94483-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94483-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94483-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="94483-105">Attributes and Elements</span></span>  
 <span data-ttu-id="94483-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="94483-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94483-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="94483-107">Attributes</span></span>  
 <span data-ttu-id="94483-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="94483-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="94483-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="94483-109">Child Elements</span></span>  
  
|<span data-ttu-id="94483-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="94483-110">Attribute</span></span>|<span data-ttu-id="94483-111">Popis</span><span class="sxs-lookup"><span data-stu-id="94483-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="94483-112">\<add></span><span class="sxs-lookup"><span data-stu-id="94483-112">\<add></span></span>](add-of-allowaccounts.md)|<span data-ttu-id="94483-113">Přidá uživatelský účet pro procesy, které hostují služby WCF, a uděluje přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="94483-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94483-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="94483-114">Parent Elements</span></span>  
  
|<span data-ttu-id="94483-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="94483-115">Element</span></span>|<span data-ttu-id="94483-116">Popis</span><span class="sxs-lookup"><span data-stu-id="94483-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94483-117">NET. pipe > nebo [ \<](net-pipe.md) [ \<NET. TCP >](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="94483-117">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="94483-118">Určuje nastavení konfigurace pro síťové kanály nebo služby sdílení protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="94483-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94483-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94483-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
