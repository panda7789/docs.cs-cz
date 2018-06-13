---
title: '&lt;add&gt; – &lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 2230b8d22a14c3df5eb3aa10872246febce015e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349688"
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="31187-102">&lt;add&gt; – &lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="31187-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="31187-103">Určuje uživatelský účet pro procesy, které hostování služby WCF a je uděleno oprávnění k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="31187-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="31187-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="31187-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31187-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31187-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31187-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="31187-106">Attributes and Elements</span></span>  
 <span data-ttu-id="31187-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="31187-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31187-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="31187-108">Attributes</span></span>  
  
|<span data-ttu-id="31187-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="31187-109">Attribute</span></span>|<span data-ttu-id="31187-110">Popis</span><span class="sxs-lookup"><span data-stu-id="31187-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31187-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="31187-111">securityIdentifier</span></span>|<span data-ttu-id="31187-112">Řetězec, který určuje jedinečný identifikátor, který se používá k identifikaci uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="31187-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="31187-113">Výchozí hodnoty jsou LocalSystem, správci, NS, LS a IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="31187-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31187-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="31187-114">Child Elements</span></span>  
 <span data-ttu-id="31187-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="31187-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31187-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="31187-116">Parent Elements</span></span>  
  
|<span data-ttu-id="31187-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="31187-117">Element</span></span>|<span data-ttu-id="31187-118">Popis</span><span class="sxs-lookup"><span data-stu-id="31187-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31187-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="31187-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="31187-120">Kolekci elementů konfigurace, které obsahují `securityIdentifier` atribut zadejte uživatelské účty pro procesy, které hostování služby WCF a je uděleno oprávnění k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="31187-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="31187-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="31187-121">Example</span></span>  
 <span data-ttu-id="31187-122">Následující příklad konfigurace přidá pět výchozích identifikátory pro uživatelské účty do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="31187-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="31187-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="31187-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
