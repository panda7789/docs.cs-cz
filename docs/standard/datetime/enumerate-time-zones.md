---
title: 'Postupy: Vytvoření výčtu časových pásem přítomných na počítači'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82898e80f5acb2cb0dcab65390701efc8d48115b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586572"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Postupy: Vytvoření výčtu časových pásem přítomných na počítači

Úspěšně spolupracuje s určeným časovým pásmem vyžaduje systém k dispozici informace o tomto časovém pásmu. Operační systémy Windows XP a Windows Vista ukládání příslušných informací v registru. Však sice velký počet časových pásem, které existují po celém světě, registr obsahuje informace o jenom část z nich. Kromě toho samotného registru je dynamické strukturu, jejíž obsah se můžou rozhodnout vědomě a záměrně, náhodné změnit. V důsledku toho aplikace nemůže vždy předpokládat, že konkrétní časové pásmo je definované a dostupné v systému. Prvním krokem pro mnoho aplikací, které používají aplikace informace o časovém pásmu je určit, zda jsou k dispozici v místním systému vyžaduje časových pásem nebo poskytnout seznam časových pásem, ze kterého chcete vybrat uživatele. To vyžaduje, aby aplikace vytvoření výčtu časových pásem definovaných v lokálním systému.

> [!NOTE]
> Pokud aplikace závisí na přítomnosti určitého časového pásma, které nemusí být definováno v lokálním systému, můžete aplikaci zajistit jeho přítomnost serializaci a deserializaci informace o časovém pásmu. Časové pásmo je potom možné přidat do ovládacího prvku seznam, tak, aby uživatel aplikace můžete vybrat. Podrobnosti najdete v tématu [jak: Ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) a [jak: Obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>K vytvoření výčtu časových pásem přítomných v místním systému

1. Volání <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metody. Metoda vrátí obecnou <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekce <xref:System.TimeZoneInfo> objekty. Položky v kolekci jsou seřazeny podle jejich <xref:System.TimeZoneInfo.DisplayName%2A> vlastnost. Příklad:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Zobrazení výčtu jednotlivých <xref:System.TimeZoneInfo> objekty v kolekci pomocí `foreach` smyčky (v jazyce C#) nebo `For Each`...`Next` smyčky (v jazyce Visual Basic) a proveďte všechny nezbytné zpracování pro každý objekt. Například následující kód vytvoří výčet <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekce <xref:System.TimeZoneInfo> objektů vrácených v kroku 1 a obsahuje zobrazovaný název jednotlivých časových pásmech na konzole.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Chcete-li uživateli zprostředkovali seznam časových pásem přítomných v místním systému

1. Volání <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metody. Metoda vrátí obecnou <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekce <xref:System.TimeZoneInfo> objekty.

2. Přiřadit kolekci vrácené v kroku 1, a `DataSource` vlastnost systému Windows forms nebo technologii ASP.NET ovládací prvek seznamu.

3. Načíst <xref:System.TimeZoneInfo> objekt, který uživatel vybral.

V příkladu je uvedena ukázka pro aplikace Windows.

## <a name="example"></a>Příklad

V příkladu spustí aplikaci Windows, která zobrazuje časových pásem definovaných v rámci systému v seznamu. Následně příklad zobrazí dialogové okno, které obsahuje hodnotu <xref:System.TimeZoneInfo.DisplayName%2A> vlastnost v objektu časové pásmo vybraný uživatelem.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Nejvíce seznamu ovládacích prvků (například <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> nebo <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> ovládací prvek) umožňují přiřadit kolekci objektových proměnných na jejich `DataSource` , dokud tuto kolekci implementuje vlastnost <xref:System.Collections.IEnumerable> rozhraní. (Obecné <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> třída.) Ovládací prvek pro zobrazení jednotlivých objektů v kolekci, volá tento objekt `ToString` metoda extrahování řetězec, který se používá k reprezentaci objektu. V případě třídy <xref:System.TimeZoneInfo> objekty, `ToString` vrátí metoda <xref:System.TimeZoneInfo> zobrazovaný název objektu (hodnota jeho <xref:System.TimeZoneInfo.DisplayName%2A> vlastnost).

> [!NOTE]
> Protože ovládacích prvcích seznam volání objektu `ToString` metodu, můžete přiřadit kolekci <xref:System.TimeZoneInfo> objekty do ovládacího prvku, mají ovládací prvek zobrazení smysluplný název pro každý objekt a načíst <xref:System.TimeZoneInfo> objekt, který uživatel vybral. Tím se eliminuje potřeba extrahovat řetězce pro každý objekt v kolekci, řetězec přiřadit kolekci, která je následně přiřazeno ovládacího prvku `DataSource` vlastnost načíst řetězec, který uživatel vybral a pak použít tento řetězec k extrakci objektu Popisuje ji. 

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

* Aby byly importované následující obory názvů:

  <xref:System> (v kódu jazyka C#)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Postupy: Ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
- [Postupy: Obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
