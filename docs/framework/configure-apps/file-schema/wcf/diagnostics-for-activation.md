---
title: <diagnostics>pro aktivaci
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 543c41936921eda39017e07f1c97294b268a9141
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919223"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="b3850-102">\<Diagnostika > pro aktivaci</span><span class="sxs-lookup"><span data-stu-id="b3850-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="b3850-103">Konfiguruje funkce diagnostiky naslouchacího procesu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b3850-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="b3850-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="b3850-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="b3850-105">\<> diagnostiky</span><span class="sxs-lookup"><span data-stu-id="b3850-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3850-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3850-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="b3850-107">type</span><span class="sxs-lookup"><span data-stu-id="b3850-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3850-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b3850-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b3850-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b3850-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3850-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b3850-110">Attributes</span></span>  
  
|<span data-ttu-id="b3850-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="b3850-111">Attribute</span></span>|<span data-ttu-id="b3850-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b3850-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="b3850-113">Logická hodnota, která určuje, zda jsou povoleny čítače výkonu pro diagnostické účely.</span><span class="sxs-lookup"><span data-stu-id="b3850-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3850-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b3850-114">Child Elements</span></span>  
 <span data-ttu-id="b3850-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="b3850-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3850-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b3850-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b3850-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="b3850-117">Element</span></span>|<span data-ttu-id="b3850-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b3850-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3850-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="b3850-119">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="b3850-120">Obsahuje nastavení konfigurace procesu naslouchacího procesu SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="b3850-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3850-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3850-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
