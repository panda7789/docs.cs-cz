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
ms.openlocfilehash: 8c8ff38325e26dd1bc946f6f12c365b6dea3e228
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047331"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Postupy: vytvoření instance objektu TimeZoneInfo

Nejběžnější způsob vytvoření instance <xref:System.TimeZoneInfo> objekt je k načtení informací o něm z registru. Toto téma popisuje, jak vytvořit instanci <xref:System.TimeZoneInfo> objektu z místního systémového registru.

### <a name="to-instantiate-a-timezoneinfo-object"></a>K vytvoření instance objektu TimeZoneInfo

1. Deklarace <xref:System.TimeZoneInfo> objektu.

2. Volání `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> metody.

3. Zpracování jakýchkoli výjimek metodou, zejména <xref:System.TimeZoneNotFoundException> , která je vyvolána, pokud časové pásmo není definovaná v registru.

## <a name="example"></a>Příklad

Následující kód načte <xref:System.TimeZoneInfo> objekt, který představuje standardní východní časové pásmo a zobrazí východní běžný čas, který odpovídá na místní čas.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> Jediný parametr metody je identifikátor v časovém pásmu, který chcete načíst, což odpovídá objektu <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> vlastnost. Identifikátor časové pásmo je pole s klíčem, který jednoznačně identifikuje časové pásmo. Většina klíčů jsou poměrně krátké, identifikátor časové pásmo je poměrně dlouho. Ve většině případů, jeho hodnota odpovídá <xref:System.TimeZoneInfo.StandardName%2A> vlastnost <xref:System.TimeZoneInfo> objekt, který slouží k poskytnutí názvu časového pásma (běžný čas). Existují však výjimky. Vytvoření výčtu časových pásem, který je k dispozici ve vašem systému a Všimněte si identifikátory časových pásem přítomných na nich je nejlepší způsob, jak Ujistěte se, abyste zadali platný identifikátor. Pro ilustraci, naleznete v tématu [postupy: vytvoření výčtu časových pásem přítomných na počítači](../../../docs/standard/datetime/enumerate-time-zones.md). [Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) téma obsahuje také seznam identifikátorů vybranému časovému pásmu.

Pokud se najde časové pásmo, metoda vrátí jeho <xref:System.TimeZoneInfo> objektu. Pokud se časové pásmo není nalezen, metoda vyvolá <xref:System.TimeZoneNotFoundException>. Pokud se nachází na časové pásmo, ale jeho data jsou poškozena nebo nekompletní, vyvolá metoda <xref:System.InvalidTimeZoneException>.

Pokud vaše aplikace závisí na časové pásmo, které musí být k dispozici, měli byste nejprve zavolat <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody k získání informace o časovém pásmu z registru. Pokud selže volání metody obslužné rutině výjimek by měl pak vytvořit novou instanci třídy časové pásmo nebo jej znovu vytvořit pomocí deserializaci serializovaného <xref:System.TimeZoneInfo> objektu. Zobrazit [postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) příklad.

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma](../../../docs/standard/datetime/access-utc-and-local.md)
