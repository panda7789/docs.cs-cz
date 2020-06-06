---
title: <diagnostics>pro aktivaci
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400414"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="4a0c1-102">\<diagnostics>pro aktivaci</span><span class="sxs-lookup"><span data-stu-id="4a0c1-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="4a0c1-103">Konfiguruje funkce diagnostiky naslouchacího procesu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4a0c1-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="4a0c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a0c1-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="4a0c1-105">Typ</span><span class="sxs-lookup"><span data-stu-id="4a0c1-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a0c1-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4a0c1-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4a0c1-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4a0c1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a0c1-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="4a0c1-108">Attributes</span></span>  
  
|<span data-ttu-id="4a0c1-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="4a0c1-109">Attribute</span></span>|<span data-ttu-id="4a0c1-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4a0c1-110">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="4a0c1-111">Logická hodnota, která určuje, zda jsou povoleny čítače výkonu pro diagnostické účely.</span><span class="sxs-lookup"><span data-stu-id="4a0c1-111">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a0c1-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4a0c1-112">Child Elements</span></span>  
 <span data-ttu-id="4a0c1-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="4a0c1-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a0c1-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4a0c1-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4a0c1-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="4a0c1-115">Element</span></span>|<span data-ttu-id="4a0c1-116">Description</span><span class="sxs-lookup"><span data-stu-id="4a0c1-116">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="4a0c1-117">Obsahuje nastavení konfigurace procesu naslouchacího procesu SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="4a0c1-117">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a0c1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a0c1-118">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
