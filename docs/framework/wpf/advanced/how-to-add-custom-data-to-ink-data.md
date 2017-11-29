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
# <a name="how-to-add-custom-data-to-ink-data"></a><span data-ttu-id="d1804-102">Postupy: Přidání vlastních dat do dat inkoustu</span><span class="sxs-lookup"><span data-stu-id="d1804-102">How to: Add Custom Data to Ink Data</span></span>
<span data-ttu-id="d1804-103">Přidáním vlastních dat do barvu, která bude uloženo při uložení rukopisu rukopisu serializovat formát (Serialized Format).</span><span class="sxs-lookup"><span data-stu-id="d1804-103">You can add custom data to ink that will be saved when the ink is saved as ink serialized format (ISF).</span></span>  <span data-ttu-id="d1804-104">Můžete uložit vlastní data, která mají <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>, nebo <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="d1804-104">You can save the custom data to the <xref:System.Windows.Ink.DrawingAttributes>, the <xref:System.Windows.Ink.StrokeCollection>, or the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="d1804-105">Schopnost uložit vlastní data na tři objekty vám dává možnost k rozhodování o nejlepší místo k uložení dat.</span><span class="sxs-lookup"><span data-stu-id="d1804-105">Being able to save custom data on three objects gives you the ability to decide the best place to save the data.</span></span>  <span data-ttu-id="d1804-106">Všechny tři třídy podobné metody používat k ukládání a přístup k vlastní data.</span><span class="sxs-lookup"><span data-stu-id="d1804-106">All three classes use similar methods to store and access custom data.</span></span>  
  
 <span data-ttu-id="d1804-107">Jako vlastní data lze uložit pouze následující typy:</span><span class="sxs-lookup"><span data-stu-id="d1804-107">Only the following types can be saved as custom data:</span></span>  
  
-   <xref:System.Boolean>  
  
-   <span data-ttu-id="d1804-108"><xref:System.Boolean>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-108"><xref:System.Boolean>[]</span></span>  
  
-   <xref:System.Byte>  
  
-   <span data-ttu-id="d1804-109"><xref:System.Byte>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-109"><xref:System.Byte>[]</span></span>  
  
-   <xref:System.Char>  
  
-   <span data-ttu-id="d1804-110"><xref:System.Char>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-110"><xref:System.Char>[]</span></span>  
  
-   <xref:System.DateTime>  
  
-   <span data-ttu-id="d1804-111"><xref:System.DateTime>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-111"><xref:System.DateTime>[]</span></span>  
  
-   <xref:System.Decimal>  
  
-   <span data-ttu-id="d1804-112"><xref:System.Decimal>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-112"><xref:System.Decimal>[]</span></span>  
  
-   <xref:System.Double>  
  
-   <span data-ttu-id="d1804-113"><xref:System.Double>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-113"><xref:System.Double>[]</span></span>  
  
-   <xref:System.Int16>  
  
-   <span data-ttu-id="d1804-114"><xref:System.Int16>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-114"><xref:System.Int16>[]</span></span>  
  
-   <xref:System.Int32>  
  
-   <span data-ttu-id="d1804-115"><xref:System.Int32>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-115"><xref:System.Int32>[]</span></span>  
  
-   <xref:System.Int64>  
  
-   <span data-ttu-id="d1804-116"><xref:System.Int64>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-116"><xref:System.Int64>[]</span></span>  
  
-   <xref:System.Single>  
  
-   <span data-ttu-id="d1804-117"><xref:System.Single>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-117"><xref:System.Single>[]</span></span>  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <span data-ttu-id="d1804-118"><xref:System.UInt16>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-118"><xref:System.UInt16>[]</span></span>  
  
-   <xref:System.UInt32>  
  
-   <span data-ttu-id="d1804-119"><xref:System.UInt32>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-119"><xref:System.UInt32>[]</span></span>  
  
-   <xref:System.UInt64>  
  
-   <span data-ttu-id="d1804-120"><xref:System.UInt64>[]</span><span class="sxs-lookup"><span data-stu-id="d1804-120"><xref:System.UInt64>[]</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1804-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1804-121">Example</span></span>  
 <span data-ttu-id="d1804-122">Následující příklad ukazuje, jak přidat a načíst vlastní data ze <xref:System.Windows.Ink.StrokeCollection>.</span><span class="sxs-lookup"><span data-stu-id="d1804-122">The following example demonstrates how to add and retrieve custom data from a <xref:System.Windows.Ink.StrokeCollection>.</span></span>  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 <span data-ttu-id="d1804-123">Následující příklad vytvoří aplikaci, která zobrazuje <xref:System.Windows.Controls.InkCanvas> a dvě tlačítka.</span><span class="sxs-lookup"><span data-stu-id="d1804-123">The following example creates an application that displays an <xref:System.Windows.Controls.InkCanvas> and two buttons.</span></span>  <span data-ttu-id="d1804-124">Tlačítko, `switchAuthor`, umožňuje dvě pera, který se má použít dvě různé autory.</span><span class="sxs-lookup"><span data-stu-id="d1804-124">The button, `switchAuthor`, enables two pens to be used by two different authors.</span></span>  <span data-ttu-id="d1804-125">Tlačítko `changePenColors` změní barvu každého tahu na <xref:System.Windows.Controls.InkCanvas> podle autora.</span><span class="sxs-lookup"><span data-stu-id="d1804-125">The button `changePenColors` changes the color of each stroke on the <xref:System.Windows.Controls.InkCanvas> according to the author.</span></span>  <span data-ttu-id="d1804-126">Aplikace definuje dvě <xref:System.Windows.Ink.DrawingAttributes> objekty a přidá vlastní vlastnost pro každé z nich určující, které autor obrázek <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="d1804-126">The application defines two <xref:System.Windows.Ink.DrawingAttributes> objects and adds a custom property to each one that indicates which author drew the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="d1804-127">Když uživatel klikne na `changePenColors`, aplikace mění vzhled tahu podle hodnotu vlastní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d1804-127">When the user clicks `changePenColors`, the application changes the appearance of the stroke according to the value of the custom property.</span></span>  
  
 [!code-xaml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
