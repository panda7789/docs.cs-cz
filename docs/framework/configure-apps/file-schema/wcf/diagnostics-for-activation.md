---
title: '&lt;diagnostics&gt; pro aktivaci'
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 28f051a7ab06dbc1b40f804c56071818eb37e88b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144974"
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="42eea-102">&lt;diagnostics&gt; pro aktivaci</span><span class="sxs-lookup"><span data-stu-id="42eea-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="42eea-103">Nakonfiguruje funkce diagnostiky Windows Communication Foundation (WCF) naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="42eea-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="42eea-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="42eea-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="42eea-105">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="42eea-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42eea-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42eea-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="42eea-107">Typ</span><span class="sxs-lookup"><span data-stu-id="42eea-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42eea-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="42eea-108">Attributes and Elements</span></span>  
 <span data-ttu-id="42eea-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="42eea-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42eea-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="42eea-110">Attributes</span></span>  
  
|<span data-ttu-id="42eea-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="42eea-111">Attribute</span></span>|<span data-ttu-id="42eea-112">Popis</span><span class="sxs-lookup"><span data-stu-id="42eea-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="42eea-113">Logická hodnota, která určuje, zda jsou povoleny čítače výkonu pro diagnostické účely.</span><span class="sxs-lookup"><span data-stu-id="42eea-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42eea-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="42eea-114">Child Elements</span></span>  
 <span data-ttu-id="42eea-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="42eea-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42eea-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="42eea-116">Parent Elements</span></span>  
  
|<span data-ttu-id="42eea-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="42eea-117">Element</span></span>|<span data-ttu-id="42eea-118">Popis</span><span class="sxs-lookup"><span data-stu-id="42eea-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42eea-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="42eea-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="42eea-120">Obsahuje nastavení konfigurace pro naslouchací proces SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="42eea-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42eea-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="42eea-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
