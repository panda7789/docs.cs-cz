---
title: Použití písem a textu
ms.date: 03/30/2017
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
ms.openlocfilehash: d157b51e24009d847dede9ea6a9f81c8898c5b06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526260"
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="9993d-102">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="9993d-102">Using Fonts and Text</span></span>
<span data-ttu-id="9993d-103">Existuje několik tříd, které nabízí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pro kreslení textu v rozhraní Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9993d-103">There are several classes offered by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text on Windows Forms.</span></span> <span data-ttu-id="9993d-104">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Třída obsahuje několik <xref:System.Drawing.Graphics.DrawString%2A> metody, které vám umožní určit různé funkce textu, jako je například umístění, ohraničujícího rámečku, písma a formát.</span><span class="sxs-lookup"><span data-stu-id="9993d-104">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="9993d-105">Kromě toho můžete kreslení a měřit textu s [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pomocí statické <xref:System.Windows.Forms.TextRenderer.DrawText%2A> a <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> metody nabízené `TextRenderer` třídy.</span><span class="sxs-lookup"><span data-stu-id="9993d-105">In addition, you can draw and measure text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="9993d-106">[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Metody taky umožňují určit umístění, písma a formát.</span><span class="sxs-lookup"><span data-stu-id="9993d-106">The [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="9993d-107">Můžete buď [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] nebo [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pro vykreslování textu; však [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] obecně nabízí lepší výkon a přesnější měření text.</span><span class="sxs-lookup"><span data-stu-id="9993d-107">You can choose either [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] or [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] for text rendering; however, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="9993d-108">Zahrnout další třídy, které přispívají k vykreslování textu `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, a `TextFormatFlags`.</span><span class="sxs-lookup"><span data-stu-id="9993d-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9993d-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9993d-109">In This Section</span></span>  
 [<span data-ttu-id="9993d-110">Postupy: Vytváření rodin písem a písem</span><span class="sxs-lookup"><span data-stu-id="9993d-110">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="9993d-111">Ukazuje, jak vytvořit `Font` a `FontFamily` objekty.</span><span class="sxs-lookup"><span data-stu-id="9993d-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="9993d-112">Postupy: Kreslení textu v určeném umístění</span><span class="sxs-lookup"><span data-stu-id="9993d-112">How to: Draw Text at a Specified Location</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="9993d-113">Popisuje, jak kreslení textu v určitých umístění pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9993d-113">Describes how to draw text in a certain location using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="9993d-114">Postupy: Kreslení zalomeného textu do obdélníku</span><span class="sxs-lookup"><span data-stu-id="9993d-114">How to: Draw Wrapped Text in a Rectangle</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="9993d-115">Vysvětluje, jak kreslení textu v obdélníku pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9993d-115">Explains how to draw text in a rectangle using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="9993d-116">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="9993d-116">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="9993d-117">Ukazuje, jak používat [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pro kreslení textu.</span><span class="sxs-lookup"><span data-stu-id="9993d-117">Demonstrates how to use [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text.</span></span>  
  
 [<span data-ttu-id="9993d-118">Postupy: Zarovnání vykresleného textu</span><span class="sxs-lookup"><span data-stu-id="9993d-118">How to: Align Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 <span data-ttu-id="9993d-119">Ukazuje, jak k formátování [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.</span><span class="sxs-lookup"><span data-stu-id="9993d-119">Shows how to format [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.</span></span>  
  
 [<span data-ttu-id="9993d-120">Postupy: Vytvoření svislého textu</span><span class="sxs-lookup"><span data-stu-id="9993d-120">How to: Create Vertical Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 <span data-ttu-id="9993d-121">Popisuje, jak kreslení svisle zarovnaný textu s [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9993d-121">Describes how to draw vertically aligned text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="9993d-122">Postupy: Nastavení zarážek v kresleném textu</span><span class="sxs-lookup"><span data-stu-id="9993d-122">How to: Set Tab Stops in Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="9993d-123">Ukazuje, jak kreslení textu pomocí zarážek tabulátoru s [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9993d-123">Shows how draw text with tab stops with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="9993d-124">Postupy: Výčet instalovaných písem</span><span class="sxs-lookup"><span data-stu-id="9993d-124">How to: Enumerate Installed Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="9993d-125">Vysvětluje, jak zobrazit názvy instalovaných písem.</span><span class="sxs-lookup"><span data-stu-id="9993d-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="9993d-126">Postupy: Vytvoření soukromé kolekce písem</span><span class="sxs-lookup"><span data-stu-id="9993d-126">How to: Create a Private Font Collection</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="9993d-127">Popisuje postup vytvoření <xref:System.Drawing.Text.PrivateFontCollection> objektu.</span><span class="sxs-lookup"><span data-stu-id="9993d-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="9993d-128">Postupy: Získání metriky písma</span><span class="sxs-lookup"><span data-stu-id="9993d-128">How to: Obtain Font Metrics</span></span>](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 <span data-ttu-id="9993d-129">Ukazuje, jak získat metriky písma, jako je například výstup buňky a klesání.</span><span class="sxs-lookup"><span data-stu-id="9993d-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="9993d-130">Postupy: Použití vyhlazení u textu</span><span class="sxs-lookup"><span data-stu-id="9993d-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="9993d-131">Tento článek vysvětluje použití vyhlazení při kreslení textu.</span><span class="sxs-lookup"><span data-stu-id="9993d-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9993d-132">Odkaz</span><span class="sxs-lookup"><span data-stu-id="9993d-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="9993d-133">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="9993d-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="9993d-134">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="9993d-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="9993d-135">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="9993d-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="9993d-136">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="9993d-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="9993d-137">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="9993d-137">Describes this class and contains links to all of its members.</span></span>
