---
title: '&lt;add&gt; – &lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 63f8e678b81838a25664180888e9e7a8eabd043d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721947"
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="e3a11-102">&lt;add&gt; – &lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="e3a11-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="e3a11-103">Určuje uživatelský účet pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="e3a11-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="e3a11-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="e3a11-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a11-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3a11-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3a11-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e3a11-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e3a11-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e3a11-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3a11-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="e3a11-108">Attributes</span></span>  
  
|<span data-ttu-id="e3a11-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="e3a11-109">Attribute</span></span>|<span data-ttu-id="e3a11-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e3a11-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3a11-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="e3a11-111">securityIdentifier</span></span>|<span data-ttu-id="e3a11-112">Řetězec určující jedinečný identifikátor sloužící k identifikaci uživatelského účtu.</span><span class="sxs-lookup"><span data-stu-id="e3a11-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="e3a11-113">Výchozí hodnoty jsou LocalSystem, správci, NS, LS a IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="e3a11-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3a11-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e3a11-114">Child Elements</span></span>  
 <span data-ttu-id="e3a11-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="e3a11-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3a11-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e3a11-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e3a11-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="e3a11-117">Element</span></span>|<span data-ttu-id="e3a11-118">Popis</span><span class="sxs-lookup"><span data-stu-id="e3a11-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3a11-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="e3a11-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="e3a11-120">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atributy uživatelské účty pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="e3a11-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e3a11-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3a11-121">Example</span></span>  
 <span data-ttu-id="e3a11-122">Následující příklad konfigurace přidá pět výchozích identifikátorů pro uživatelské účty do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="e3a11-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3a11-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3a11-123">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
