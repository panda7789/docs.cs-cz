---
title: '&lt;diagnostics&gt; pro aktivaci'
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 4e5332eed87ded51cebcd614f45cbc8e80e570fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="83a0c-102">&lt;diagnostics&gt; pro aktivaci</span><span class="sxs-lookup"><span data-stu-id="83a0c-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="83a0c-103">Nakonfiguruje funkce diagnostiky naslouchání Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="83a0c-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="83a0c-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="83a0c-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="83a0c-105">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="83a0c-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83a0c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83a0c-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="83a0c-107">Typ</span><span class="sxs-lookup"><span data-stu-id="83a0c-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83a0c-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="83a0c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="83a0c-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="83a0c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83a0c-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="83a0c-110">Attributes</span></span>  
  
|<span data-ttu-id="83a0c-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="83a0c-111">Attribute</span></span>|<span data-ttu-id="83a0c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="83a0c-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="83a0c-113">Logická hodnota, která určuje, zda jsou povoleny čítače výkonu k diagnostickým účelům.</span><span class="sxs-lookup"><span data-stu-id="83a0c-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83a0c-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="83a0c-114">Child Elements</span></span>  
 <span data-ttu-id="83a0c-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="83a0c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83a0c-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="83a0c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="83a0c-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="83a0c-117">Element</span></span>|<span data-ttu-id="83a0c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="83a0c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83a0c-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="83a0c-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="83a0c-120">Obsahuje nastavení konfigurace pro proces naslouchání SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="83a0c-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83a0c-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="83a0c-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
