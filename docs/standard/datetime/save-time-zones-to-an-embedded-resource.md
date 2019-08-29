---
title: 'Postupy: Ukládání časových pásem do integrovaného prostředku'
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
ms.openlocfilehash: 9ca39d989cc7bc16ec2678ba5fa53710899f3ac4
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107161"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="1c471-102">Postupy: Ukládání časových pásem do integrovaného prostředku</span><span class="sxs-lookup"><span data-stu-id="1c471-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="1c471-103">Aplikace pracující s časovým pásmem často vyžaduje přítomnost konkrétního časového pásma.</span><span class="sxs-lookup"><span data-stu-id="1c471-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="1c471-104">Vzhledem k tomu, že dostupnost jednotlivých <xref:System.TimeZoneInfo> objektů závisí na informacích uložených v registru místního systému, nemusí být k dispozici ani běžně dostupná časová pásma.</span><span class="sxs-lookup"><span data-stu-id="1c471-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="1c471-105">Kromě toho informace o vlastních časových pásmech, které jsou vytvořeny pomocí <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody, nejsou uloženy spolu s dalšími informacemi o časovém pásmu v registru.</span><span class="sxs-lookup"><span data-stu-id="1c471-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="1c471-106">Chcete-li zajistit, aby tato časová pásma byla k dispozici v případě potřeby, můžete je uložit jejich serializací a později je obnovit jejich deserializací.</span><span class="sxs-lookup"><span data-stu-id="1c471-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="1c471-107">K serializaci <xref:System.TimeZoneInfo> objektu obvykle dochází z aplikace pracující s časovým pásmem.</span><span class="sxs-lookup"><span data-stu-id="1c471-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="1c471-108">V závislosti na úložišti dat, které se používá pro <xref:System.TimeZoneInfo> blokování serializovaných objektů, může být data časového pásma serializována jako součást Instalační rutiny nebo Instalační rutiny (například když jsou data uložena v klíči aplikace registru) nebo jako součást rutiny, která spouští nástroj. před kompilací konečné aplikace (například když jsou serializovaná data uložena v souboru prostředků .NET XML (. resx)).</span><span class="sxs-lookup"><span data-stu-id="1c471-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="1c471-109">Kromě souboru prostředků, který je zkompilován s aplikací, lze použít několik dalších úložišť dat pro informace o časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="1c471-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="1c471-110">Patří mezi ně například:</span><span class="sxs-lookup"><span data-stu-id="1c471-110">These include the following:</span></span>

- <span data-ttu-id="1c471-111">Registr.</span><span class="sxs-lookup"><span data-stu-id="1c471-111">The registry.</span></span> <span data-ttu-id="1c471-112">Všimněte si, že aplikace by měla použít podklíče vlastního klíče aplikace k uložení dat vlastního časového pásma namísto použití podklíčů zón HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time.</span><span class="sxs-lookup"><span data-stu-id="1c471-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

- <span data-ttu-id="1c471-113">Konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="1c471-113">Configuration files.</span></span>

- <span data-ttu-id="1c471-114">Jiné systémové soubory.</span><span class="sxs-lookup"><span data-stu-id="1c471-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="1c471-115">Uložení časového pásma pomocí serializace do souboru. resx</span><span class="sxs-lookup"><span data-stu-id="1c471-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="1c471-116">Načtěte existující časové pásmo nebo vytvořte nové časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="1c471-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="1c471-117">Chcete-li načíst existující časové pásmo, [Přečtěte si téma How to: Přístup k předdefinovaným objektům](../../../docs/standard/datetime/access-utc-and-local.md) UTC a místnímu časovému pásmu a [postupy: Vytvoří instanci objektu](../../../docs/standard/datetime/instantiate-time-zone-info.md)TimeZoneInfo.</span><span class="sxs-lookup"><span data-stu-id="1c471-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="1c471-118">Chcete-li vytvořit nové časové pásmo, zavolejte jedno z přetížení <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1c471-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="1c471-119">Další informace najdete v tématu [jak: Vytváření časových pásem bez pravidel](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) úprav a [postupy: Vytváření časových pásem s pravidly](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)úpravy</span><span class="sxs-lookup"><span data-stu-id="1c471-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="1c471-120"><xref:System.TimeZoneInfo.ToSerializedString%2A> Zavolejte metodu pro vytvoření řetězce, který obsahuje data časového pásma.</span><span class="sxs-lookup"><span data-stu-id="1c471-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="1c471-121">Vytvořte instanci <xref:System.IO.StreamWriter> objektu zadáním názvu a volitelně cesty k souboru. resx konstruktoru třídy. <xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="1c471-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="1c471-122">Vytvořte instanci <xref:System.IO.StreamWriter> <xref:System.Resources.ResXResourceWriter> objektu předáním objektu konstruktoru třídy. <xref:System.Resources.ResXResourceWriter></span><span class="sxs-lookup"><span data-stu-id="1c471-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="1c471-123">Předat serializovanému řetězci časového pásma do <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="1c471-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="1c471-124">Volání <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="1c471-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="1c471-125">Volání <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="1c471-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="1c471-126">Zavřete objekt voláním jeho <xref:System.IO.StreamWriter.Close%2A>metody. <xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="1c471-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="1c471-127">Přidejte vygenerovaný soubor. resx do projektu aplikace Visual Studio aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c471-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="1c471-128">V okně **vlastnosti** v sadě Visual Studio se ujistěte, že vlastnost **Akce sestavení** souboru. resx je nastavená na **Integrovaný prostředek**.</span><span class="sxs-lookup"><span data-stu-id="1c471-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="1c471-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c471-129">Example</span></span>

