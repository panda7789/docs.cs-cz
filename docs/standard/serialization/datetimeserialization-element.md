---
title: Element <dateTimeSerialization>
description: Tento článek popisuje <dateTimeSerialization> prvek, který určuje režim serializace objektů typu DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 652a88e25f59cd905e47ef71351e47e67f375286
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375829"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="2bf22-103">\<dateTimeSerialization – element></span><span class="sxs-lookup"><span data-stu-id="2bf22-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="2bf22-104">Určuje režim serializace <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="2bf22-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="2bf22-105">\<> konfigurace</span><span class="sxs-lookup"><span data-stu-id="2bf22-105">\<configuration></span></span>  
<span data-ttu-id="2bf22-106">\<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="2bf22-106">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bf22-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bf22-107">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bf22-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2bf22-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2bf22-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2bf22-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bf22-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2bf22-110">Attributes</span></span>  
  
|<span data-ttu-id="2bf22-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2bf22-111">Attributes</span></span>|<span data-ttu-id="2bf22-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2bf22-112">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="2bf22-113">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="2bf22-113">Optional.</span></span> <span data-ttu-id="2bf22-114">Určuje režim serializace.</span><span class="sxs-lookup"><span data-stu-id="2bf22-114">Specifies the serialization mode.</span></span> <span data-ttu-id="2bf22-115">Nastavte na jednu z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2bf22-115">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="2bf22-116">Výchozí hodnota je **zpáteční**.</span><span class="sxs-lookup"><span data-stu-id="2bf22-116">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bf22-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2bf22-117">Child Elements</span></span>  
 <span data-ttu-id="2bf22-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="2bf22-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2bf22-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2bf22-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2bf22-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="2bf22-120">Element</span></span>|<span data-ttu-id="2bf22-121">Popis</span><span class="sxs-lookup"><span data-stu-id="2bf22-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2bf22-122">System.XML.Serialization</span><span class="sxs-lookup"><span data-stu-id="2bf22-122">system.xml.serialization</span></span>|<span data-ttu-id="2bf22-123">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="2bf22-123">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bf22-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bf22-124">Remarks</span></span>  
 <span data-ttu-id="2bf22-125">V verzích 1,0, 1,1, 2,0 a novějších .NET Framework platí, že pokud je tato vlastnost nastavena na **místní**, <xref:System.DateTime> objekty jsou vždy formátovány jako místní čas.</span><span class="sxs-lookup"><span data-stu-id="2bf22-125">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="2bf22-126">Informace o zóně Místní čas je vždy součástí serializovaná data.</span><span class="sxs-lookup"><span data-stu-id="2bf22-126">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="2bf22-127">Nastavte tuto vlastnost na **místní** , aby se zajistila kompatibilita se staršími verzemi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2bf22-127">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="2bf22-128">Ve verzi 2,0 a novějších .NET Framework, které mají tuto vlastnost nastavenou na hodnotu **zpětného převodu**, <xref:System.DateTime> jsou zkontrolovány objekty za účelem zjištění, zda jsou v místním, UTC nebo neurčeném časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="2bf22-128">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="2bf22-129"><xref:System.DateTime> Objekty jsou pak serializován tak, že tyto informace je zachováno.</span><span class="sxs-lookup"><span data-stu-id="2bf22-129">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="2bf22-130">Toto je výchozí chování a je doporučené chování pro všechny nové aplikace, které nekomunikují ve starších verzích rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2bf22-130">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf22-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bf22-131">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="2bf22-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="2bf22-132">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="2bf22-133">\<schemaImporterExtensions – element></span><span class="sxs-lookup"><span data-stu-id="2bf22-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="2bf22-134">\<Přidat> element pro \<>schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="2bf22-134">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="2bf22-135">\<System. XML. Serialization – element></span><span class="sxs-lookup"><span data-stu-id="2bf22-135">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
