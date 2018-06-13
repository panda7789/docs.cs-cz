---
title: '&lt;dateTimeSerialization&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 5e48753b5e8383a1ad946a29636e30ef07ceee9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581726"
---
# <a name="ltdatetimeserializationgt-element"></a><span data-ttu-id="2109d-102">&lt;dateTimeSerialization&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="2109d-102">&lt;dateTimeSerialization&gt; Element</span></span>
<span data-ttu-id="2109d-103">Určuje režim serializace <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="2109d-103">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="2109d-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="2109d-104">\<configuration></span></span>  
<span data-ttu-id="2109d-105">\<dateTimeSerialization ></span><span class="sxs-lookup"><span data-stu-id="2109d-105">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2109d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2109d-106">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2109d-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2109d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2109d-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2109d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2109d-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="2109d-109">Attributes</span></span>  
  
|<span data-ttu-id="2109d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2109d-110">Attributes</span></span>|<span data-ttu-id="2109d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="2109d-111">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="2109d-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2109d-112">Optional.</span></span> <span data-ttu-id="2109d-113">Určuje režim serializace.</span><span class="sxs-lookup"><span data-stu-id="2109d-113">Specifies the serialization mode.</span></span> <span data-ttu-id="2109d-114">Nastavte na jednu z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2109d-114">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="2109d-115">Výchozí hodnota je **umožňujícím zpětnou transformaci**.</span><span class="sxs-lookup"><span data-stu-id="2109d-115">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2109d-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2109d-116">Child Elements</span></span>  
 <span data-ttu-id="2109d-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="2109d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2109d-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2109d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2109d-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="2109d-119">Element</span></span>|<span data-ttu-id="2109d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2109d-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2109d-121">System.XML.Serialization</span><span class="sxs-lookup"><span data-stu-id="2109d-121">system.xml.serialization</span></span>|<span data-ttu-id="2109d-122">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="2109d-122">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2109d-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2109d-123">Remarks</span></span>  
 <span data-ttu-id="2109d-124">Verze 1.0, 1.1, 2.0 nebo novější verze rozhraní .NET Framework, když je tato vlastnost nastavena na **místní**, <xref:System.DateTime> objekty jsou vždy formátovaný jako místní čas.</span><span class="sxs-lookup"><span data-stu-id="2109d-124">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="2109d-125">Informace o zóně Místní čas je vždy součástí serializovaná data.</span><span class="sxs-lookup"><span data-stu-id="2109d-125">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="2109d-126">Tuto vlastnost nastavit na **místní** pro zajištění kompatibility s starší verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2109d-126">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="2109d-127">Ve verzi 2.0 a novější verze rozhraní .NET Framework, které mají tuto vlastnost nastavit na **umožňujícím zpětnou transformaci**, <xref:System.DateTime> objekty jsou prověřit, abyste zjistili, jestli jsou v místní, UTC nebo neurčené časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="2109d-127">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="2109d-128"><xref:System.DateTime> Objekty jsou pak serializován tak, že tyto informace je zachováno.</span><span class="sxs-lookup"><span data-stu-id="2109d-128">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="2109d-129">Toto je výchozí chování a je doporučené chování pro všechny nové aplikace, které nekomunikují ve starších verzích rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2109d-129">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2109d-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="2109d-130">See Also</span></span>  
 <xref:System.DateTime>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="2109d-131">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="2109d-131">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="2109d-132">\<schemaImporterExtensions > elementu</span><span class="sxs-lookup"><span data-stu-id="2109d-132">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [<span data-ttu-id="2109d-133">\<Přidat > elementu pro \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="2109d-133">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [<span data-ttu-id="2109d-134">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="2109d-134">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
