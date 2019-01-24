---
title: '&lt;dateTimeSerialization&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: b915a1e310d8375f70a09a9cd1f0e3051bda7895
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564952"
---
# <a name="ltdatetimeserializationgt-element"></a><span data-ttu-id="74534-102">&lt;dateTimeSerialization&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="74534-102">&lt;dateTimeSerialization&gt; Element</span></span>
<span data-ttu-id="74534-103">Určuje režim serializace <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="74534-103">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="74534-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="74534-104">\<configuration></span></span>  
<span data-ttu-id="74534-105">\<dateTimeSerialization ></span><span class="sxs-lookup"><span data-stu-id="74534-105">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74534-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74534-106">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74534-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="74534-107">Attributes and Elements</span></span>  
 <span data-ttu-id="74534-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="74534-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74534-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="74534-109">Attributes</span></span>  
  
|<span data-ttu-id="74534-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="74534-110">Attributes</span></span>|<span data-ttu-id="74534-111">Popis</span><span class="sxs-lookup"><span data-stu-id="74534-111">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="74534-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="74534-112">Optional.</span></span> <span data-ttu-id="74534-113">Určuje režim serializace.</span><span class="sxs-lookup"><span data-stu-id="74534-113">Specifies the serialization mode.</span></span> <span data-ttu-id="74534-114">Nastavte na jednu z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="74534-114">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="74534-115">Výchozí hodnota je **umožňujícím zpětnou transformaci**.</span><span class="sxs-lookup"><span data-stu-id="74534-115">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74534-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="74534-116">Child Elements</span></span>  
 <span data-ttu-id="74534-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="74534-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74534-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="74534-118">Parent Elements</span></span>  
  
|<span data-ttu-id="74534-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="74534-119">Element</span></span>|<span data-ttu-id="74534-120">Popis</span><span class="sxs-lookup"><span data-stu-id="74534-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74534-121">System.XML.Serialization</span><span class="sxs-lookup"><span data-stu-id="74534-121">system.xml.serialization</span></span>|<span data-ttu-id="74534-122">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="74534-122">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74534-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74534-123">Remarks</span></span>  
 <span data-ttu-id="74534-124">Ve verzích 1.0 a 1.1, 2.0 a novějších verzích rozhraní .NET Framework, když je tato vlastnost nastavená na **místní**, <xref:System.DateTime> objekty jsou vždy formátována jako místní čas.</span><span class="sxs-lookup"><span data-stu-id="74534-124">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="74534-125">Informace o zóně Místní čas je vždy součástí serializovaná data.</span><span class="sxs-lookup"><span data-stu-id="74534-125">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="74534-126">Tuto vlastnost nastavte na **místní** k zajištění kompatibility se staršími verzemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="74534-126">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="74534-127">Ve verzi 2.0 a novějších verzích rozhraní .NET Framework, které mají tato vlastnost nastavena na **umožňujícím zpětnou transformaci**, <xref:System.DateTime> objekty jsou prověřit, abyste zjistili, jestli jsou v místním, UTC nebo nespecifikované časového pásma.</span><span class="sxs-lookup"><span data-stu-id="74534-127">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="74534-128"><xref:System.DateTime> Objekty jsou pak serializován tak, že tyto informace je zachováno.</span><span class="sxs-lookup"><span data-stu-id="74534-128">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="74534-129">Toto je výchozí chování a je doporučené chování pro všechny nové aplikace, které nekomunikují ve starších verzích rozhraní.</span><span class="sxs-lookup"><span data-stu-id="74534-129">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74534-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74534-130">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="74534-131">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="74534-131">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="74534-132">\<schemaImporterExtensions> Element</span><span class="sxs-lookup"><span data-stu-id="74534-132">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="74534-133">\<Přidat > – Element pro \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="74534-133">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="74534-134">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="74534-134">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
