---
title: 'Postupy: Obnovení časových pásem z integrovaného prostředku'
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
ms.openlocfilehash: 98813bf6685be78d33ebd5cc5e8c07a61a811c25
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106751"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="191ec-102">Postupy: Obnovení časových pásem z integrovaného prostředku</span><span class="sxs-lookup"><span data-stu-id="191ec-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="191ec-103">Toto téma popisuje, jak obnovit časová pásma uložená v souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="191ec-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="191ec-104">Informace a pokyny k ukládání časových pásem naleznete v tématu [How to: Uloží časová pásma do vloženého](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)prostředku.</span><span class="sxs-lookup"><span data-stu-id="191ec-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="191ec-105">Deserializace objektu TimeZoneInfo od vloženého prostředku</span><span class="sxs-lookup"><span data-stu-id="191ec-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="191ec-106">Pokud časové pásmo, které má být načteno, není vlastním časovým pásmem, zkuste vytvořit instanci pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="191ec-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="191ec-107">Vytvořte instanci objektu předáním plně kvalifikovaného názvu vloženého souboru prostředků a odkazu na sestavení, které obsahuje soubor prostředků. <xref:System.Resources.ResourceManager></span><span class="sxs-lookup"><span data-stu-id="191ec-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="191ec-108">Pokud nemůžete určit plně kvalifikovaný název vloženého souboru prostředků, použijte nástroj [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) a prověřte manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="191ec-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="191ec-109">`.mresource` Položka identifikuje prostředek.</span><span class="sxs-lookup"><span data-stu-id="191ec-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="191ec-110">V tomto příkladu je `SerializeTimeZoneData.SerializedTimeZones`plně kvalifikovaný název prostředku.</span><span class="sxs-lookup"><span data-stu-id="191ec-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="191ec-111">Pokud je soubor prostředků vložen do stejného sestavení, které obsahuje kód pro vytvoření instance časového pásma, můžete na něj získat odkaz voláním `static` metody (`Shared` v Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> .</span><span class="sxs-lookup"><span data-stu-id="191ec-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="191ec-112">Pokud volání <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody dojde k chybě nebo pokud je vytvořena instance vlastního časového pásma, načtěte řetězec, který obsahuje serializované časové pásmo <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="191ec-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="191ec-113">Deserializace dat časového pásma voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="191ec-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="191ec-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="191ec-114">Example</span></span>

<span data-ttu-id="191ec-115">Následující příklad deserializace <xref:System.TimeZoneInfo> objekt uložený v vloženém souboru prostředků .NET XML.</span><span class="sxs-lookup"><span data-stu-id="191ec-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="191ec-116">Tento kód ilustruje zpracování výjimek, aby bylo <xref:System.TimeZoneInfo> zajištěno, že objekt vyžadovaný aplikací je přítomen.</span><span class="sxs-lookup"><span data-stu-id="191ec-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="191ec-117">Nejprve se pokusí vytvořit instanci <xref:System.TimeZoneInfo> objektu jejich načtením z registru <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="191ec-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="191ec-118">Pokud časové pásmo nelze vytvořit, kód ho načte z vloženého souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="191ec-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="191ec-119">Vzhledem k tomu, že data pro vlastní časová pásma (časová <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> pásma vytvořená pomocí metody) nejsou uložena v registru, kód <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> nevolá pro vytvoření instance časového pásma pro Palmer, Antarktida.</span><span class="sxs-lookup"><span data-stu-id="191ec-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="191ec-120">Místo toho se hned vyhledá vložený soubor prostředků, aby se načetl řetězec, který obsahuje data časového pásma před voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="191ec-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="191ec-121">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="191ec-121">Compiling the code</span></span>

<span data-ttu-id="191ec-122">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="191ec-122">This example requires:</span></span>

- <span data-ttu-id="191ec-123">Do projektu se přidá odkaz na System. Windows. Forms. dll a System. Core. dll.</span><span class="sxs-lookup"><span data-stu-id="191ec-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="191ec-124">Následující obory názvů se naimportují:</span><span class="sxs-lookup"><span data-stu-id="191ec-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="191ec-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="191ec-125">See also</span></span>

- [<span data-ttu-id="191ec-126">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="191ec-126">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="191ec-127">Přehled časových pásem</span><span class="sxs-lookup"><span data-stu-id="191ec-127">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="191ec-128">Postupy: Uložit časová pásma do vloženého prostředku</span><span class="sxs-lookup"><span data-stu-id="191ec-128">How to: Save time zones to an embedded resource</span></span>](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
