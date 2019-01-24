---
title: '&lt;diagnostics&gt; pro aktivaci'
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 5d8fcce28182dcac945655a52d829945a432a9b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723911"
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="c33d6-102">&lt;diagnostics&gt; pro aktivaci</span><span class="sxs-lookup"><span data-stu-id="c33d6-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="c33d6-103">Nakonfiguruje funkce diagnostiky Windows Communication Foundation (WCF) naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="c33d6-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="c33d6-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="c33d6-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="c33d6-105">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="c33d6-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c33d6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c33d6-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="c33d6-107">Typ</span><span class="sxs-lookup"><span data-stu-id="c33d6-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c33d6-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c33d6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c33d6-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c33d6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c33d6-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c33d6-110">Attributes</span></span>  
  
|<span data-ttu-id="c33d6-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="c33d6-111">Attribute</span></span>|<span data-ttu-id="c33d6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c33d6-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="c33d6-113">Logická hodnota, která určuje, zda jsou povoleny čítače výkonu pro diagnostické účely.</span><span class="sxs-lookup"><span data-stu-id="c33d6-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c33d6-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c33d6-114">Child Elements</span></span>  
 <span data-ttu-id="c33d6-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="c33d6-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c33d6-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c33d6-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c33d6-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="c33d6-117">Element</span></span>|<span data-ttu-id="c33d6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="c33d6-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c33d6-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="c33d6-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="c33d6-120">Obsahuje nastavení konfigurace pro naslouchací proces SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="c33d6-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c33d6-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c33d6-121">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
