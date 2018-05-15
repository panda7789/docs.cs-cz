---
title: '&lt;add&gt; – &lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 20e1052a0517bb170cf796dd40d58c298185a958
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="7e61e-102">&lt;add&gt; – &lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="7e61e-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="7e61e-103">Určuje, uživatelský účet pro procesy na tomto hostiteli [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a je uděleno oprávnění k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="7e61e-103">Specifies a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="7e61e-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="7e61e-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e61e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e61e-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e61e-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7e61e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="7e61e-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7e61e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e61e-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="7e61e-108">Attributes</span></span>  
  
|<span data-ttu-id="7e61e-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="7e61e-109">Attribute</span></span>|<span data-ttu-id="7e61e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="7e61e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e61e-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="7e61e-111">securityIdentifier</span></span>|<span data-ttu-id="7e61e-112">Řetězec, který určuje jedinečný identifikátor, který se používá k identifikaci uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="7e61e-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="7e61e-113">Výchozí hodnoty jsou LocalSystem, správci, NS, LS a IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="7e61e-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e61e-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7e61e-114">Child Elements</span></span>  
 <span data-ttu-id="7e61e-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="7e61e-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e61e-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7e61e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7e61e-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="7e61e-117">Element</span></span>|<span data-ttu-id="7e61e-118">Popis</span><span class="sxs-lookup"><span data-stu-id="7e61e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e61e-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="7e61e-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="7e61e-120">Kolekci elementů konfigurace, které obsahují `securityIdentifier` atribut k určení uživatelských účtů pro procesy, které hostují [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a je uděleno oprávnění k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="7e61e-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7e61e-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e61e-121">Example</span></span>  
 <span data-ttu-id="7e61e-122">Následující příklad konfigurace přidá pět výchozích identifikátory pro uživatelské účty do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="7e61e-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>  
   // LocalSystem account  
   <add securityIdentifier="S-1-5-18"/>  
   // LocalService account  
   <add securityIdentifier="S-1-5-19"/>  
   // Administrators account  
   <add securityIdentifier="S-1-5-20"/>  
   // Network Service account  
   <add securityIdentifier="S-1-5-32-544" />  
   // IIS_IUSRS account (Vista only)  
   <add securityIdentifier="S-1-5-32-568"/>  
</allowAccounts>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e61e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e61e-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
