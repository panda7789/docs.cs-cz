---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398409"
---
# \<allowAccounts>
<span data-ttu-id="7b5fd-101">Obsahuje kolekci prvků konfigurace, které určují uživatelské účty pro procesy, které hostují služby Windows Communication Foundation (WCF) a kterým je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="7b5fd-101">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="7b5fd-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b5fd-102">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b5fd-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7b5fd-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7b5fd-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7b5fd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b5fd-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="7b5fd-105">Attributes</span></span>  
 <span data-ttu-id="7b5fd-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="7b5fd-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7b5fd-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7b5fd-107">Child Elements</span></span>  
  
|<span data-ttu-id="7b5fd-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="7b5fd-108">Attribute</span></span>|<span data-ttu-id="7b5fd-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7b5fd-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="7b5fd-110">Přidá uživatelský účet pro procesy, které hostují služby WCF, a uděluje přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="7b5fd-110">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b5fd-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7b5fd-111">Parent Elements</span></span>  
  
|<span data-ttu-id="7b5fd-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="7b5fd-112">Element</span></span>|<span data-ttu-id="7b5fd-113">Description</span><span class="sxs-lookup"><span data-stu-id="7b5fd-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b5fd-114">[\<net.pipe>](net-pipe.md)ani[\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="7b5fd-114">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="7b5fd-115">Určuje nastavení konfigurace pro síťové kanály nebo služby sdílení protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="7b5fd-115">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b5fd-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b5fd-116">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
