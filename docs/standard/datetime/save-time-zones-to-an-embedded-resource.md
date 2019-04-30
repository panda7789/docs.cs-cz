---
title: 'Postupy: Ukládání časových pásem do integrovaného prostředku'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c67a97193d186275e6a788f6b18bbc17c535f367
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912701"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Postupy: Ukládání časových pásem do integrovaného prostředku

S ohledem na časové pásmo aplikace často vyžaduje přítomnost konkrétní časové pásmo. Ale protože dostupnost jednotlivých <xref:System.TimeZoneInfo> objekty závisí na informace uložené v registru místního systému, dokonce i běžně k dispozici časových pásem nemusí být k dispozici. Kromě toho vytvořit instanci pomocí informací o vlastní časových pásmech <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody není uložen s další informace o časovém pásmu v registru. Aby se zajistilo, že tato časová pásma jsou k dispozici, když jsou potřeba, můžete uložit pomocí serializace je a později je obnovit pomocí jejich deserializaci.

Obvykle k serializaci <xref:System.TimeZoneInfo> objekt vyskytuje kromě aplikace podporující službu časového pásma. V závislosti na datové úložiště používané pro uložení serializovaná <xref:System.TimeZoneInfo> objekty, časové pásmo dat může být serializován jako součást instalace nebo instalace rutina (například, když jsou data uložena v klíči registru), nebo v rámci obslužné rutiny, na kterém běží před posledním aplikace je kompilována (například když jsou serializovaná data uložená v souboru prostředku (RESX) .NET XML).

Kromě zdrojového souboru, který je zkompilován s aplikací lze použít několik dalších datových úložišť pro informace o časovém pásmu. Patří mezi ně například:

* V registru. Všimněte si, že by měla aplikace použít podklíčů klíče vlastní aplikace k ukládání dat vlastní časové pásmo spíš než podklíčů HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time zóny.

* Konfigurační soubory.

* Další soubory systému.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Chcete-li uložit časového pásma pomocí jeho serializace do souboru .resx

1. Načíst existující časové pásmo nebo vytvořte nové časové pásmo.

   Pokud chcete načíst existující časové pásmo, najdete v článku [jak: Přístup k předdefinované objekty UTC a lokálního časového pásma](../../../docs/standard/datetime/access-utc-and-local.md) a [jak: Vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

   Chcete-li vytvořit nové časové pásmo, zavoláním jednoho z přetížení <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody. Další informace najdete v tématu [jak: Vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) a [jak: Vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

2. Volání <xref:System.TimeZoneInfo.ToSerializedString%2A> metodu pro vytvoření řetězec obsahující časové pásmo data.

3. Vytvořit instanci <xref:System.IO.StreamWriter> objekt tím, že poskytuje název a volitelně cestu k souboru .resx <xref:System.IO.StreamWriter> konstruktoru třídy.

4. Vytvořit instanci <xref:System.Resources.ResXResourceWriter> předáním objektu <xref:System.IO.StreamWriter> objektu <xref:System.Resources.ResXResourceWriter> konstruktoru třídy.

5. Předejte časové pásmo serializovaný řetězec, který má <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody.

6. Volání <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metody.

7. Volání <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody.

8. Zavřít <xref:System.IO.StreamWriter> objektu voláním jeho <xref:System.IO.StreamWriter.Close%2A> metoda.

9. Vytvořený soubor .resx přidáte do projektu aplikace Visual Studio.

10. Použití **vlastnosti** okna v sadě Visual Studio, ujistěte se, že soubor .resx **akce sestavení** je nastavena na **integrovaný prostředek**.

## <a name="example"></a>Příklad

Následující příklad serializuje <xref:System.TimeZoneInfo> objekt, který představuje střed (běžný čas) a <xref:System.TimeZoneInfo> objekt, který představuje soubor prostředků .NET XML, který je pojmenován SerializedTimeZones.resx Palmera, Antarktida čas. Střední (běžný čas) je obvykle definováno v registru. Palmera, Antarktida je vlastní časové pásmo.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Tento příklad serializuje <xref:System.TimeZoneInfo> objekty tak, aby byly k dispozici v souboru prostředků v době kompilace.

Vzhledem k tomu, <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metoda přidá úplné informace hlavičky v souboru prostředků .NET XML, nelze přidat prostředky do existujícího souboru. V příkladu to kontrolou souboru SerializedTimeZones.resx a, pokud existuje, uložení všech jeho prostředků jiných než dva serializovaná časových pásmech obecný <xref:System.Collections.Generic.Dictionary%602> objektu. Pak odstraní existující soubor a stávající prostředky se přidají do nového souboru SerializedTimeZones.resx. Serializovaná časové pásmo data je také přidána do tohoto souboru.

Klíč (nebo **název**) prostředků by neměly obsahovat mezery. <xref:System.String.Replace%28System.String%2CSystem.String%29> Metoda je volána k odebrání všech vložených mezer v identifikátory časových pásem před přiřazením do souboru prostředků.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

* Aby byl odkaz na System.Windows.Forms.dll a System.Core.dll přidán do projektu.

* Aby byly importované následující obory názvů:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
- [Postupy: Obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
