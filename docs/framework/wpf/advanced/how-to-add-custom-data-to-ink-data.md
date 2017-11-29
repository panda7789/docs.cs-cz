---
title: "Postupy: Přidání vlastních dat do dat inkoustu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f266f3c98ca64c80ccbb669a1cc646321754579f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-add-custom-data-to-ink-data"></a>Postupy: Přidání vlastních dat do dat inkoustu
Přidáním vlastních dat do barvu, která bude uloženo při uložení rukopisu rukopisu serializovat formát (Serialized Format).  Můžete uložit vlastní data, která mají <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, nebo <xref:System.Windows.Ink.Stroke>.  Schopnost uložit vlastní data na tři objekty vám dává možnost k rozhodování o nejlepší místo k uložení dat.  Všechny tři třídy podobné metody používat k ukládání a přístup k vlastní data.  
  
 Jako vlastní data lze uložit pouze následující typy:  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Boolean>[]  
  
-   <xref:System.Byte>  
  
-   <xref:System.Byte>[]  
  
-   <xref:System.Char>  
  
-   <xref:System.Char>[]  
  
-   <xref:System.DateTime>  
  
-   <xref:System.DateTime>[]  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Decimal>[]  
  
-   <xref:System.Double>  
  
-   <xref:System.Double>[]  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int16>[]  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int32>[]  
  
-   <xref:System.Int64>  
  
-   <xref:System.Int64>[]  
  
-   <xref:System.Single>  
  
-   <xref:System.Single>[]  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <xref:System.UInt16>[]  
  
-   <xref:System.UInt32>  
  
-   <xref:System.UInt32>[]  
  
-   <xref:System.UInt64>  
  
-   <xref:System.UInt64>[]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přidat a načíst vlastní data ze <xref:System.Windows.Ink.StrokeCollection>.  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 Následující příklad vytvoří aplikaci, která zobrazuje <xref:System.Windows.Controls.InkCanvas> a dvě tlačítka.  Tlačítko, `switchAuthor`, umožňuje dvě pera, který se má použít dvě různé autory.  Tlačítko `changePenColors` změní barvu každého tahu na <xref:System.Windows.Controls.InkCanvas> podle autora.  Aplikace definuje dvě <xref:System.Windows.Ink.DrawingAttributes> objekty a přidá vlastní vlastnost pro každé z nich určující, které autor obrázek <xref:System.Windows.Ink.Stroke>.  Když uživatel klikne na `changePenColors`, aplikace mění vzhled tahu podle hodnotu vlastní vlastnosti.  
  
 [!code-xaml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
