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
ms.openlocfilehash: 31dd785c419d9a8e11eb23deabd2dfa71c4d6e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572343"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="ca435-102">Postupy: obnovení časových pásem ze vloženého prostředku</span><span class="sxs-lookup"><span data-stu-id="ca435-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="ca435-103">Toto téma popisuje postup obnovení časových pásem, které byly uloženy do souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="ca435-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="ca435-104">Informace a pokyny k ukládání časových pásem, najdete v části [postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="ca435-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="ca435-105">K deserializaci objektu TimeZoneInfo ze vloženého prostředku</span><span class="sxs-lookup"><span data-stu-id="ca435-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="ca435-106">Pokud mají být načteny časové pásmo není vlastní časové pásmo, pokuste se vytvořit instanci pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ca435-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="ca435-107">Vytváření instancí <xref:System.Resources.ResourceManager> objekt předáním plně kvalifikovaný název vloženého prostředku souboru a odkaz na sestavení, která obsahuje soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="ca435-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="ca435-108">Pokud nelze určit plně kvalifikovaný název souboru vložený prostředek, použijte [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) prozkoumat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca435-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="ca435-109">`.mresource` Položka identifikuje prostředek.</span><span class="sxs-lookup"><span data-stu-id="ca435-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="ca435-110">V tomto příkladu plně kvalifikovaný název prostředku je `SerializeTimeZoneData.SerializedTimeZones`.</span><span class="sxs-lookup"><span data-stu-id="ca435-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="ca435-111">Pokud se soubor prostředků je vložen do stejného sestavení, která obsahuje kód pro vytvoření instance časové pásmo, můžete načíst odkaz na jeho voláním `static` (`Shared` v jazyce Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ca435-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="ca435-112">Pokud volání <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metoda selže, nebo pokud vlastní časové pásmo má být vytvořena instance, načíst řetězec, který obsahuje serializované časové pásmo voláním <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="ca435-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="ca435-113">Deserializovat údaje o časovém pásmu voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ca435-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="ca435-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca435-114">Example</span></span>

<span data-ttu-id="ca435-115">Následující příklad deserializuje <xref:System.TimeZoneInfo> objektu uloženého ve vloženém .NET XML souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="ca435-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="ca435-116">Tento kód ukazuje zpracování výjimek zajistit, aby <xref:System.TimeZoneInfo> nachází objekt požadované aplikací.</span><span class="sxs-lookup"><span data-stu-id="ca435-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="ca435-117">Nejprve se pokusí vytvořit instanci <xref:System.TimeZoneInfo> objekt načtením z registru pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ca435-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="ca435-118">Pokud nelze vytvořit instanci časové pásmo, načte kód z soubor vložený prostředek.</span><span class="sxs-lookup"><span data-stu-id="ca435-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="ca435-119">Protože data pro vlastní časových pásem (časových pásem vytvořené pomocí <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda) nejsou uložené v registru nevyvolá kód <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> k vytváření instancí časové pásmo pro Palmer Antarktida.</span><span class="sxs-lookup"><span data-stu-id="ca435-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="ca435-120">Místo toho okamžitě vypadá to, k souboru vložený prostředek načíst řetězec, který obsahuje data na časové pásmo, zavolá <xref:System.TimeZoneInfo.FromSerializedString%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ca435-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="ca435-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ca435-121">Compiling the code</span></span>

<span data-ttu-id="ca435-122">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ca435-122">This example requires:</span></span>

* <span data-ttu-id="ca435-123">Aby byl přidán odkaz na System.Windows.Forms.dll a System.Core.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="ca435-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="ca435-124">Aby byly importované následujících oborů názvů:</span><span class="sxs-lookup"><span data-stu-id="ca435-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="ca435-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca435-125">See also</span></span>

<span data-ttu-id="ca435-126">[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
[postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)</span><span class="sxs-lookup"><span data-stu-id="ca435-126">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)</span></span>
