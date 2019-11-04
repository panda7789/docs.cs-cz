---
title: Element <dateTimeSerialization>
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 180a4942dd4b701b56fe4788d5f8cd8607faaedd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459260"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="d160a-102">\<element > dateTimeSerialization</span><span class="sxs-lookup"><span data-stu-id="d160a-102">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="d160a-103">Určuje režim serializace <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="d160a-103">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="d160a-104">Konfigurace \<</span><span class="sxs-lookup"><span data-stu-id="d160a-104">\<configuration></span></span>  
<span data-ttu-id="d160a-105">\<dateTimeSerialization ></span><span class="sxs-lookup"><span data-stu-id="d160a-105">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d160a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d160a-106">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d160a-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d160a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d160a-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d160a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d160a-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="d160a-109">Attributes</span></span>  
  
|<span data-ttu-id="d160a-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d160a-110">Attributes</span></span>|<span data-ttu-id="d160a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="d160a-111">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="d160a-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d160a-112">Optional.</span></span> <span data-ttu-id="d160a-113">Určuje režim serializace.</span><span class="sxs-lookup"><span data-stu-id="d160a-113">Specifies the serialization mode.</span></span> <span data-ttu-id="d160a-114">Nastavte na jednu z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d160a-114">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="d160a-115">Výchozí hodnota je **zpáteční**.</span><span class="sxs-lookup"><span data-stu-id="d160a-115">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d160a-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d160a-116">Child Elements</span></span>  
 <span data-ttu-id="d160a-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="d160a-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d160a-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d160a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d160a-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="d160a-119">Element</span></span>|<span data-ttu-id="d160a-120">Popis</span><span class="sxs-lookup"><span data-stu-id="d160a-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d160a-121">System.XML.Serialization</span><span class="sxs-lookup"><span data-stu-id="d160a-121">system.xml.serialization</span></span>|<span data-ttu-id="d160a-122">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="d160a-122">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d160a-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d160a-123">Remarks</span></span>  
 <span data-ttu-id="d160a-124">Ve verzích 1,0, 1,1, 2,0 a novějších .NET Framework platí, že pokud je tato vlastnost nastavená na **místní**, <xref:System.DateTime> objekty se vždycky naformátují jako místní čas.</span><span class="sxs-lookup"><span data-stu-id="d160a-124">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="d160a-125">Informace o zóně Místní čas je vždy součástí serializovaná data.</span><span class="sxs-lookup"><span data-stu-id="d160a-125">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="d160a-126">Nastavte tuto vlastnost na **místní** , aby se zajistila kompatibilita se staršími verzemi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d160a-126">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d160a-127">Ve verzi 2,0 a novějších .NET Framework, které mají tuto vlastnost nastavenou na hodnotu **zpětného převodu**, se <xref:System.DateTime> objekty zkontrolují za účelem zjištění, zda jsou v místním, UTC nebo neurčeném časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="d160a-127">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="d160a-128"><xref:System.DateTime> Objekty jsou pak serializován tak, že tyto informace je zachováno.</span><span class="sxs-lookup"><span data-stu-id="d160a-128">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="d160a-129">Toto je výchozí chování a je doporučené chování pro všechny nové aplikace, které nekomunikují ve starších verzích rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d160a-129">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d160a-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d160a-130">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="d160a-131">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d160a-131">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="d160a-132">\<element > schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="d160a-132">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="d160a-133">\<přidat > element pro \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="d160a-133">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="d160a-134">\<element System. XML. Serialization > elementu</span><span class="sxs-lookup"><span data-stu-id="d160a-134">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
