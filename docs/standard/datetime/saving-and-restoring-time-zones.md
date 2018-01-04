---
title: "Ukládání a obnova časových pásem"
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
- restoring time zones
- deserialization [.NET Framework], time zones
- serialization [.NET Framework], time zones
- time zone objects [.NET Framework], restoring
- saving time zones
- time zone objects [.NET Framework], deserializing
- time zones [.NET Framework], saving
- time zones [.NET Framework], restoring
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d9451b1b0ff41f32c31ef3574b5684ae5a02e252
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="saving-and-restoring-time-zones"></a><span data-ttu-id="35706-102">Ukládání a obnova časových pásem</span><span class="sxs-lookup"><span data-stu-id="35706-102">Saving and restoring time zones</span></span>

<span data-ttu-id="35706-103"><xref:System.TimeZoneInfo> Třída vychází z registru pro načtení dat předdefinovaného časového pásma.</span><span class="sxs-lookup"><span data-stu-id="35706-103">The <xref:System.TimeZoneInfo> class relies on the registry to retrieve predefined time zone data.</span></span> <span data-ttu-id="35706-104">Dynamická struktura je však registru.</span><span class="sxs-lookup"><span data-stu-id="35706-104">However, the registry is a dynamic structure.</span></span> <span data-ttu-id="35706-105">Kromě toho informace o časovém pásmu, který obsahuje registru se používá v operačním systému především pro zpracování úpravy času a převody pro aktuálního roku.</span><span class="sxs-lookup"><span data-stu-id="35706-105">Additionally, the time zone information that the registry contains is used by the operating system primarily to handle time adjustments and conversions for the current year.</span></span> <span data-ttu-id="35706-106">To má dva hlavní důsledky pro aplikace, které jsou závislé na přesné časové pásmo dat:</span><span class="sxs-lookup"><span data-stu-id="35706-106">This has two major implications for applications that rely on accurate time zone data:</span></span>

* <span data-ttu-id="35706-107">Časové pásmo, které je vyžadována danou aplikací nemusí být definován v registru, nebo bylo přejmenováno nebo odebrat z registru.</span><span class="sxs-lookup"><span data-stu-id="35706-107">A time zone that is required by an application may not be defined in the registry, or it may have been renamed or removed from the registry.</span></span>

* <span data-ttu-id="35706-108">Časové pásmo, která je definována v registru mohou chybět informace o pravidlech konkrétní úprav, které jsou nezbytné pro převody historických časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="35706-108">A time zone that is defined in the registry may lack information about the particular adjustment rules that are necessary for historical time zone conversions.</span></span>

<span data-ttu-id="35706-109"><xref:System.TimeZoneInfo> Třída řeší tato omezení prostřednictvím své podpory serializace (ukládání) a rekonstrukce (obnovení) dat časového pásma.</span><span class="sxs-lookup"><span data-stu-id="35706-109">The <xref:System.TimeZoneInfo> class addresses these limitations through its support for serialization (saving) and deserialization (restoring) of time zone data.</span></span>

## <a name="time-zone-serialization-and-deserialization"></a><span data-ttu-id="35706-110">Časové pásmo serializace a deserializace</span><span class="sxs-lookup"><span data-stu-id="35706-110">Time zone serialization and deserialization</span></span>

<span data-ttu-id="35706-111">Ukládání a obnovení časového pásma pomocí serializace a deserializace dat časového pásma zahrnuje pouze dvě volání metod:</span><span class="sxs-lookup"><span data-stu-id="35706-111">Saving and restoring a time zone by serializing and deserializing time zone data involves just two method calls:</span></span>

* <span data-ttu-id="35706-112">Může serializovat <xref:System.TimeZoneInfo> objekt voláním tento objekt <xref:System.TimeZoneInfo.ToSerializedString%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="35706-112">You can serialize a <xref:System.TimeZoneInfo> object by calling that object's <xref:System.TimeZoneInfo.ToSerializedString%2A> method.</span></span> <span data-ttu-id="35706-113">Metoda nepřijímá žádné parametry a vrátí řetězec, který obsahuje informace o časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="35706-113">The method takes no parameters and returns a string that contains time zone information.</span></span>

