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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1610c77125d2820e3adc06b3c37177058c85abdd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="08565-102">&lt;diagnostics&gt; pro aktivaci</span><span class="sxs-lookup"><span data-stu-id="08565-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="08565-103">Nakonfiguruje [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] funkce diagnostiky pro naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="08565-103">Configures [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="08565-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="08565-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="08565-105">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="08565-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08565-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08565-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="08565-107">Typ</span><span class="sxs-lookup"><span data-stu-id="08565-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08565-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="08565-108">Attributes and Elements</span></span>  
 <span data-ttu-id="08565-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="08565-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08565-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="08565-110">Attributes</span></span>  
  
|<span data-ttu-id="08565-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="08565-111">Attribute</span></span>|<span data-ttu-id="08565-112">Popis</span><span class="sxs-lookup"><span data-stu-id="08565-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="08565-113">Logická hodnota, která určuje, zda jsou povoleny čítače výkonu k diagnostickým účelům.</span><span class="sxs-lookup"><span data-stu-id="08565-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08565-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="08565-114">Child Elements</span></span>  
 <span data-ttu-id="08565-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="08565-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08565-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="08565-116">Parent Elements</span></span>  
  
|<span data-ttu-id="08565-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="08565-117">Element</span></span>|<span data-ttu-id="08565-118">Popis</span><span class="sxs-lookup"><span data-stu-id="08565-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08565-119">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="08565-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="08565-120">Obsahuje nastavení konfigurace pro proces naslouchání SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="08565-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08565-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="08565-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
