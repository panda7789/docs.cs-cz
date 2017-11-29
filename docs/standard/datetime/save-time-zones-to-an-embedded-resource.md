---
title: "Postupy: ukládání časových pásem do vloženého prostředku"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 96dd3f0a3ed27a9e09c62f3ad4f450ced5a8e644
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="1dc68-102">Postupy: ukládání časových pásem do vloženého prostředku</span><span class="sxs-lookup"><span data-stu-id="1dc68-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="1dc68-103">Časová pásma si aplikace často vyžaduje přítomnost konkrétní časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="1dc68-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="1dc68-104">Ale protože dostupnost individuální <xref:System.TimeZoneInfo> objekty závisí na informace uložené v registru místního systému, dokonce i běžně k dispozici časových pásem nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1dc68-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="1dc68-105">Kromě toho se informace o vlastních časových pásmech vytvořené pomocí <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda není uložen s další informace o časovém pásmu v registru.</span><span class="sxs-lookup"><span data-stu-id="1dc68-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="1dc68-106">K zajištění, že tato časová pásma jsou k dispozici, když jsou potřeba, můžete je uložit pomocí jejich serializace a později je obnovit pomocí jejich rekonstrukce.</span><span class="sxs-lookup"><span data-stu-id="1dc68-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="1dc68-107">Obvykle k serializaci <xref:System.TimeZoneInfo> objekt dochází mimo časové pásmo s deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="1dc68-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="1dc68-108">V závislosti na datové úložiště používané pro udržení serializovaných <xref:System.TimeZoneInfo> objekty, časové pásmo dat může serializovat jako součást instalace nebo instalace rutiny (například když jsou data uložená v klíči registru), nebo jako součást obslužné rutiny, která spouští před posledním aplikace kompiluje (například když serializovaná data uložena v souboru prostředků (RESX) .NET XML).</span><span class="sxs-lookup"><span data-stu-id="1dc68-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="1dc68-109">Kromě souboru prostředků, který se zkompiluje s aplikací můžete použít několik dalších datových úložišť pro informace o časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="1dc68-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="1dc68-110">Patří mezi ně například:</span><span class="sxs-lookup"><span data-stu-id="1dc68-110">These include the following:</span></span>

* <span data-ttu-id="1dc68-111">V registru.</span><span class="sxs-lookup"><span data-stu-id="1dc68-111">The registry.</span></span> <span data-ttu-id="1dc68-112">Upozorňujeme, že aplikace by měl použít podklíčů svůj vlastní klíč aplikace pro ukládání dat vlastní časového pásma, nikoli pomocí podklíče HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time zón.</span><span class="sxs-lookup"><span data-stu-id="1dc68-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

* <span data-ttu-id="1dc68-113">Konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="1dc68-113">Configuration files.</span></span>

* <span data-ttu-id="1dc68-114">Další soubory systému.</span><span class="sxs-lookup"><span data-stu-id="1dc68-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="1dc68-115">Uložte časové pásmo serializací do souboru RESX</span><span class="sxs-lookup"><span data-stu-id="1dc68-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="1dc68-116">Načtení existující časového pásma nebo vytvořte nové časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="1dc68-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="1dc68-117">Načíst existující časové pásmo, najdete v části [postupy: přístup k místním ČASEM a předdefinované objekty pásem](../../../docs/standard/datetime/access-utc-and-local.md) a [postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="1dc68-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="1dc68-118">Pokud chcete vytvořit nové časové pásmo, volání jednoho z přetížení <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1dc68-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="1dc68-119">Další informace najdete v tématu [postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) a [postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="1dc68-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="1dc68-120">Volání <xref:System.TimeZoneInfo.ToSerializedString%2A> metodu pro vytvoření řetězec, který obsahuje data na časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="1dc68-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="1dc68-121">Vytváření instancí <xref:System.IO.StreamWriter> objekt tím, že poskytuje název a volitelně cestu k souboru .resx <xref:System.IO.StreamWriter> konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="1dc68-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="1dc68-122">Vytváření instancí <xref:System.Resources.ResXResourceWriter> objekt předáním <xref:System.IO.StreamWriter> do objektu <xref:System.Resources.ResXResourceWriter> konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="1dc68-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="1dc68-123">Předejte časové pásmo serializovaný řetězec, který má <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="1dc68-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="1dc68-124">Volání <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="1dc68-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="1dc68-125">Volání <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="1dc68-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="1dc68-126">Zavřít <xref:System.IO.StreamWriter> objekt voláním jeho <xref:System.IO.StreamWriter.Close%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1dc68-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="1dc68-127">Vytvořený soubor .resx přidejte do projektu aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1dc68-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="1dc68-128">Pomocí **vlastnosti** oken v sadě Visual Studio, ujistěte se, že soubor .resx **akce sestavení** je nastavena na **vložený prostředek**.</span><span class="sxs-lookup"><span data-stu-id="1dc68-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="1dc68-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="1dc68-129">Example</span></span>

<span data-ttu-id="1dc68-130">V následujícím příkladu jsou <xref:System.TimeZoneInfo> objekt, který představuje čas a <xref:System.TimeZoneInfo> objekt, který reprezentuje Palmer stanice, Antarktida čas do souboru .NET XML prostředků s názvem SerializedTimeZones.resx.</span><span class="sxs-lookup"><span data-stu-id="1dc68-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="1dc68-131">Centrální běžný čas je obvykle definováno v registru; Stanice Palmer, Antarktida je vlastní časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="1dc68-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="1dc68-132">Tento příklad serializuje <xref:System.TimeZoneInfo> objekty tak, aby byly k dispozici v souboru prostředků v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="1dc68-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="1dc68-133">Protože <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metoda přidá do souboru .NET XML prostředků úplné informace hlavičky, nelze jej použít chcete přidat prostředky do existující soubor.</span><span class="sxs-lookup"><span data-stu-id="1dc68-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="1dc68-134">V příkladu to kontrolou souboru SerializedTimeZones.resx a, pokud existuje, všechny její prostředky uložení jiných než dva serializovaná časových pásem s obecným <xref:System.Collections.Generic.Dictionary%602> objektu.</span><span class="sxs-lookup"><span data-stu-id="1dc68-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="1dc68-135">Odstraní existující soubor a existující prostředky jsou přidány do nového souboru SerializedTimeZones.resx.</span><span class="sxs-lookup"><span data-stu-id="1dc68-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="1dc68-136">Data serializovaná časové pásmo je taky přidaná do tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="1dc68-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="1dc68-137">Klíč (nebo **název**) prostředků nesmí obsahovat mezery.</span><span class="sxs-lookup"><span data-stu-id="1dc68-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="1dc68-138"><xref:System.String.Replace%28System.String%2CSystem.String%29> Metoda je volána před jsou přiřazeny k souboru prostředků odeberte všechny mezery v identifikátory časových pásem.</span><span class="sxs-lookup"><span data-stu-id="1dc68-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="1dc68-139">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1dc68-139">Compiling the code</span></span>

<span data-ttu-id="1dc68-140">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1dc68-140">This example requires:</span></span>

* <span data-ttu-id="1dc68-141">Aby byl přidán odkaz na System.Windows.Forms.dll a System.Core.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="1dc68-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="1dc68-142">Aby byly importované následujících oborů názvů:</span><span class="sxs-lookup"><span data-stu-id="1dc68-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="1dc68-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="1dc68-143">See also</span></span>

<span data-ttu-id="1dc68-144">[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
[postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)</span><span class="sxs-lookup"><span data-stu-id="1dc68-144">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)</span></span>
