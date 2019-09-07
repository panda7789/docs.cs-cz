---
title: <diagnostics>pro aktivaci
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400414"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="3d2a6-102">\<Diagnostika > pro aktivaci</span><span class="sxs-lookup"><span data-stu-id="3d2a6-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="3d2a6-103">Konfiguruje funkce diagnostiky naslouchacího procesu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3d2a6-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
<span data-ttu-id="3d2a6-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3d2a6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3d2a6-105">&nbsp;&nbsp;[ **\<System. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="3d2a6-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="3d2a6-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> diagnostiky**</span><span class="sxs-lookup"><span data-stu-id="3d2a6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d2a6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d2a6-107">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="3d2a6-108">type</span><span class="sxs-lookup"><span data-stu-id="3d2a6-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d2a6-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3d2a6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3d2a6-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3d2a6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d2a6-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="3d2a6-111">Attributes</span></span>  
  
|<span data-ttu-id="3d2a6-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="3d2a6-112">Attribute</span></span>|<span data-ttu-id="3d2a6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3d2a6-113">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="3d2a6-114">Logická hodnota, která určuje, zda jsou povoleny čítače výkonu pro diagnostické účely.</span><span class="sxs-lookup"><span data-stu-id="3d2a6-114">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d2a6-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3d2a6-115">Child Elements</span></span>  
 <span data-ttu-id="3d2a6-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="3d2a6-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d2a6-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3d2a6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3d2a6-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="3d2a6-118">Element</span></span>|<span data-ttu-id="3d2a6-119">Popis</span><span class="sxs-lookup"><span data-stu-id="3d2a6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d2a6-120">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="3d2a6-120">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="3d2a6-121">Obsahuje nastavení konfigurace procesu naslouchacího procesu SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="3d2a6-121">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d2a6-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d2a6-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
