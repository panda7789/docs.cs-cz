---
title: <add> z <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 1ed0b5025ab969c45d7440f2a209426c5c87f549
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920278"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="6a034-102">\<Přidat > \<> allowAccounts</span><span class="sxs-lookup"><span data-stu-id="6a034-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="6a034-103">Určuje uživatelský účet pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="6a034-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="6a034-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="6a034-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a034-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a034-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a034-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6a034-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6a034-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6a034-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a034-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="6a034-108">Attributes</span></span>  
  
|<span data-ttu-id="6a034-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="6a034-109">Attribute</span></span>|<span data-ttu-id="6a034-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6a034-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a034-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="6a034-111">securityIdentifier</span></span>|<span data-ttu-id="6a034-112">Řetězec, který určuje jedinečný identifikátor, který slouží k identifikaci uživatelského účtu.</span><span class="sxs-lookup"><span data-stu-id="6a034-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="6a034-113">Výchozí hodnoty jsou LocalSystem, Administrators, NS, LS a IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="6a034-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a034-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6a034-114">Child Elements</span></span>  
 <span data-ttu-id="6a034-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="6a034-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a034-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6a034-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6a034-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="6a034-117">Element</span></span>|<span data-ttu-id="6a034-118">Popis</span><span class="sxs-lookup"><span data-stu-id="6a034-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a034-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="6a034-119">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="6a034-120">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atribut pro určení uživatelských účtů pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="6a034-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a034-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a034-121">Example</span></span>  
 <span data-ttu-id="6a034-122">Následující konfigurační příklad přidá pět výchozích identifikátorů pro uživatelské účty do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="6a034-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a034-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a034-123">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
