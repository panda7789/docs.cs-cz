---
title: <add> of <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 1c6764b37b2aa5349b8ccf63e6b7c2bc580b69b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186599"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="5fc19-102">\<add> of \<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="5fc19-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="5fc19-103">Určuje uživatelský účet pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="5fc19-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="5fc19-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="5fc19-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fc19-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fc19-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fc19-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5fc19-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5fc19-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5fc19-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fc19-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="5fc19-108">Attributes</span></span>  
  
|<span data-ttu-id="5fc19-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="5fc19-109">Attribute</span></span>|<span data-ttu-id="5fc19-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5fc19-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5fc19-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="5fc19-111">securityIdentifier</span></span>|<span data-ttu-id="5fc19-112">Řetězec určující jedinečný identifikátor sloužící k identifikaci uživatelského účtu.</span><span class="sxs-lookup"><span data-stu-id="5fc19-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="5fc19-113">Výchozí hodnoty jsou LocalSystem, správci, NS, LS a IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="5fc19-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fc19-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5fc19-114">Child Elements</span></span>  
 <span data-ttu-id="5fc19-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="5fc19-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fc19-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5fc19-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5fc19-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="5fc19-117">Element</span></span>|<span data-ttu-id="5fc19-118">Popis</span><span class="sxs-lookup"><span data-stu-id="5fc19-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fc19-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="5fc19-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="5fc19-120">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atributy uživatelské účty pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="5fc19-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5fc19-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fc19-121">Example</span></span>  
 <span data-ttu-id="5fc19-122">Následující příklad konfigurace přidá pět výchozích identifikátorů pro uživatelské účty do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="5fc19-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>
  <!-- LocalSystem account -->
  <add securityIdentifier="S-1-5-18" />
  <!-- LocalService account -->
  <add securityIdentifier="S-1-5-19" />
  <!-- Administrators account -->
  <add securityIdentifier="S-1-5-20" />
  <!-- Network Service account -->
  <add securityIdentifier="S-1-5-32-544" />
  <!-- IIS_IUSRS account (Vista only) -->
  <add securityIdentifier="S-1-5-32-568" />
</allowAccounts>
```  
  
## <a name="see-also"></a><span data-ttu-id="5fc19-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fc19-123">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
