---
title: 'Postupy: Vytvoření instance objektu TimeZoneInfo'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
ms.openlocfilehash: e8d50419dc21a1748a88c96c200806d0558f0e5a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276879"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Postupy: Vytvoření instance objektu TimeZoneInfo

Nejběžnější způsob, jak vytvořit instanci objektu, <xref:System.TimeZoneInfo> je načíst z registru informace. Toto téma popisuje, jak vytvořit instanci <xref:System.TimeZoneInfo> objektu z registru místního systému.

### <a name="to-instantiate-a-timezoneinfo-object"></a>Vytvoření instance objektu TimeZoneInfo

1. Deklarujte <xref:System.TimeZoneInfo> objekt.

2. Zavolejte `static` metodu ( `Shared` v Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> .

3. Zpracujte všechny výjimky vyvolané metodou, zejména <xref:System.TimeZoneNotFoundException> to, které je vyvolána, pokud časové pásmo není definováno v registru.

## <a name="example"></a>Příklad

Následující kód načte <xref:System.TimeZoneInfo> objekt, který představuje východní standardní časové pásmo, a zobrazí východní standardní čas, který odpovídá místnímu času.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType>Jediným parametrem metody je identifikátor časového pásma, které chcete načíst, což odpovídá <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> vlastnosti objektu. Identifikátor časového pásma je klíčové pole, které jedinečně identifikuje časové pásmo. I když je většina klíčů relativně krátká, identifikátor časového pásma je relativně dlouhý. Ve většině případů jeho hodnota odpovídá <xref:System.TimeZoneInfo.StandardName%2A> vlastnosti <xref:System.TimeZoneInfo> objektu, který slouží k zadání názvu standardního času časového pásma. Existují však výjimky. Nejlepším způsobem, jak zajistit, aby byl zadán platný identifikátor, je vytvořit výčet časových pásem dostupných ve vašem systému a poznamenat si identifikátory časových pásem, které jsou v nich k dispozici. Ilustraci naleznete v tématu [How to: výčet časových pásem, které jsou k dispozici v počítači](enumerate-time-zones.md). [Hledání časových pásem definovaných v místním systémovém](finding-the-time-zones-on-local-system.md) tématu obsahuje také seznam vybraných identifikátorů časových pásem.

Pokud je časové pásmo nalezeno, metoda vrátí svůj <xref:System.TimeZoneInfo> objekt. Pokud časové pásmo není nalezeno, metoda vyvolá <xref:System.TimeZoneNotFoundException> . Pokud je časové pásmo nalezeno, ale jeho data jsou poškozena nebo neúplná, metoda vyvolá <xref:System.InvalidTimeZoneException> .

Pokud vaše aplikace spoléhá na časové pásmo, které musí být k dispozici, měli byste nejprve zavolat <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metodu pro načtení informací o časovém pásmu z registru. Pokud volání metody neproběhne úspěšně, obslužná rutina výjimky by pak měla vytvořit novou instanci časového pásma nebo ji znovu vytvořit pomocí deserializace serializovaného <xref:System.TimeZoneInfo> objektu. Příklad najdete v tématu [Postupy: Obnovení časových pásem z integrovaného prostředku](restore-time-zones-from-an-embedded-resource.md) .

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
- [Hledání časových pásem definovaných v lokálním systému](finding-the-time-zones-on-local-system.md)
- [Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma](access-utc-and-local.md)
