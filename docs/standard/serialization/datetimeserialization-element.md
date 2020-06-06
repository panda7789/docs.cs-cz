---
title: Element <dateTimeSerialization>
description: Tento článek popisuje <dateTimeSerialization> prvek, který určuje režim serializace objektů typu DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: a2684ab72c1fb109d711e333e01836d3399caf86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289639"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="634be-103">Element \<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="634be-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="634be-104">Určuje režim serializace <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="634be-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="634be-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="634be-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="634be-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="634be-106">Attributes and Elements</span></span>  
 <span data-ttu-id="634be-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="634be-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="634be-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="634be-108">Attributes</span></span>  
  
|<span data-ttu-id="634be-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="634be-109">Attributes</span></span>|<span data-ttu-id="634be-110">Description</span><span class="sxs-lookup"><span data-stu-id="634be-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="634be-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="634be-111">Optional.</span></span> <span data-ttu-id="634be-112">Určuje režim serializace.</span><span class="sxs-lookup"><span data-stu-id="634be-112">Specifies the serialization mode.</span></span> <span data-ttu-id="634be-113">Nastavte na jednu z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="634be-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="634be-114">Výchozí hodnota je **zpáteční**.</span><span class="sxs-lookup"><span data-stu-id="634be-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="634be-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="634be-115">Child Elements</span></span>  
 <span data-ttu-id="634be-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="634be-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="634be-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="634be-117">Parent Elements</span></span>  
  
|<span data-ttu-id="634be-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="634be-118">Element</span></span>|<span data-ttu-id="634be-119">Description</span><span class="sxs-lookup"><span data-stu-id="634be-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="634be-120">System.XML.Serialization</span><span class="sxs-lookup"><span data-stu-id="634be-120">system.xml.serialization</span></span>|<span data-ttu-id="634be-121">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="634be-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="634be-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="634be-122">Remarks</span></span>  
 <span data-ttu-id="634be-123">V verzích 1,0, 1,1, 2,0 a novějších .NET Framework platí, že pokud je tato vlastnost nastavena na **místní**, <xref:System.DateTime> objekty jsou vždy formátovány jako místní čas.</span><span class="sxs-lookup"><span data-stu-id="634be-123">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="634be-124">Informace o zóně Místní čas je vždy součástí serializovaná data.</span><span class="sxs-lookup"><span data-stu-id="634be-124">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="634be-125">Nastavte tuto vlastnost na **místní** , aby se zajistila kompatibilita se staršími verzemi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="634be-125">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="634be-126">Ve verzi 2,0 a novějších .NET Framework, které mají tuto vlastnost nastavenou na hodnotu **zpětného převodu**, <xref:System.DateTime> jsou zkontrolovány objekty za účelem zjištění, zda jsou v místním, UTC nebo neurčeném časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="634be-126">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="634be-127"><xref:System.DateTime> Objekty jsou pak serializován tak, že tyto informace je zachováno.</span><span class="sxs-lookup"><span data-stu-id="634be-127">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="634be-128">Toto je výchozí chování a je doporučené chování pro všechny nové aplikace, které nekomunikují ve starších verzích rozhraní.</span><span class="sxs-lookup"><span data-stu-id="634be-128">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="634be-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="634be-129">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="634be-130">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="634be-130">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="634be-131">\<schemaImporterExtensions>Objekt</span><span class="sxs-lookup"><span data-stu-id="634be-131">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="634be-132">\<add>Element pro\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="634be-132">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="634be-133">\<system.xml.serialization>Objekt</span><span class="sxs-lookup"><span data-stu-id="634be-133">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
