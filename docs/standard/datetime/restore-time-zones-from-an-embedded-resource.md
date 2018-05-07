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
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Postupy: obnovení časových pásem ze vloženého prostředku

Toto téma popisuje postup obnovení časových pásem, které byly uloženy do souboru prostředků. Informace a pokyny k ukládání časových pásem, najdete v části [postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>K deserializaci objektu TimeZoneInfo ze vloženého prostředku

1. Pokud mají být načteny časové pásmo není vlastní časové pásmo, pokuste se vytvořit instanci pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metoda.

2. Vytváření instancí <xref:System.Resources.ResourceManager> objekt předáním plně kvalifikovaný název vloženého prostředku souboru a odkaz na sestavení, která obsahuje soubor prostředků.

   Pokud nelze určit plně kvalifikovaný název souboru vložený prostředek, použijte [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) prozkoumat manifest sestavení. `.mresource` Položka identifikuje prostředek. V tomto příkladu plně kvalifikovaný název prostředku je `SerializeTimeZoneData.SerializedTimeZones`.

   Pokud se soubor prostředků je vložen do stejného sestavení, která obsahuje kód pro vytvoření instance časové pásmo, můžete načíst odkaz na jeho voláním `static` (`Shared` v jazyce Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metoda.

3. Pokud volání <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metoda selže, nebo pokud vlastní časové pásmo má být vytvořena instance, načíst řetězec, který obsahuje serializované časové pásmo voláním <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metoda.

4. Deserializovat údaje o časovém pásmu voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metoda.

## <a name="example"></a>Příklad

Následující příklad deserializuje <xref:System.TimeZoneInfo> objektu uloženého ve vloženém .NET XML souboru prostředků.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Tento kód ukazuje zpracování výjimek zajistit, aby <xref:System.TimeZoneInfo> nachází objekt požadované aplikací. Nejprve se pokusí vytvořit instanci <xref:System.TimeZoneInfo> objekt načtením z registru pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metoda. Pokud nelze vytvořit instanci časové pásmo, načte kód z soubor vložený prostředek.

Protože data pro vlastní časových pásem (časových pásem vytvořené pomocí <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda) nejsou uložené v registru nevyvolá kód <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> k vytváření instancí časové pásmo pro Palmer Antarktida. Místo toho okamžitě vypadá to, k souboru vložený prostředek načíst řetězec, který obsahuje data na časové pásmo, zavolá <xref:System.TimeZoneInfo.FromSerializedString%2A> metoda.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

* Aby byl přidán odkaz na System.Windows.Forms.dll a System.Core.dll do projektu.

* Aby byly importované následujících oborů názvů:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
[postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
