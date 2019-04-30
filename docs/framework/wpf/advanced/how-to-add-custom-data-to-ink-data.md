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
# <a name="how-to-add-custom-data-to-ink-data"></a><span data-ttu-id="fa8a5-102">Postupy: Přidání vlastních dat do dat rukopisu</span><span class="sxs-lookup"><span data-stu-id="fa8a5-102">How to: Add Custom Data to Ink Data</span></span>
<span data-ttu-id="fa8a5-103">Přidat vlastní data pro barvu, která se uloží při uložení rukopisu ve formátu inkoustu serializovat (ISF).</span><span class="sxs-lookup"><span data-stu-id="fa8a5-103">You can add custom data to ink that will be saved when the ink is saved as ink serialized format (ISF).</span></span>  <span data-ttu-id="fa8a5-104">Vlastní data, která můžete uložit <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, nebo <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="fa8a5-104">You can save the custom data to the <xref:System.Windows.Ink.DrawingAttributes>, the <xref:System.Windows.Ink.StrokeCollection>, or the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="fa8a5-105">Schopnost uložit vlastní data na třech objektech dává možnost se rozhodnout nejlepší místo pro uložení data.</span><span class="sxs-lookup"><span data-stu-id="fa8a5-105">Being able to save custom data on three objects gives you the ability to decide the best place to save the data.</span></span>  <span data-ttu-id="fa8a5-106">Všechny tři třídy podobným způsobem ukládání a přístup k vlastní data.</span><span class="sxs-lookup"><span data-stu-id="fa8a5-106">All three classes use similar methods to store and access custom data.</span></span>  
  
 <span data-ttu-id="fa8a5-107">Jako vlastní data lze uložit pouze následující typy:</span><span class="sxs-lookup"><span data-stu-id="fa8a5-107">Only the following types can be saved as custom data:</span></span>  
  
- <xref:System.Boolean>  
  
- <span data-ttu-id="fa8a5-108"><xref:System.Boolean>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-108"><xref:System.Boolean>[]</span></span>  
  
- <xref:System.Byte>  
  
- <span data-ttu-id="fa8a5-109"><xref:System.Byte>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-109"><xref:System.Byte>[]</span></span>  
  
- <xref:System.Char>  
  
- <span data-ttu-id="fa8a5-110"><xref:System.Char>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-110"><xref:System.Char>[]</span></span>  
  
- <xref:System.DateTime>  
  
- <span data-ttu-id="fa8a5-111"><xref:System.DateTime>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-111"><xref:System.DateTime>[]</span></span>  
  
- <xref:System.Decimal>  
  
- <span data-ttu-id="fa8a5-112"><xref:System.Decimal>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-112"><xref:System.Decimal>[]</span></span>  
  
- <xref:System.Double>  
  
- <span data-ttu-id="fa8a5-113"><xref:System.Double>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-113"><xref:System.Double>[]</span></span>  
  
- <xref:System.Int16>  
  
- <span data-ttu-id="fa8a5-114"><xref:System.Int16>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-114"><xref:System.Int16>[]</span></span>  
  
- <xref:System.Int32>  
  
- <span data-ttu-id="fa8a5-115"><xref:System.Int32>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-115"><xref:System.Int32>[]</span></span>  
  
- <xref:System.Int64>  
  
- <span data-ttu-id="fa8a5-116"><xref:System.Int64>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-116"><xref:System.Int64>[]</span></span>  
  
- <xref:System.Single>  
  
- <span data-ttu-id="fa8a5-117"><xref:System.Single>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-117"><xref:System.Single>[]</span></span>  
  
- <xref:System.String>  
  
- <xref:System.UInt16>  
  
- <span data-ttu-id="fa8a5-118"><xref:System.UInt16>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-118"><xref:System.UInt16>[]</span></span>  
  
- <xref:System.UInt32>  
  
- <span data-ttu-id="fa8a5-119"><xref:System.UInt32>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-119"><xref:System.UInt32>[]</span></span>  
  
- <xref:System.UInt64>  
  
- <span data-ttu-id="fa8a5-120"><xref:System.UInt64>[]</span><span class="sxs-lookup"><span data-stu-id="fa8a5-120"><xref:System.UInt64>[]</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa8a5-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa8a5-121">Example</span></span>  
 <span data-ttu-id="fa8a5-122">Následující příklad ukazuje, jak přidat a načíst vlastní data <xref:System.Windows.Ink.StrokeCollection>.</span><span class="sxs-lookup"><span data-stu-id="fa8a5-122">The following example demonstrates how to add and retrieve custom data from a <xref:System.Windows.Ink.StrokeCollection>.</span></span>  
  
 [!code-csharp[HowToAddCustomDataToInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 <span data-ttu-id="fa8a5-123">Následující příklad vytvoří aplikaci, která se zobrazí <xref:System.Windows.Controls.InkCanvas> a dvě tlačítka.</span><span class="sxs-lookup"><span data-stu-id="fa8a5-123">The following example creates an application that displays an <xref:System.Windows.Controls.InkCanvas> and two buttons.</span></span>  <span data-ttu-id="fa8a5-124">Tlačítko, `switchAuthor`, umožňuje používat dva různí tvůrci dva pera.</span><span class="sxs-lookup"><span data-stu-id="fa8a5-124">The button, `switchAuthor`, enables two pens to be used by two different authors.</span></span>  <span data-ttu-id="fa8a5-125">Tlačítko `changePenColors` změní barvu každého tahu na <xref:System.Windows.Controls.InkCanvas> podle autora.</span><span class="sxs-lookup"><span data-stu-id="fa8a5-125">The button `changePenColors` changes the color of each stroke on the <xref:System.Windows.Controls.InkCanvas> according to the author.</span></span>  <span data-ttu-id="fa8a5-126">Aplikace definuje dvě <xref:System.Windows.Ink.DrawingAttributes> objektů a přidá vlastní vlastnost pro každý z nich, která určuje, které autor nakreslili <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="fa8a5-126">The application defines two <xref:System.Windows.Ink.DrawingAttributes> objects and adds a custom property to each one that indicates which author drew the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="fa8a5-127">Když uživatel klepne `changePenColors`, aplikace změní vzhled objektu stroke podle hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fa8a5-127">When the user clicks `changePenColors`, the application changes the appearance of the stroke according to the value of the custom property.</span></span>  
  
 [!code-xaml[HowToAddCustomDataToInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
