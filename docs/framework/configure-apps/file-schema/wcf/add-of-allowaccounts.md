---
title: <add> z <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 6edf0bc2d532deb01f24450b9868bbc240bab413
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259607"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="10c4a-102">\<add> of \<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="10c4a-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="10c4a-103">Určuje uživatelský účet pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="10c4a-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="10c4a-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="10c4a-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10c4a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10c4a-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10c4a-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="10c4a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="10c4a-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="10c4a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10c4a-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="10c4a-108">Attributes</span></span>  
  
|<span data-ttu-id="10c4a-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="10c4a-109">Attribute</span></span>|<span data-ttu-id="10c4a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="10c4a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10c4a-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="10c4a-111">securityIdentifier</span></span>|<span data-ttu-id="10c4a-112">Řetězec určující jedinečný identifikátor sloužící k identifikaci uživatelského účtu.</span><span class="sxs-lookup"><span data-stu-id="10c4a-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="10c4a-113">Výchozí hodnoty jsou LocalSystem, správci, NS, LS a IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="10c4a-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10c4a-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="10c4a-114">Child Elements</span></span>  
 <span data-ttu-id="10c4a-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="10c4a-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10c4a-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="10c4a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="10c4a-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="10c4a-117">Element</span></span>|<span data-ttu-id="10c4a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="10c4a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10c4a-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="10c4a-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="10c4a-120">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atributy uživatelské účty pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="10c4a-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="10c4a-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="10c4a-121">Example</span></span>  
 <span data-ttu-id="10c4a-122">Následující příklad konfigurace přidá pět výchozích identifikátorů pro uživatelské účty do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="10c4a-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10c4a-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10c4a-123">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
