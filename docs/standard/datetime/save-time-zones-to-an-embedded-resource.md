---
title: 'Postupy: ukládání časových pásem do vloženého prostředku'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 921874e774d18751c29db495dac1bc53d10cc8ad
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "44778624"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="8a5e4-102">Postupy: ukládání časových pásem do vloženého prostředku</span><span class="sxs-lookup"><span data-stu-id="8a5e4-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="8a5e4-103">S ohledem na časové pásmo aplikace často vyžaduje přítomnost konkrétní časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="8a5e4-104">Ale protože dostupnost jednotlivých <xref:System.TimeZoneInfo> objekty závisí na informace uložené v registru místního systému, dokonce i běžně k dispozici časových pásem nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="8a5e4-105">Kromě toho vytvořit instanci pomocí informací o vlastní časových pásmech <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody není uložen s další informace o časovém pásmu v registru.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="8a5e4-106">Aby se zajistilo, že tato časová pásma jsou k dispozici, když jsou potřeba, můžete uložit pomocí serializace je a později je obnovit pomocí jejich deserializaci.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="8a5e4-107">Obvykle k serializaci <xref:System.TimeZoneInfo> objekt vyskytuje kromě aplikace podporující službu časového pásma.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="8a5e4-108">V závislosti na datové úložiště používané pro uložení serializovaná <xref:System.TimeZoneInfo> objekty, časové pásmo dat může být serializován jako součást instalace nebo instalace rutina (například, když jsou data uložena v klíči registru), nebo v rámci obslužné rutiny, na kterém běží před posledním aplikace je kompilována (například když jsou serializovaná data uložená v souboru prostředku (RESX) .NET XML).</span><span class="sxs-lookup"><span data-stu-id="8a5e4-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="8a5e4-109">Kromě zdrojového souboru, který je zkompilován s aplikací lze použít několik dalších datových úložišť pro informace o časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="8a5e4-110">Patří mezi ně například:</span><span class="sxs-lookup"><span data-stu-id="8a5e4-110">These include the following:</span></span>

* <span data-ttu-id="8a5e4-111">V registru.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-111">The registry.</span></span> <span data-ttu-id="8a5e4-112">Všimněte si, že by měla aplikace použít podklíčů klíče vlastní aplikace k ukládání dat vlastní časové pásmo spíš než podklíčů HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time zóny.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

* <span data-ttu-id="8a5e4-113">Konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-113">Configuration files.</span></span>

* <span data-ttu-id="8a5e4-114">Další soubory systému.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="8a5e4-115">Chcete-li uložit časového pásma pomocí jeho serializace do souboru .resx</span><span class="sxs-lookup"><span data-stu-id="8a5e4-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="8a5e4-116">Načíst existující časové pásmo nebo vytvořte nové časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="8a5e4-117">Pokud chcete načíst existující časové pásmo, přečtěte si [postupy: přístup k předdefinované objekty UTC a lokálního časového pásma](../../../docs/standard/datetime/access-utc-and-local.md) a [postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="8a5e4-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="8a5e4-118">Chcete-li vytvořit nové časové pásmo, zavoláním jednoho z přetížení <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="8a5e4-119">Další informace najdete v tématu [postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) a [postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="8a5e4-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="8a5e4-120">Volání <xref:System.TimeZoneInfo.ToSerializedString%2A> metodu pro vytvoření řetězec obsahující časové pásmo data.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="8a5e4-121">Vytvořit instanci <xref:System.IO.StreamWriter> objekt tím, že poskytuje název a volitelně cestu k souboru .resx <xref:System.IO.StreamWriter> konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="8a5e4-122">Vytvořit instanci <xref:System.Resources.ResXResourceWriter> předáním objektu <xref:System.IO.StreamWriter> objektu <xref:System.Resources.ResXResourceWriter> konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="8a5e4-123">Předejte časové pásmo serializovaný řetězec, který má <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="8a5e4-124">Volání <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="8a5e4-125">Volání <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="8a5e4-126">Zavřít <xref:System.IO.StreamWriter> objektu voláním jeho <xref:System.IO.StreamWriter.Close%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="8a5e4-127">Vytvořený soubor .resx přidáte do projektu aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="8a5e4-128">Použití **vlastnosti** okna v sadě Visual Studio, ujistěte se, že soubor .resx **akce sestavení** je nastavena na **integrovaný prostředek**.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="8a5e4-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a5e4-129">Example</span></span>

<span data-ttu-id="8a5e4-130">Následující příklad serializuje <xref:System.TimeZoneInfo> objekt, který představuje střed (běžný čas) a <xref:System.TimeZoneInfo> objekt, který představuje soubor prostředků .NET XML, který je pojmenován SerializedTimeZones.resx Palmera, Antarktida čas.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="8a5e4-131">Střední (běžný čas) je obvykle definováno v registru. Palmera, Antarktida je vlastní časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="8a5e4-132">Tento příklad serializuje <xref:System.TimeZoneInfo> objekty tak, aby byly k dispozici v souboru prostředků v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="8a5e4-133">Vzhledem k tomu, <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metoda přidá úplné informace hlavičky v souboru prostředků .NET XML, nelze přidat prostředky do existujícího souboru.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="8a5e4-134">V příkladu to kontrolou souboru SerializedTimeZones.resx a, pokud existuje, uložení všech jeho prostředků jiných než dva serializovaná časových pásmech obecný <xref:System.Collections.Generic.Dictionary%602> objektu.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="8a5e4-135">Pak odstraní existující soubor a stávající prostředky se přidají do nového souboru SerializedTimeZones.resx.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="8a5e4-136">Serializovaná časové pásmo data je také přidána do tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="8a5e4-137">Klíč (nebo **název**) prostředků by neměly obsahovat mezery.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="8a5e4-138"><xref:System.String.Replace%28System.String%2CSystem.String%29> Metoda je volána k odebrání všech vložených mezer v identifikátory časových pásem před přiřazením do souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="8a5e4-139">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="8a5e4-139">Compiling the code</span></span>

<span data-ttu-id="8a5e4-140">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="8a5e4-140">This example requires:</span></span>

* <span data-ttu-id="8a5e4-141">Aby byl odkaz na System.Windows.Forms.dll a System.Core.dll přidán do projektu.</span><span class="sxs-lookup"><span data-stu-id="8a5e4-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="8a5e4-142">Aby byly importované následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="8a5e4-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="8a5e4-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a5e4-143">See also</span></span>

* [<span data-ttu-id="8a5e4-144">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="8a5e4-144">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
* [<span data-ttu-id="8a5e4-145">Přehled časových pásem</span><span class="sxs-lookup"><span data-stu-id="8a5e4-145">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
* [<span data-ttu-id="8a5e4-146">Postupy: Obnovení časových pásem z integrovaného prostředku</span><span class="sxs-lookup"><span data-stu-id="8a5e4-146">How to: Restore time zones from an embedded resource</span></span>](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
