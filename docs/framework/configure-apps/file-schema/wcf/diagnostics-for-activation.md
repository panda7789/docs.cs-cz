---
title: <diagnostics> pro aktivaci
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 30456963a7d74a93e39bb1fddc0910daae97f039
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203805"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="7021c-102">\<Diagnostika > pro aktivaci</span><span class="sxs-lookup"><span data-stu-id="7021c-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="7021c-103">Nakonfiguruje funkce diagnostiky Windows Communication Foundation (WCF) naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="7021c-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="7021c-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="7021c-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="7021c-105">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="7021c-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7021c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7021c-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="7021c-107">Type</span><span class="sxs-lookup"><span data-stu-id="7021c-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7021c-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7021c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7021c-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7021c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7021c-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7021c-110">Attributes</span></span>  
  
|<span data-ttu-id="7021c-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="7021c-111">Attribute</span></span>|<span data-ttu-id="7021c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7021c-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="7021c-113">Logická hodnota, která určuje, zda jsou povoleny čítače výkonu pro diagnostické účely.</span><span class="sxs-lookup"><span data-stu-id="7021c-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7021c-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7021c-114">Child Elements</span></span>  
 <span data-ttu-id="7021c-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="7021c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7021c-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7021c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7021c-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="7021c-117">Element</span></span>|<span data-ttu-id="7021c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="7021c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7021c-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="7021c-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="7021c-120">Obsahuje nastavení konfigurace pro naslouchací proces SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="7021c-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7021c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7021c-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
