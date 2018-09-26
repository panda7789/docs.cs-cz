---
title: 'Postupy: obnovení časových pásem ze vloženého prostředku'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99d38b336b5e655dd1c96682eec90c5fbe8469d6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077392"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="ba1ba-102">Postupy: obnovení časových pásem ze vloženého prostředku</span><span class="sxs-lookup"><span data-stu-id="ba1ba-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="ba1ba-103">Toto téma popisuje postup při obnovení časových pásem, které byly uloženy do souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="ba1ba-104">Informace a pokyny k ukládání časových pásem najdete v tématu [postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="ba1ba-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="ba1ba-105">K deserializaci instance objektu TimeZoneInfo ze vloženého prostředku</span><span class="sxs-lookup"><span data-stu-id="ba1ba-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="ba1ba-106">Pokud se časové pásmo, které se mají načíst není vlastní časové pásmo, pokuste se vytvořit instanci pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="ba1ba-107">Vytvořit instanci <xref:System.Resources.ResourceManager> objekt předáním plně kvalifikovaný název souboru vložené zdroje a odkaz na sestavení, které obsahuje soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="ba1ba-108">Pokud nelze určit plně kvalifikovaný název souboru vloženého prostředku, použijte [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) prozkoumat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="ba1ba-109">`.mresource` Položka identifikuje prostředek.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="ba1ba-110">V tomto příkladu je plně kvalifikovaný název prostředku `SerializeTimeZoneData.SerializedTimeZones`.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="ba1ba-111">Pokud soubor prostředků je vložený ve stejném sestavení, která obsahuje kód pro vytvoření instance časové pásmo, můžete načíst na ni odkaz pomocí volání `static` (`Shared` v jazyce Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="ba1ba-112">Pokud volání <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metoda selže, nebo pokud je vlastní časové pásmo má být vytvořena, načíst řetězec, který obsahuje serializovaná časové pásmo voláním <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="ba1ba-113">Zrušit serializaci dat časové pásmo voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="ba1ba-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba1ba-114">Example</span></span>

<span data-ttu-id="ba1ba-115">Následující příklad deserializuje <xref:System.TimeZoneInfo> objekt uložený v souboru vložený prostředek .NET XML.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="ba1ba-116">Tento kód ukazuje zpracování výjimek a zkontrolujte, že <xref:System.TimeZoneInfo> objekt vyžadované aplikací je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="ba1ba-117">Nejprve se pokusí vytvořit instanci <xref:System.TimeZoneInfo> objekt načtením z registru pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="ba1ba-118">Pokud nelze vytvořit instanci časové pásmo, kód načte z vloženého zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="ba1ba-119">Protože data pro vlastní časových pásem (časových pásem vytvořit instanci pomocí <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda) nejsou uložené v registru, nevolá kód <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pro vytvoření instance časové pásmo pro Palmer, Antarktida.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="ba1ba-120">Místo toho okamžitě vypadá do souboru integrovaný prostředek, aby se načetl řetězec obsahující časové pásmo data před voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="ba1ba-121">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="ba1ba-121">Compiling the code</span></span>

<span data-ttu-id="ba1ba-122">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ba1ba-122">This example requires:</span></span>

* <span data-ttu-id="ba1ba-123">Aby byl odkaz na System.Windows.Forms.dll a System.Core.dll přidán do projektu.</span><span class="sxs-lookup"><span data-stu-id="ba1ba-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="ba1ba-124">Aby byly importované následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="ba1ba-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="ba1ba-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba1ba-125">See also</span></span>

* [<span data-ttu-id="ba1ba-126">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="ba1ba-126">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
* [<span data-ttu-id="ba1ba-127">Přehled časových pásem</span><span class="sxs-lookup"><span data-stu-id="ba1ba-127">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
* [<span data-ttu-id="ba1ba-128">Postupy: Ukládání časových pásem do integrovaného prostředku</span><span class="sxs-lookup"><span data-stu-id="ba1ba-128">How to: Save time zones to an embedded resource</span></span>](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
