---
title: 'Postupy: ukládání časových pásem do vloženého prostředku'
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
ms.openlocfilehash: 4dd7e6db78b76d737cb4646c2fad79d96fb60aee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Postupy: ukládání časových pásem do vloženého prostředku

Časová pásma si aplikace často vyžaduje přítomnost konkrétní časové pásmo. Ale protože dostupnost individuální <xref:System.TimeZoneInfo> objekty závisí na informace uložené v registru místního systému, dokonce i běžně k dispozici časových pásem nemusí být k dispozici. Kromě toho se informace o vlastních časových pásmech vytvořené pomocí <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda není uložen s další informace o časovém pásmu v registru. K zajištění, že tato časová pásma jsou k dispozici, když jsou potřeba, můžete je uložit pomocí jejich serializace a později je obnovit pomocí jejich rekonstrukce.

Obvykle k serializaci <xref:System.TimeZoneInfo> objekt dochází mimo časové pásmo s deklaracemi. V závislosti na datové úložiště používané pro udržení serializovaných <xref:System.TimeZoneInfo> objekty, časové pásmo dat může serializovat jako součást instalace nebo instalace rutiny (například když jsou data uložená v klíči registru), nebo jako součást obslužné rutiny, která spouští před posledním aplikace kompiluje (například když serializovaná data uložena v souboru prostředků (RESX) .NET XML).

Kromě souboru prostředků, který se zkompiluje s aplikací můžete použít několik dalších datových úložišť pro informace o časovém pásmu. Patří mezi ně například:

* V registru. Upozorňujeme, že aplikace by měl použít podklíčů svůj vlastní klíč aplikace pro ukládání dat vlastní časového pásma, nikoli pomocí podklíče HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time zón.

* Konfigurační soubory.

* Další soubory systému.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Uložte časové pásmo serializací do souboru RESX

1. Načtení existující časového pásma nebo vytvořte nové časové pásmo.

   Načíst existující časové pásmo, najdete v části [postupy: přístup k místním ČASEM a předdefinované objekty pásem](../../../docs/standard/datetime/access-utc-and-local.md) a [postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

   Pokud chcete vytvořit nové časové pásmo, volání jednoho z přetížení <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda. Další informace najdete v tématu [postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) a [postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

2. Volání <xref:System.TimeZoneInfo.ToSerializedString%2A> metodu pro vytvoření řetězec, který obsahuje data na časové pásmo.

3. Vytváření instancí <xref:System.IO.StreamWriter> objekt tím, že poskytuje název a volitelně cestu k souboru .resx <xref:System.IO.StreamWriter> konstruktoru třídy.

4. Vytváření instancí <xref:System.Resources.ResXResourceWriter> objekt předáním <xref:System.IO.StreamWriter> do objektu <xref:System.Resources.ResXResourceWriter> konstruktoru třídy.

5. Předejte časové pásmo serializovaný řetězec, který má <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metoda.

6. Volání <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metoda.

7. Volání <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metoda.

8. Zavřít <xref:System.IO.StreamWriter> objekt voláním jeho <xref:System.IO.StreamWriter.Close%2A> metoda.

9. Vytvořený soubor .resx přidejte do projektu aplikace Visual Studio.

10. Pomocí **vlastnosti** oken v sadě Visual Studio, ujistěte se, že soubor .resx **akce sestavení** je nastavena na **vložený prostředek**.

## <a name="example"></a>Příklad

V následujícím příkladu jsou <xref:System.TimeZoneInfo> objekt, který představuje čas a <xref:System.TimeZoneInfo> objekt, který reprezentuje Palmer stanice, Antarktida čas do souboru .NET XML prostředků s názvem SerializedTimeZones.resx. Centrální běžný čas je obvykle definováno v registru; Stanice Palmer, Antarktida je vlastní časové pásmo.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Tento příklad serializuje <xref:System.TimeZoneInfo> objekty tak, aby byly k dispozici v souboru prostředků v době kompilace.

Protože <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metoda přidá do souboru .NET XML prostředků úplné informace hlavičky, nelze jej použít chcete přidat prostředky do existující soubor. V příkladu to kontrolou souboru SerializedTimeZones.resx a, pokud existuje, všechny její prostředky uložení jiných než dva serializovaná časových pásem s obecným <xref:System.Collections.Generic.Dictionary%602> objektu. Odstraní existující soubor a existující prostředky jsou přidány do nového souboru SerializedTimeZones.resx. Data serializovaná časové pásmo je taky přidaná do tohoto souboru.

Klíč (nebo **název**) prostředků nesmí obsahovat mezery. <xref:System.String.Replace%28System.String%2CSystem.String%29> Metoda je volána před jsou přiřazeny k souboru prostředků odeberte všechny mezery v identifikátory časových pásem.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

* Aby byl přidán odkaz na System.Windows.Forms.dll a System.Core.dll do projektu.

* Aby byly importované následujících oborů názvů:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
[postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