* <span data-ttu-id="35706-114">Může deserializovat <xref:System.TimeZoneInfo> z serializovaného řetězce předáním tohoto řetězce pro objekt `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="35706-114">You can deserialize a <xref:System.TimeZoneInfo> object from a serialized string by passing that string to the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> method.</span></span>

## <a name="serialization-and-deserialization-scenarios"></a><span data-ttu-id="35706-115">Serializace a deserializace scénáře</span><span class="sxs-lookup"><span data-stu-id="35706-115">Serialization and deserialization scenarios</span></span>

<span data-ttu-id="35706-116">Možnost uložení (nebo serializovat) <xref:System.TimeZoneInfo> objekt na řetězec a k obnovení (nebo deserializaci) je pro pozdější použití zvyšuje nástroj a flexibilitu <xref:System.TimeZoneInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="35706-116">The ability to save (or serialize) a <xref:System.TimeZoneInfo> object to a string and to restore (or deserialize) it for later use increases both the utility and the flexibility of the <xref:System.TimeZoneInfo> class.</span></span> <span data-ttu-id="35706-117">Tento oddíl se zabývá některé situace, ve kterých jsou velmi užitečné serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="35706-117">This section examines some of the situations in which serialization and deserialization are most useful.</span></span>

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a><span data-ttu-id="35706-118">Serializace a deserializace dat časového pásma v aplikaci</span><span class="sxs-lookup"><span data-stu-id="35706-118">Serializing and deserializing time zone data in an application</span></span>

<span data-ttu-id="35706-119">Serializované časové pásmo lze obnovit z řetězce, když je to potřeba.</span><span class="sxs-lookup"><span data-stu-id="35706-119">A serialized time zone can be restored from a string when it is needed.</span></span> <span data-ttu-id="35706-120">Aplikace to třeba udělat, pokud nelze správně převést datum a čas v konkrétní datum rozsahu časovém pásmu z registru načíst.</span><span class="sxs-lookup"><span data-stu-id="35706-120">An application might do this if the time zone retrieved from the registry is unable to correctly convert a date and time within a particular date range.</span></span> <span data-ttu-id="35706-121">Například data časové pásmo v registru systému Windows XP podporuje jediné pravidlo úprav, zatímco časových pásem definovaných v registru systému Windows Vista obvykle poskytují informace o dvou pravidlech úprav.</span><span class="sxs-lookup"><span data-stu-id="35706-121">For example, time zone data in the Windows XP registry supports a single adjustment rule, while time zones defined in the Windows Vista registry typically provide information about two adjustment rules.</span></span> <span data-ttu-id="35706-122">To znamená, že historické čas převody mohou být nepřesné.</span><span class="sxs-lookup"><span data-stu-id="35706-122">This means that historical time conversions may be inaccurate.</span></span> <span data-ttu-id="35706-123">Serializace a deserializace dat časového pásma může zpracovávat toto omezení.</span><span class="sxs-lookup"><span data-stu-id="35706-123">Serialization and deserialization of time zone data can handle this limitation.</span></span>

<span data-ttu-id="35706-124">V následujícím příkladu, vlastní <xref:System.TimeZoneInfo> třídu, která nemá žádná pravidla úprav není definován pro představují USA Východní standardního časového pásma z 1883 k 1917 před zavedením letního času ve Spojených státech amerických.</span><span class="sxs-lookup"><span data-stu-id="35706-124">In the following example, a custom <xref:System.TimeZoneInfo> class that has no adjustment rules is defined to represent the U.S. Eastern Standard Time zone from 1883 to 1917, before the introduction of daylight saving time in the United States.</span></span> <span data-ttu-id="35706-125">Vlastní časové pásmo je serializováno v proměnné, která má globální obor.</span><span class="sxs-lookup"><span data-stu-id="35706-125">The custom time zone is serialized in a variable that has global scope.</span></span> <span data-ttu-id="35706-126">Metodě převodu časového pásma `ConvertUtcTime`, předaný převést časy koordinovaný univerzální čas (UTC).</span><span class="sxs-lookup"><span data-stu-id="35706-126">The time zone conversion method, `ConvertUtcTime`, is passed Coordinated Universal Time (UTC) times to convert.</span></span> <span data-ttu-id="35706-127">Pokud datum a čas, dojde k 1917 nebo dřívější, vlastní standardní východní časové pásmo je obnoven ze serializovaného řetězce a nahradí časovém pásmu z registru načíst.</span><span class="sxs-lookup"><span data-stu-id="35706-127">If the date and time occurs in 1917 or earlier, the custom Eastern Standard Time zone is restored from a serialized string and replaces the time zone retrieved from the registry.</span></span>

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a><span data-ttu-id="35706-128">Zpracování výjimek časového pásma</span><span class="sxs-lookup"><span data-stu-id="35706-128">Handling time zone exceptions</span></span>

<span data-ttu-id="35706-129">Protože registru je dynamická struktura, její obsah se vztahují nechtěným nebo záměrným změnám.</span><span class="sxs-lookup"><span data-stu-id="35706-129">Because the registry is a dynamic structure, its contents are subject to accidental or deliberate modification.</span></span> <span data-ttu-id="35706-130">To znamená, že časové pásmo, který by měl být definován v registru a, který je vyžadován ke spuštění aplikace nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="35706-130">This means that a time zone that should be defined in the registry and that is required for an application to execute successfully may be absent.</span></span> <span data-ttu-id="35706-131">Bez podpory pro časové pásmo serializace a deserializace, budete mít velmi málo možností ale zpracování výsledné <xref:System.TimeZoneNotFoundException> ukončením aplikace.</span><span class="sxs-lookup"><span data-stu-id="35706-131">Without support for time zone serialization and deserialization, you have little choice but to handle the resulting <xref:System.TimeZoneNotFoundException> by ending the application.</span></span> <span data-ttu-id="35706-132">Však pomocí časové pásmo serializace a deserializace lze zpracovat neočekávanou <xref:System.TimeZoneNotFoundException> obnovením požadováno časového pásma z serializovaného řetězce a aplikace bude dále běžet.</span><span class="sxs-lookup"><span data-stu-id="35706-132">However, by using time zone serialization and deserialization, you can handle an unexpected <xref:System.TimeZoneNotFoundException> by restoring the required time zone from a serialized string, and the application will continue to run.</span></span>

<span data-ttu-id="35706-133">Následující příklad vytvoří a serializuje vlastní centrální standardní časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="35706-133">The following example creates and serializes a custom Central Standard Time zone.</span></span> <span data-ttu-id="35706-134">Potom se pokusí načíst centrální standardního časového pásma z registru.</span><span class="sxs-lookup"><span data-stu-id="35706-134">It then tries to retrieve the Central Standard Time zone from the registry.</span></span> <span data-ttu-id="35706-135">Pokud operace načítání vyvolá <xref:System.TimeZoneNotFoundException> nebo <xref:System.InvalidTimeZoneException>, obslužná rutina výjimky deserializuje časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="35706-135">If the retrieval operation throws either a <xref:System.TimeZoneNotFoundException> or an <xref:System.InvalidTimeZoneException>, the exception handler deserializes the time zone.</span></span>

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a><span data-ttu-id="35706-136">Ukládání serializovaného řetězce a obnovení dat v případě potřeby</span><span class="sxs-lookup"><span data-stu-id="35706-136">Storing a serialized string and restoring it when needed</span></span>

<span data-ttu-id="35706-137">V předchozích příkladech mít uložené informace o časovém pásmu na proměnnou string a obnovit jej v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="35706-137">The previous examples have stored time zone information to a string variable and restored it when needed.</span></span> <span data-ttu-id="35706-138">Řetězec, který obsahuje serializovaných čas, informace o zóně může sám sebe být uložený v některém paměťovém médiu, jako je například externí soubor, soubor prostředků však vložený registru nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="35706-138">However, the string that contains serialized time zone information can itself be stored in some storage medium, such as an external file, a resource file embedded in the application, or the registry.</span></span> <span data-ttu-id="35706-139">(Všimněte si, že by měly být uložené informace o vlastních časových pásmech kromě systému časové pásmo klíče v registru.)</span><span class="sxs-lookup"><span data-stu-id="35706-139">(Note that information about custom time zones should be stored apart from the system's time zone keys in the registry.)</span></span>

<span data-ttu-id="35706-140">Ukládání řetězce serializované časové pásmo tímto způsobem také odděluje rutinu vytváření časového pásma od vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="35706-140">Storing a serialized time zone string in this manner also separates the time zone creation routine from the application itself.</span></span> <span data-ttu-id="35706-141">Například rutina vytvoření časového pásma můžete spustit a vytvořit datový soubor, který obsahuje informace o historických časovém pásmu, který můžete použít aplikaci.</span><span class="sxs-lookup"><span data-stu-id="35706-141">For example, a time zone creation routine can execute and create a data file that contains historical time zone information that an application can use.</span></span> <span data-ttu-id="35706-142">Datový soubor může být následně instalován s aplikací a můžete ho otevřít a jeden nebo více jeho časových pásem lze deserializovat, když je aplikace vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="35706-142">The data file can be then be installed with the application, and it can be opened and one or more of its time zones can be deserialized when the application requires them.</span></span>

<span data-ttu-id="35706-143">Příklad, který používá vložený prostředek k uložení serializovaných dat časového pásma, naleznete v části [postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) a [postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="35706-143">For an example that uses an embedded resource to store serialized time zone data, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="35706-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="35706-144">See also</span></span>

[<span data-ttu-id="35706-145">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="35706-145">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
