---
title: <diagnostics> pro aktivaci
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: ac235b9a3c125cd3fe63ccd899e2ff92d4d3f31b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278445"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="05280-102">\<Diagnostika > pro aktivaci</span><span class="sxs-lookup"><span data-stu-id="05280-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="05280-103">Nakonfiguruje funkce diagnostiky Windows Communication Foundation (WCF) naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="05280-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="05280-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="05280-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="05280-105">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="05280-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05280-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05280-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="05280-107">Typ</span><span class="sxs-lookup"><span data-stu-id="05280-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05280-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="05280-108">Attributes and Elements</span></span>  
 <span data-ttu-id="05280-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="05280-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05280-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="05280-110">Attributes</span></span>  
  
|<span data-ttu-id="05280-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="05280-111">Attribute</span></span>|<span data-ttu-id="05280-112">Popis</span><span class="sxs-lookup"><span data-stu-id="05280-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="05280-113">Logická hodnota, která určuje, zda jsou povoleny čítače výkonu pro diagnostické účely.</span><span class="sxs-lookup"><span data-stu-id="05280-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05280-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="05280-114">Child Elements</span></span>  
 <span data-ttu-id="05280-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="05280-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05280-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="05280-116">Parent Elements</span></span>  
  
|<span data-ttu-id="05280-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="05280-117">Element</span></span>|<span data-ttu-id="05280-118">Popis</span><span class="sxs-lookup"><span data-stu-id="05280-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05280-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="05280-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="05280-120">Obsahuje nastavení konfigurace pro naslouchací proces SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="05280-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05280-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05280-121">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
