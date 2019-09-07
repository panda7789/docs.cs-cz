---
title: <add> z <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 02654b8ab198a2b161b3044c1f3aa452761a6a4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398382"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="03edd-102">\<Přidat > \<> allowAccounts</span><span class="sxs-lookup"><span data-stu-id="03edd-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="03edd-103">Určuje uživatelský účet pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="03edd-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
<span data-ttu-id="03edd-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="03edd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="03edd-105">&nbsp;&nbsp;[ **\<System. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="03edd-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="03edd-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> NET. pipe**](net-pipe.md)</span><span class="sxs-lookup"><span data-stu-id="03edd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)</span></span>\
<span data-ttu-id="03edd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<allowAccounts >** ](allowaccounts.md)</span><span class="sxs-lookup"><span data-stu-id="03edd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)</span></span>\
<span data-ttu-id="03edd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="03edd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03edd-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03edd-109">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03edd-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03edd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="03edd-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03edd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03edd-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="03edd-112">Attributes</span></span>  
  
|<span data-ttu-id="03edd-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="03edd-113">Attribute</span></span>|<span data-ttu-id="03edd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="03edd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="03edd-115">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="03edd-115">securityIdentifier</span></span>|<span data-ttu-id="03edd-116">Řetězec, který určuje jedinečný identifikátor, který slouží k identifikaci uživatelského účtu.</span><span class="sxs-lookup"><span data-stu-id="03edd-116">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="03edd-117">Výchozí hodnoty jsou LocalSystem, Administrators, NS, LS a IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="03edd-117">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03edd-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03edd-118">Child Elements</span></span>  
 <span data-ttu-id="03edd-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="03edd-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03edd-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03edd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="03edd-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="03edd-121">Element</span></span>|<span data-ttu-id="03edd-122">Popis</span><span class="sxs-lookup"><span data-stu-id="03edd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03edd-123">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="03edd-123">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="03edd-124">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atribut pro určení uživatelských účtů pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="03edd-124">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="03edd-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="03edd-125">Example</span></span>  
 <span data-ttu-id="03edd-126">Následující konfigurační příklad přidá pět výchozích identifikátorů pro uživatelské účty do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="03edd-126">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03edd-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03edd-127">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
