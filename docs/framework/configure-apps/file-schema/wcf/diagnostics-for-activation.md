---
title: '&lt;diagnostics&gt; pro aktivaci'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 29f2e56dd18da9dc3ce3206f5c3c80f4a47a7ff0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="dc18c-102">&lt;diagnostics&gt; pro aktivaci</span><span class="sxs-lookup"><span data-stu-id="dc18c-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="dc18c-103">Nakonfiguruje [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] funkce diagnostiky pro naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="dc18c-103">Configures [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="dc18c-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="dc18c-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="dc18c-105">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="dc18c-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc18c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc18c-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="dc18c-107">Typ</span><span class="sxs-lookup"><span data-stu-id="dc18c-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc18c-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dc18c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dc18c-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dc18c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc18c-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="dc18c-110">Attributes</span></span>  
  
|<span data-ttu-id="dc18c-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="dc18c-111">Attribute</span></span>|<span data-ttu-id="dc18c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="dc18c-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="dc18c-113">Logická hodnota, která určuje, zda jsou povoleny čítače výkonu k diagnostickým účelům.</span><span class="sxs-lookup"><span data-stu-id="dc18c-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc18c-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dc18c-114">Child Elements</span></span>  
 <span data-ttu-id="dc18c-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="dc18c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc18c-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dc18c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="dc18c-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc18c-117">Element</span></span>|<span data-ttu-id="dc18c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="dc18c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc18c-119">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="dc18c-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="dc18c-120">Obsahuje nastavení konfigurace pro proces naslouchání SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="dc18c-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc18c-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc18c-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
