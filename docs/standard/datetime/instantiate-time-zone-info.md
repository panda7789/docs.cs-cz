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
ms.openlocfilehash: 5975270dd6a166bb625278a97f4c60851cbe7942
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122286"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Postupy: vytvoření instance objektu TimeZoneInfo

Nejběžnější způsob, jak vytvořit instanci objektu <xref:System.TimeZoneInfo>, je načíst informace z registru. Toto téma popisuje, jak vytvořit instanci objektu <xref:System.TimeZoneInfo> z registru místního systému.

### <a name="to-instantiate-a-timezoneinfo-object"></a>Vytvoření instance objektu TimeZoneInfo

1. Deklarujte objekt <xref:System.TimeZoneInfo>.

2. <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> metodu zavolejte `static` (`Shared` in Visual Basic).

3. Zpracujte jakékoli výjimky vyvolané metodou, zejména <xref:System.TimeZoneNotFoundException>, která je vyvolána, pokud časové pásmo není definováno v registru.

## <a name="example"></a>Příklad

Následující kód načte <xref:System.TimeZoneInfo> objekt, který představuje východní standardní časové pásmo a zobrazí východní standardní čas, který odpovídá místnímu času.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

Jediným parametrem metody <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> je identifikátor časového pásma, které chcete načíst, což odpovídá vlastnosti objektu <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType>. Identifikátor časového pásma je klíčové pole, které jedinečně identifikuje časové pásmo. I když je většina klíčů relativně krátká, identifikátor časového pásma je relativně dlouhý. Ve většině případů jeho hodnota odpovídá vlastnosti <xref:System.TimeZoneInfo.StandardName%2A> objektu <xref:System.TimeZoneInfo>, který slouží k zadání názvu standardního času časového pásma. Existují však výjimky. Nejlepším způsobem, jak zajistit, aby byl zadán platný identifikátor, je vytvořit výčet časových pásem dostupných ve vašem systému a poznamenat si identifikátory časových pásem, které jsou v nich k dispozici. Ilustraci naleznete v tématu [How to: výčet časových pásem, které jsou k dispozici v počítači](../../../docs/standard/datetime/enumerate-time-zones.md). [Hledání časových pásem definovaných v místním systémovém](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) tématu obsahuje také seznam vybraných identifikátorů časových pásem.

Pokud je časové pásmo nalezeno, metoda vrátí svůj objekt <xref:System.TimeZoneInfo>. Pokud časové pásmo není nalezeno, vyvolá metoda <xref:System.TimeZoneNotFoundException>. Pokud je časové pásmo nalezeno, ale jeho data jsou poškozena nebo neúplná, vyvolá metoda <xref:System.InvalidTimeZoneException>.

Pokud vaše aplikace spoléhá na časové pásmo, které musí být k dispozici, měli byste nejprve zavolat metodu <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pro načtení informací o časovém pásmu z registru. Pokud se volání metody nezdařilo, vaše obslužná rutina výjimky by pak měla vytvořit novou instanci časového pásma nebo ji znovu vytvořit pomocí deserializace serializovaného objektu <xref:System.TimeZoneInfo>. Příklad najdete v tématu [Postupy: Obnovení časových pásem z integrovaného prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) .

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma](../../../docs/standard/datetime/access-utc-and-local.md)
