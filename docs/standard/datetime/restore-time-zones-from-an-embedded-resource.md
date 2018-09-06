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
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43885295"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Postupy: obnovení časových pásem ze vloženého prostředku

Toto téma popisuje postup při obnovení časových pásem, které byly uloženy do souboru prostředků. Informace a pokyny k ukládání časových pásem najdete v tématu [postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>K deserializaci instance objektu TimeZoneInfo ze vloženého prostředku

1. Pokud se časové pásmo, které se mají načíst není vlastní časové pásmo, pokuste se vytvořit instanci pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody.

2. Vytvořit instanci <xref:System.Resources.ResourceManager> objekt předáním plně kvalifikovaný název souboru vložené zdroje a odkaz na sestavení, které obsahuje soubor prostředků.

   Pokud nelze určit plně kvalifikovaný název souboru vloženého prostředku, použijte [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) prozkoumat manifest sestavení. `.mresource` Položka identifikuje prostředek. V tomto příkladu je plně kvalifikovaný název prostředku `SerializeTimeZoneData.SerializedTimeZones`.

   Pokud soubor prostředků je vložený ve stejném sestavení, která obsahuje kód pro vytvoření instance časové pásmo, můžete načíst na ni odkaz pomocí volání `static` (`Shared` v jazyce Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metody.

3. Pokud volání <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metoda selže, nebo pokud je vlastní časové pásmo má být vytvořena, načíst řetězec, který obsahuje serializovaná časové pásmo voláním <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metody.

4. Zrušit serializaci dat časové pásmo voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.

## <a name="example"></a>Příklad

Následující příklad deserializuje <xref:System.TimeZoneInfo> objekt uložený v souboru vložený prostředek .NET XML.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Tento kód ukazuje zpracování výjimek a zkontrolujte, že <xref:System.TimeZoneInfo> objekt vyžadované aplikací je k dispozici. Nejprve se pokusí vytvořit instanci <xref:System.TimeZoneInfo> objekt načtením z registru pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody. Pokud nelze vytvořit instanci časové pásmo, kód načte z vloženého zdrojového souboru.

Protože data pro vlastní časových pásem (časových pásem vytvořit instanci pomocí <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda) nejsou uložené v registru, nevolá kód <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pro vytvoření instance časové pásmo pro Palmer, Antarktida. Místo toho okamžitě vypadá do souboru integrovaný prostředek, aby se načetl řetězec obsahující časové pásmo data před voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

* Aby byl odkaz na System.Windows.Forms.dll a System.Core.dll přidán do projektu.

* Aby byly importované následující obory názvů:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Viz také:

* [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
* [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
* [Postupy: Ukládání časových pásem do integrovaného prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
