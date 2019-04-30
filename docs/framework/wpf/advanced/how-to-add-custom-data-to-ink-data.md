---
title: 'Postupy: Přidání vlastních dat do dat rukopisu'
ms.date: 03/30/2017
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
ms.openlocfilehash: c524e30943a21426e2e5e8fe6ae009999924fead
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777049"
---
# <a name="how-to-add-custom-data-to-ink-data"></a>Postupy: Přidání vlastních dat do dat rukopisu
Přidat vlastní data pro barvu, která se uloží při uložení rukopisu ve formátu inkoustu serializovat (ISF).  Vlastní data, která můžete uložit <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, nebo <xref:System.Windows.Ink.Stroke>.  Schopnost uložit vlastní data na třech objektech dává možnost se rozhodnout nejlepší místo pro uložení data.  Všechny tři třídy podobným způsobem ukládání a přístup k vlastní data.  
  
 Jako vlastní data lze uložit pouze následující typy:  
  
- <xref:System.Boolean>  
  
- <xref:System.Boolean>[]  
  
- <xref:System.Byte>  
  
- <xref:System.Byte>[]  
  
- <xref:System.Char>  
  
- <xref:System.Char>[]  
  
- <xref:System.DateTime>  
  
- <xref:System.DateTime>[]  
  
- <xref:System.Decimal>  
  
- <xref:System.Decimal>[]  
  
- <xref:System.Double>  
  
- <xref:System.Double>[]  
  
- <xref:System.Int16>  
  
- <xref:System.Int16>[]  
  
- <xref:System.Int32>  
  
- <xref:System.Int32>[]  
  
- <xref:System.Int64>  
  
- <xref:System.Int64>[]  
  
- <xref:System.Single>  
  
- <xref:System.Single>[]  
  
- <xref:System.String>  
  
- <xref:System.UInt16>  
  
- <xref:System.UInt16>[]  
  
- <xref:System.UInt32>  
  
- <xref:System.UInt32>[]  
  
- <xref:System.UInt64>  
  
- <xref:System.UInt64>[]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přidat a načíst vlastní data <xref:System.Windows.Ink.StrokeCollection>.  
  
 [!code-csharp[HowToAddCustomDataToInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 Následující příklad vytvoří aplikaci, která se zobrazí <xref:System.Windows.Controls.InkCanvas> a dvě tlačítka.  Tlačítko, `switchAuthor`, umožňuje používat dva různí tvůrci dva pera.  Tlačítko `changePenColors` změní barvu každého tahu na <xref:System.Windows.Controls.InkCanvas> podle autora.  Aplikace definuje dvě <xref:System.Windows.Ink.DrawingAttributes> objektů a přidá vlastní vlastnost pro každý z nich, která určuje, které autor nakreslili <xref:System.Windows.Ink.Stroke>.  Když uživatel klepne `changePenColors`, aplikace změní vzhled objektu stroke podle hodnoty vlastnosti.  
  
 [!code-xaml[HowToAddCustomDataToInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
