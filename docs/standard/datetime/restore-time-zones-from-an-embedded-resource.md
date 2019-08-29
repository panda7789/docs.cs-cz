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
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Postupy: Obnovení časových pásem z integrovaného prostředku

Toto téma popisuje, jak obnovit časová pásma uložená v souboru prostředků. Informace a pokyny k ukládání časových pásem naleznete v tématu [How to: Uloží časová pásma do vloženého](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)prostředku.

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Deserializace objektu TimeZoneInfo od vloženého prostředku

1. Pokud časové pásmo, které má být načteno, není vlastním časovým pásmem, zkuste vytvořit instanci pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody.

2. Vytvořte instanci objektu předáním plně kvalifikovaného názvu vloženého souboru prostředků a odkazu na sestavení, které obsahuje soubor prostředků. <xref:System.Resources.ResourceManager>

   Pokud nemůžete určit plně kvalifikovaný název vloženého souboru prostředků, použijte nástroj [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) a prověřte manifest sestavení. `.mresource` Položka identifikuje prostředek. V tomto příkladu je `SerializeTimeZoneData.SerializedTimeZones`plně kvalifikovaný název prostředku.

   Pokud je soubor prostředků vložen do stejného sestavení, které obsahuje kód pro vytvoření instance časového pásma, můžete na něj získat odkaz voláním `static` metody (`Shared` v Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> .

3. Pokud volání <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody dojde k chybě nebo pokud je vytvořena instance vlastního časového pásma, načtěte řetězec, který obsahuje serializované časové pásmo <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> voláním metody.

4. Deserializace dat časového pásma voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.

## <a name="example"></a>Příklad

Následující příklad deserializace <xref:System.TimeZoneInfo> objekt uložený v vloženém souboru prostředků .NET XML.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Tento kód ilustruje zpracování výjimek, aby bylo <xref:System.TimeZoneInfo> zajištěno, že objekt vyžadovaný aplikací je přítomen. Nejprve se pokusí vytvořit instanci <xref:System.TimeZoneInfo> objektu jejich načtením z registru <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pomocí metody. Pokud časové pásmo nelze vytvořit, kód ho načte z vloženého souboru prostředků.

Vzhledem k tomu, že data pro vlastní časová pásma (časová <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> pásma vytvořená pomocí metody) nejsou uložena v registru, kód <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> nevolá pro vytvoření instance časového pásma pro Palmer, Antarktida. Místo toho se hned vyhledá vložený soubor prostředků, aby se načetl řetězec, který obsahuje data časového pásma před voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

- Do projektu se přidá odkaz na System. Windows. Forms. dll a System. Core. dll.

- Následující obory názvů se naimportují:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
- [Postupy: Uložit časová pásma do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
