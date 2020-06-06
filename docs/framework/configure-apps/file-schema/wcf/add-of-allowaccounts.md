---
title: <add> z <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 02654b8ab198a2b161b3044c1f3aa452761a6a4c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398382"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="f6ff2-102">\<add> z \<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="f6ff2-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="f6ff2-103">Určuje uživatelský účet pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="f6ff2-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="f6ff2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6ff2-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6ff2-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f6ff2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f6ff2-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f6ff2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6ff2-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="f6ff2-107">Attributes</span></span>  
  
|<span data-ttu-id="f6ff2-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="f6ff2-108">Attribute</span></span>|<span data-ttu-id="f6ff2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f6ff2-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6ff2-110">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="f6ff2-110">securityIdentifier</span></span>|<span data-ttu-id="f6ff2-111">Řetězec, který určuje jedinečný identifikátor, který slouží k identifikaci uživatelského účtu.</span><span class="sxs-lookup"><span data-stu-id="f6ff2-111">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="f6ff2-112">Výchozí hodnoty jsou LocalSystem, Administrators, NS, LS a IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="f6ff2-112">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6ff2-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f6ff2-113">Child Elements</span></span>  
 <span data-ttu-id="f6ff2-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="f6ff2-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6ff2-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f6ff2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f6ff2-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="f6ff2-116">Element</span></span>|<span data-ttu-id="f6ff2-117">Description</span><span class="sxs-lookup"><span data-stu-id="f6ff2-117">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="f6ff2-118">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atribut pro určení uživatelských účtů pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="f6ff2-118">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f6ff2-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6ff2-119">Example</span></span>  
 <span data-ttu-id="f6ff2-120">Následující konfigurační příklad přidá pět výchozích identifikátorů pro uživatelské účty do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="f6ff2-120">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6ff2-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6ff2-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
