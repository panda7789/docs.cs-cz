---
title: <diagnostics> pro aktivaci
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 30456963a7d74a93e39bb1fddc0910daae97f039
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203805"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="a6fed-102">\<Diagnostika > pro aktivaci</span><span class="sxs-lookup"><span data-stu-id="a6fed-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="a6fed-103">Nakonfiguruje funkce diagnostiky Windows Communication Foundation (WCF) naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="a6fed-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="a6fed-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="a6fed-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="a6fed-105">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="a6fed-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6fed-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6fed-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="a6fed-107">Type</span><span class="sxs-lookup"><span data-stu-id="a6fed-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6fed-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a6fed-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a6fed-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a6fed-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6fed-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a6fed-110">Attributes</span></span>  
  
|<span data-ttu-id="a6fed-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a6fed-111">Attribute</span></span>|<span data-ttu-id="a6fed-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a6fed-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="a6fed-113">Logická hodnota, která určuje, zda jsou povoleny čítače výkonu pro diagnostické účely.</span><span class="sxs-lookup"><span data-stu-id="a6fed-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6fed-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a6fed-114">Child Elements</span></span>  
 <span data-ttu-id="a6fed-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="a6fed-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6fed-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a6fed-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a6fed-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6fed-117">Element</span></span>|<span data-ttu-id="a6fed-118">Popis</span><span class="sxs-lookup"><span data-stu-id="a6fed-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6fed-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="a6fed-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="a6fed-120">Obsahuje nastavení konfigurace pro naslouchací proces SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="a6fed-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6fed-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6fed-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
