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
ms.openlocfilehash: b1cece13c88b3a49c9c4c90045a07dd009d4282d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281320"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="3ff17-102">Postupy: Obnovení časových pásem z integrovaného prostředku</span><span class="sxs-lookup"><span data-stu-id="3ff17-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="3ff17-103">Toto téma popisuje, jak obnovit časová pásma uložená v souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="3ff17-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="3ff17-104">Informace a pokyny k ukládání časových pásem najdete v tématu [Postupy: ukládání časových pásem do vloženého prostředku](save-time-zones-to-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="3ff17-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="3ff17-105">Deserializace objektu TimeZoneInfo od vloženého prostředku</span><span class="sxs-lookup"><span data-stu-id="3ff17-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="3ff17-106">Pokud časové pásmo, které má být načteno, není vlastním časovým pásmem, zkuste vytvořit instanci pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3ff17-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="3ff17-107">Vytvořte instanci <xref:System.Resources.ResourceManager> objektu předáním plně kvalifikovaného názvu vloženého souboru prostředků a odkazu na sestavení, které obsahuje soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="3ff17-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="3ff17-108">Pokud nemůžete určit plně kvalifikovaný název vloženého souboru prostředků, použijte nástroj [Ildasm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) a prověřte manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="3ff17-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="3ff17-109">`.mresource`Položka identifikuje prostředek.</span><span class="sxs-lookup"><span data-stu-id="3ff17-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="3ff17-110">V tomto příkladu je plně kvalifikovaný název prostředku `SerializeTimeZoneData.SerializedTimeZones` .</span><span class="sxs-lookup"><span data-stu-id="3ff17-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="3ff17-111">Pokud je soubor prostředků vložen do stejného sestavení, které obsahuje kód pro vytvoření instance časového pásma, můžete na něj získat odkaz voláním `static` `Shared` metody (v Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> .</span><span class="sxs-lookup"><span data-stu-id="3ff17-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="3ff17-112">Pokud volání <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody dojde k chybě nebo pokud je vytvořena instance vlastního časového pásma, načtěte řetězec, který obsahuje serializované časové pásmo voláním <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="3ff17-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="3ff17-113">Deserializace dat časového pásma voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3ff17-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="3ff17-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ff17-114">Example</span></span>

<span data-ttu-id="3ff17-115">Následující příklad deserializace <xref:System.TimeZoneInfo> objekt uložený v vloženém souboru prostředků .NET XML.</span><span class="sxs-lookup"><span data-stu-id="3ff17-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="3ff17-116">Tento kód ilustruje zpracování výjimek, aby bylo zajištěno, že <xref:System.TimeZoneInfo> objekt vyžadovaný aplikací je přítomen.</span><span class="sxs-lookup"><span data-stu-id="3ff17-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="3ff17-117">Nejprve se pokusí vytvořit instanci <xref:System.TimeZoneInfo> objektu jejich načtením z registru pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3ff17-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="3ff17-118">Pokud časové pásmo nelze vytvořit, kód ho načte z vloženého souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="3ff17-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="3ff17-119">Vzhledem k tomu, že data pro vlastní časová pásma (časová pásma vytvořená pomocí <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody) nejsou uložena v registru, kód nevolá <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pro vytvoření instance časového pásma pro Palmer, Antarktida.</span><span class="sxs-lookup"><span data-stu-id="3ff17-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="3ff17-120">Místo toho se hned vyhledá vložený soubor prostředků, aby se načetl řetězec, který obsahuje data časového pásma před voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3ff17-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="3ff17-121">Zkompilování kódu</span><span class="sxs-lookup"><span data-stu-id="3ff17-121">Compiling the code</span></span>

<span data-ttu-id="3ff17-122">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="3ff17-122">This example requires:</span></span>

- <span data-ttu-id="3ff17-123">Do projektu se přidá odkaz na System. Windows. Forms. dll a System. Core. dll.</span><span class="sxs-lookup"><span data-stu-id="3ff17-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="3ff17-124">Následující obory názvů se naimportují:</span><span class="sxs-lookup"><span data-stu-id="3ff17-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="3ff17-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ff17-125">See also</span></span>

- [<span data-ttu-id="3ff17-126">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="3ff17-126">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="3ff17-127">Přehled časových pásem</span><span class="sxs-lookup"><span data-stu-id="3ff17-127">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="3ff17-128">Postupy: ukládání časových pásem do vloženého prostředku</span><span class="sxs-lookup"><span data-stu-id="3ff17-128">How to: Save time zones to an embedded resource</span></span>](save-time-zones-to-an-embedded-resource.md)
