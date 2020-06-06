---
title: <add> z <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850554"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="fc0f2-102">\<add> z \<backupList></span><span class="sxs-lookup"><span data-stu-id="fc0f2-102">\<add> of \<backupList></span></span>
<span data-ttu-id="fc0f2-103">Představuje prvek konfigurace, který definuje element záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="fc0f2-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="fc0f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc0f2-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc0f2-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fc0f2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fc0f2-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fc0f2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc0f2-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="fc0f2-107">Attributes</span></span>  
  
|<span data-ttu-id="fc0f2-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="fc0f2-108">Attribute</span></span>|<span data-ttu-id="fc0f2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fc0f2-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc0f2-110">name</span><span class="sxs-lookup"><span data-stu-id="fc0f2-110">name</span></span>|<span data-ttu-id="fc0f2-111">Řetězec, který určuje název koncového bodu zálohy.</span><span class="sxs-lookup"><span data-stu-id="fc0f2-111">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc0f2-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fc0f2-112">Child Elements</span></span>  
 <span data-ttu-id="fc0f2-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="fc0f2-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc0f2-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fc0f2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="fc0f2-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="fc0f2-115">Element</span></span>|<span data-ttu-id="fc0f2-116">Description</span><span class="sxs-lookup"><span data-stu-id="fc0f2-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="fc0f2-117">Obsahuje seznam koncových bodů, které by služba Směrování měla použít pro případ, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="fc0f2-117">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc0f2-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc0f2-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
