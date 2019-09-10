---
title: <add> z <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850554"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="2b6ad-102">\<Přidat > \<> backupList</span><span class="sxs-lookup"><span data-stu-id="2b6ad-102">\<add> of \<backupList></span></span>
<span data-ttu-id="2b6ad-103">Představuje prvek konfigurace, který definuje element záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2b6ad-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
<span data-ttu-id="2b6ad-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b6ad-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2b6ad-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2b6ad-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2b6ad-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="2b6ad-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="2b6ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupLists >** ](backuplists.md)</span><span class="sxs-lookup"><span data-stu-id="2b6ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)</span></span>\
<span data-ttu-id="2b6ad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupList >** ](backuplist.md)</span><span class="sxs-lookup"><span data-stu-id="2b6ad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)</span></span>\
<span data-ttu-id="2b6ad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="2b6ad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b6ad-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b6ad-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b6ad-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2b6ad-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2b6ad-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2b6ad-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b6ad-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="2b6ad-113">Attributes</span></span>  
  
|<span data-ttu-id="2b6ad-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="2b6ad-114">Attribute</span></span>|<span data-ttu-id="2b6ad-115">Popis</span><span class="sxs-lookup"><span data-stu-id="2b6ad-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b6ad-116">name</span><span class="sxs-lookup"><span data-stu-id="2b6ad-116">name</span></span>|<span data-ttu-id="2b6ad-117">Řetězec, který určuje název koncového bodu zálohy.</span><span class="sxs-lookup"><span data-stu-id="2b6ad-117">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b6ad-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2b6ad-118">Child Elements</span></span>  
 <span data-ttu-id="2b6ad-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="2b6ad-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b6ad-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2b6ad-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2b6ad-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="2b6ad-121">Element</span></span>|<span data-ttu-id="2b6ad-122">Popis</span><span class="sxs-lookup"><span data-stu-id="2b6ad-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b6ad-123">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="2b6ad-123">\<routing></span></span>](routing.md)|<span data-ttu-id="2b6ad-124">Obsahuje seznam koncových bodů, které by služba Směrování měla použít pro případ, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="2b6ad-124">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b6ad-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b6ad-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
