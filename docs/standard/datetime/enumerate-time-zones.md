---
title: "Postupy: vytvoření výčtu časových pásem přítomných na počítači"
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
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f77afc8a0f2e6c110f4dc037c12ecc8b06908e60
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Postupy: vytvoření výčtu časových pásem přítomných na počítači

Úspěšně spolupracuje s určeným časovým pásmem vyžaduje, aby informace o tomto časové pásmo k dispozici v systému. Operační systémy Windows XP a Windows Vista uložit tyto informace v registru. Ale sice velká celkový počet časových pásem, které existují v celém světě, registr obsahuje informace o pouze podmnožinu z nich. Kromě toho je registr je dynamické struktura, jejichž obsah se mohou změnit záměrné i náhodných. V důsledku toho aplikace nelze vždy předpokládat, že konkrétní časové pásmo je definovaný a k dispozici v systému. Prvním krokem pro mnoho aplikací, které používají aplikace informace o časovém pásmu je určit, zda jsou k dispozici v místním systému požadované časová pásma nebo uživateli přidělit seznam časových pásem ze které chcete vybrat. To vyžaduje, aby aplikace výčet časových pásem definovaných v lokálním systému.

> [!NOTE]
> Pokud aplikace spoléhá na přítomnost konkrétní časové pásmo, které nemusí být definován v lokálním systému, aplikace můžete zajistit jeho přítomnosti serializaci a deserializaci informace o časovém pásmu. Časové pásmo poté lze přidat do ovládacího prvku seznam tak, aby uživatel aplikace můžete ji vybrat. Podrobnosti najdete v tématu [postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) a [postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Výčet časových pásem přítomných v lokálním systému

1. Volání <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metoda. Metoda vrátí obecnou <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekce <xref:System.TimeZoneInfo> objekty. Položky v kolekci jsou seřazeny podle jejich <xref:System.TimeZoneInfo.DisplayName%2A> vlastnost. Příklad:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Zobrazení výčtu jednotlivých <xref:System.TimeZoneInfo> objektů v kolekcích pomocí `foreach` smyčky (v jazyku C#) nebo `For Each`...`Next` smyčky (v jazyce Visual Basic) a proveďte všechny nezbytné zpracování pro každý objekt. Například následující kód vytvoří výčet <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekce <xref:System.TimeZoneInfo> objektů vrácených v kroku 1 a vypíše zobrazovaný název každého časového pásma v konzole.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Možnost prezentovat seznam časových pásem v místním systému

1. Volání <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metoda. Metoda vrátí obecnou <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekce <xref:System.TimeZoneInfo> objekty.

2. Přiřadit kolekci vrácenou v kroku 1 `DataSource` vlastností ovládacího prvku Windows forms nebo v technologii ASP.NET ovládací prvek seznamu.

3. Načtení <xref:System.TimeZoneInfo> objekt, který uživatel vybral.

Příklad uvádí ukázku pro aplikaci systému Windows.

## <a name="example"></a>Příklad

V příkladu se spustí aplikace systému Windows, která zobrazuje časových pásem definovaných v systému v seznamu. V příkladu se pak zobrazí dialogové okno, které obsahuje hodnotu <xref:System.TimeZoneInfo.DisplayName%2A> vlastnost objektu časové pásmo vybraný uživatelem.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Nejvíce seznamu ovládacích prvků (, jako <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> nebo <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> ovládací prvek) umožňují přiřadit kolekci objektové proměnné, jejich `DataSource` vlastnost, pokud implementuje tuto kolekci <xref:System.Collections.IEnumerable> rozhraní. (Obecná <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> třída tomu.) K zobrazení jednotlivých objektů v kolekci, ovládací prvek volá tento objekt `ToString` metoda extrahování řetězec, který se používá k reprezentaci objektu. U <xref:System.TimeZoneInfo> objekty, `ToString` metoda vrátí <xref:System.TimeZoneInfo> zobrazovaný název objektu (hodnota jeho <xref:System.TimeZoneInfo.DisplayName%2A> vlastnost).

> [!NOTE]
> Protože ovládací prvky seznamu volání objektu `ToString` metodu, můžete přiřadit kolekci <xref:System.TimeZoneInfo> objekty do ovládacího prvku, mají ovládacího prvku zobrazení nějaký výstižný název pro každý objekt a načíst <xref:System.TimeZoneInfo> objekt, který uživatel vybral. Tím se eliminuje potřeba extrahovat řetězec pro každý objekt v kolekci, přiřadit řetězec do kolekce, která je pak přiřazen k ovládacímu prvku `DataSource` vlastnost načíst řetězec uživatel vybral a pak použijte tento řetězec k extrakci objektu Popisuje, že IT oddělení. 

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

* Aby byl přidán odkaz na System.Core.dll do projektu.

* Aby byly importované následujících oborů názvů:

  <xref:System>(v kódu jazyka C#)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
[postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
