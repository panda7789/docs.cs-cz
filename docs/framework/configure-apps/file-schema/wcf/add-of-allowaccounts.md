---
title: "&lt;add&gt; – &lt;allowAccounts&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09ab06bb94249e79743335da1a360f6b668b1d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="a137b-102">&lt;add&gt; – &lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="a137b-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="a137b-103">Určuje, uživatelský účet pro procesy na tomto hostiteli [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a je uděleno oprávnění k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="a137b-103">Specifies a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="a137b-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="a137b-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a137b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a137b-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a137b-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a137b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a137b-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a137b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a137b-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="a137b-108">Attributes</span></span>  
  
|<span data-ttu-id="a137b-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="a137b-109">Attribute</span></span>|<span data-ttu-id="a137b-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a137b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a137b-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="a137b-111">securityIdentifier</span></span>|<span data-ttu-id="a137b-112">Řetězec, který určuje jedinečný identifikátor, který se používá k identifikaci uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="a137b-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="a137b-113">Výchozí hodnoty jsou LocalSystem, správci, NS, LS a IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="a137b-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a137b-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a137b-114">Child Elements</span></span>  
 <span data-ttu-id="a137b-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="a137b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a137b-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a137b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a137b-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="a137b-117">Element</span></span>|<span data-ttu-id="a137b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="a137b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a137b-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="a137b-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="a137b-120">Kolekci elementů konfigurace, které obsahují `securityIdentifier` atribut k určení uživatelských účtů pro procesy, které hostují [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a je uděleno oprávnění k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="a137b-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a137b-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="a137b-121">Example</span></span>  
 <span data-ttu-id="a137b-122">Následující příklad konfigurace přidá pět výchozích identifikátory pro uživatelské účty do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="a137b-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a137b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="a137b-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
