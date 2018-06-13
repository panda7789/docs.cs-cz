---
title: 'Postupy: vytvoření instance objektu TimeZoneInfo'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e15e7f8968d7edf87ae3cd709d8fb26a2f49826a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572044"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="1a314-102">Postupy: vytvoření instance objektu TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="1a314-102">How to: Instantiate a TimeZoneInfo object</span></span>

<span data-ttu-id="1a314-103">Nejběžnější způsob vytvoření instance objektu <xref:System.TimeZoneInfo> objekt je k načtení informací o jej z registru.</span><span class="sxs-lookup"><span data-stu-id="1a314-103">The most common way to instantiate a <xref:System.TimeZoneInfo> object is to retrieve information about it from the registry.</span></span> <span data-ttu-id="1a314-104">Toto téma popisuje, jak vytvořit instanci <xref:System.TimeZoneInfo> objekt z registru místního systému.</span><span class="sxs-lookup"><span data-stu-id="1a314-104">This topic discusses how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

### <a name="to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="1a314-105">K vytvoření instance objektu TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="1a314-105">To instantiate a TimeZoneInfo object</span></span>

1. <span data-ttu-id="1a314-106">Deklarace <xref:System.TimeZoneInfo> objektu.</span><span class="sxs-lookup"><span data-stu-id="1a314-106">Declare a <xref:System.TimeZoneInfo> object.</span></span>

2. <span data-ttu-id="1a314-107">Volání `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="1a314-107">Call the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> method.</span></span>

3. <span data-ttu-id="1a314-108">Zpracujte jakékoli výjimky vyvolané metodou, zejména v <xref:System.TimeZoneNotFoundException> , je vyvolána, pokud se časové pásmo není definován v registru.</span><span class="sxs-lookup"><span data-stu-id="1a314-108">Handle any exceptions thrown by the method, particularly the <xref:System.TimeZoneNotFoundException> that is thrown if the time zone is not defined in the registry.</span></span>

## <a name="example"></a><span data-ttu-id="1a314-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a314-109">Example</span></span>

<span data-ttu-id="1a314-110">Následující kód načte <xref:System.TimeZoneInfo> objekt, který představuje standardní východní časové pásmo a zobrazí východní běžný čas, který odpovídá na místní čas.</span><span class="sxs-lookup"><span data-stu-id="1a314-110">The following code retrieves a <xref:System.TimeZoneInfo> object that represents the Eastern Standard Time zone and displays the Eastern Standard time that corresponds to the local time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<span data-ttu-id="1a314-111"><xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> Jediný parametr metody je identifikátor časové pásmo, které chcete zjistit, který odpovídá objektu <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1a314-111">The <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> method's single parameter is the identifier of the time zone that you want to retrieve, which corresponds to the object's <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1a314-112">Identifikátor časového pásma je klíčové pole, která jednoznačně identifikuje časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="1a314-112">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="1a314-113">Zatímco většina klíče jsou poměrně krátké, identifikátor časové pásmo je poměrně dlouho.</span><span class="sxs-lookup"><span data-stu-id="1a314-113">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="1a314-114">Ve většině případů jeho hodnota odpovídá <xref:System.TimeZoneInfo.StandardName%2A> vlastnost <xref:System.TimeZoneInfo> objekt, který slouží k poskytování název časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="1a314-114">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A> property of a <xref:System.TimeZoneInfo> object, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="1a314-115">Existují však výjimky.</span><span class="sxs-lookup"><span data-stu-id="1a314-115">However, there are exceptions.</span></span> <span data-ttu-id="1a314-116">Vytvoření výčtu časových pásem, který je k dispozici v systému a Všimněte si identifikátory časových pásem v nich je nejlepší způsob, jak se ujistěte, že jste zadali platný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="1a314-116">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note the identifiers of the time zones present on them.</span></span> <span data-ttu-id="1a314-117">Pro ilustraci, najdete v části [postupy: vytvoření výčtu časových pásem přítomných na počítači](../../../docs/standard/datetime/enumerate-time-zones.md).</span><span class="sxs-lookup"><span data-stu-id="1a314-117">For an illustration, see [How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md).</span></span> <span data-ttu-id="1a314-118">[Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) téma také obsahuje seznam identifikátorů vybranému časovému pásmu.</span><span class="sxs-lookup"><span data-stu-id="1a314-118">The [Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) topic also contains a list of selected time zone identifiers.</span></span>

<span data-ttu-id="1a314-119">Pokud se časové pásmo nalezeno, vrátí metoda jeho <xref:System.TimeZoneInfo> objektu.</span><span class="sxs-lookup"><span data-stu-id="1a314-119">If the time zone is found, the method returns its <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="1a314-120">Pokud není nalezen časové pásmo, vyvolá metoda <xref:System.TimeZoneNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="1a314-120">If the time zone is not found, the method throws a <xref:System.TimeZoneNotFoundException>.</span></span> <span data-ttu-id="1a314-121">Pokud je nalezena časové pásmo, ale jeho data jsou poškozená nebo nekompletní, vyvolá metoda <xref:System.InvalidTimeZoneException>.</span><span class="sxs-lookup"><span data-stu-id="1a314-121">If the time zone is found but its data is corrupted or incomplete, the method throws an <xref:System.InvalidTimeZoneException>.</span></span>

<span data-ttu-id="1a314-122">Pokud vaše aplikace závisí na časové pásmo, které musí být k dispozici, měli byste nejprve zavolat <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> a načíst informace o časovém pásmu z registru.</span><span class="sxs-lookup"><span data-stu-id="1a314-122">If your application relies on a time zone that must be present, you should first call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method to retrieve the time zone information from the registry.</span></span> <span data-ttu-id="1a314-123">Pokud selže volání metody vaší obslužné rutiny výjimky by pak buď vytvořit novou instanci třídy časové pásmo nebo jej znovu vytvořit pomocí deserializace serializovaného <xref:System.TimeZoneInfo> objektu.</span><span class="sxs-lookup"><span data-stu-id="1a314-123">If the method call fails, your exception handler should then either create a new instance of the time zone or re-create it by deserializing a serialized <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="1a314-124">V tématu [postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) příklad.</span><span class="sxs-lookup"><span data-stu-id="1a314-124">See [How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) for an example.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a314-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a314-125">See also</span></span>

<span data-ttu-id="1a314-126">[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[postupy: přístup k místním ČASEM a předdefinované objekty zóny](../../../docs/standard/datetime/access-utc-and-local.md)</span><span class="sxs-lookup"><span data-stu-id="1a314-126">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md)</span></span>
