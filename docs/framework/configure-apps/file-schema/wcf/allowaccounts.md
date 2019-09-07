---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398409"
---
# <a name="allowaccounts"></a><span data-ttu-id="22888-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="22888-101">\<allowAccounts></span></span>
<span data-ttu-id="22888-102">Obsahuje kolekci prvků konfigurace, které určují uživatelské účty pro procesy, které hostují služby Windows Communication Foundation (WCF) a kterým je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="22888-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
<span data-ttu-id="22888-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="22888-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="22888-104">&nbsp;&nbsp;[ **\<System. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="22888-104">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="22888-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> NET. pipe**](net-pipe.md)</span><span class="sxs-lookup"><span data-stu-id="22888-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)</span></span>\
<span data-ttu-id="22888-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<allowAccounts >**</span><span class="sxs-lookup"><span data-stu-id="22888-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22888-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22888-107">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22888-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="22888-108">Attributes and Elements</span></span>  
 <span data-ttu-id="22888-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="22888-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22888-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="22888-110">Attributes</span></span>  
 <span data-ttu-id="22888-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="22888-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="22888-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="22888-112">Child Elements</span></span>  
  
|<span data-ttu-id="22888-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="22888-113">Attribute</span></span>|<span data-ttu-id="22888-114">Popis</span><span class="sxs-lookup"><span data-stu-id="22888-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="22888-115">\<add></span><span class="sxs-lookup"><span data-stu-id="22888-115">\<add></span></span>](add-of-allowaccounts.md)|<span data-ttu-id="22888-116">Přidá uživatelský účet pro procesy, které hostují služby WCF, a uděluje přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="22888-116">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22888-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="22888-117">Parent Elements</span></span>  
  
|<span data-ttu-id="22888-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="22888-118">Element</span></span>|<span data-ttu-id="22888-119">Popis</span><span class="sxs-lookup"><span data-stu-id="22888-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22888-120">NET. pipe > nebo [ \<](net-pipe.md) [ \<NET. TCP >](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="22888-120">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="22888-121">Určuje nastavení konfigurace pro síťové kanály nebo služby sdílení protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="22888-121">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22888-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22888-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