<span data-ttu-id="1c471-130">Následující příklad serializace <xref:System.TimeZoneInfo> objektu, který představuje centrální standardní čas <xref:System.TimeZoneInfo> a objekt, který představuje stanici Palmer, Antarktida čas souboru prostředků .NET XML s názvem SerializedTimeZones. resx.</span><span class="sxs-lookup"><span data-stu-id="1c471-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="1c471-131">Střední běžný čas je obvykle definován v registru; Palmer stanice je Antarktida vlastním časovým pásmem.</span><span class="sxs-lookup"><span data-stu-id="1c471-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="1c471-132">Tento příklad serializace <xref:System.TimeZoneInfo> objekty tak, aby byly k dispozici v souboru prostředků v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="1c471-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="1c471-133">Vzhledem k tomu, že Metodapřidádosouboruprostředků.NETXMLúplnéinformaceohlavičce,nelzejipoužítkpřidáníprostředkůdoexistujícíhosouboru.<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1c471-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="1c471-134">Tento příklad zpracovává tuto kontrolu pomocí kontroly souboru SerializedTimeZones. resx a pokud existuje, ukládá všechny jeho prostředky jiné než dvě serializovaná časová pásma do obecného <xref:System.Collections.Generic.Dictionary%602> objektu.</span><span class="sxs-lookup"><span data-stu-id="1c471-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="1c471-135">Existující soubor se pak odstraní a stávající prostředky se přidají do nového souboru SerializedTimeZones. resx.</span><span class="sxs-lookup"><span data-stu-id="1c471-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="1c471-136">Do tohoto souboru jsou přidána také Serializovaná data časového pásma.</span><span class="sxs-lookup"><span data-stu-id="1c471-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="1c471-137">Pole klíče (nebo **Name**) prostředků nesmí obsahovat vložené mezery.</span><span class="sxs-lookup"><span data-stu-id="1c471-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="1c471-138"><xref:System.String.Replace%28System.String%2CSystem.String%29> Metoda je volána pro odebrání všech vložených mezer v identifikátorech časového pásma předtím, než jsou přiřazeny k souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="1c471-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="1c471-139">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="1c471-139">Compiling the code</span></span>

<span data-ttu-id="1c471-140">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1c471-140">This example requires:</span></span>

- <span data-ttu-id="1c471-141">Do projektu se přidá odkaz na System. Windows. Forms. dll a System. Core. dll.</span><span class="sxs-lookup"><span data-stu-id="1c471-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="1c471-142">Následující obory názvů se naimportují:</span><span class="sxs-lookup"><span data-stu-id="1c471-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="1c471-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c471-143">See also</span></span>

- [<span data-ttu-id="1c471-144">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="1c471-144">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="1c471-145">Přehled časových pásem</span><span class="sxs-lookup"><span data-stu-id="1c471-145">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="1c471-146">Postupy: Obnovení časových pásem z vloženého prostředku</span><span class="sxs-lookup"><span data-stu-id="1c471-146">How to: Restore time zones from an embedded resource</span></span>](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
