---
title: "Postupy: Vytváření rodin písem a písem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e152c525550554082d7d6c38a972ccc150adabb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-construct-font-families-and-fonts"></a><span data-ttu-id="5589a-102">Postupy: Vytváření rodin písem a písem</span><span class="sxs-lookup"><span data-stu-id="5589a-102">How to: Construct Font Families and Fonts</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="5589a-103">skupiny se stejného řezu, ale s různými styly písem do rodiny písem.</span><span class="sxs-lookup"><span data-stu-id="5589a-103"> groups fonts with the same typeface but different styles into font families.</span></span> <span data-ttu-id="5589a-104">Například typu Arial obsahuje následující písma:</span><span class="sxs-lookup"><span data-stu-id="5589a-104">For example, the Arial font family contains the following fonts:</span></span>  
  
-   <span data-ttu-id="5589a-105">Arial Regular</span><span class="sxs-lookup"><span data-stu-id="5589a-105">Arial Regular</span></span>  
  
-   <span data-ttu-id="5589a-106">Arial Bold</span><span class="sxs-lookup"><span data-stu-id="5589a-106">Arial Bold</span></span>  
  
-   <span data-ttu-id="5589a-107">Arial kurzíva</span><span class="sxs-lookup"><span data-stu-id="5589a-107">Arial Italic</span></span>  
  
-   <span data-ttu-id="5589a-108">Arial tučné, kurzíva</span><span class="sxs-lookup"><span data-stu-id="5589a-108">Arial Bold Italic</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="5589a-109">používá čtyři stylů pro formulář rodin: obyčejný, tučné, kurzíva a tučné kurzívy.</span><span class="sxs-lookup"><span data-stu-id="5589a-109"> uses four styles to form families: regular, bold, italic, and bold italic.</span></span> <span data-ttu-id="5589a-110">Přídavných jmen jako *zúžit* a *zaokrouhlené* nejsou považovány za styly; namísto jsou součástí název rodiny.</span><span class="sxs-lookup"><span data-stu-id="5589a-110">Adjectives such as *narrow* and *rounded* are not considered styles; rather they are part of the family name.</span></span> <span data-ttu-id="5589a-111">Arial úzké je třeba v dané rodině písem s následující členy:</span><span class="sxs-lookup"><span data-stu-id="5589a-111">For example, Arial Narrow is a font family with the following members:</span></span>  
  
-   <span data-ttu-id="5589a-112">Arial úzké Regular</span><span class="sxs-lookup"><span data-stu-id="5589a-112">Arial Narrow Regular</span></span>  
  
-   <span data-ttu-id="5589a-113">Arial úzké tučně</span><span class="sxs-lookup"><span data-stu-id="5589a-113">Arial Narrow Bold</span></span>  
  
-   <span data-ttu-id="5589a-114">Arial úzké kurzíva</span><span class="sxs-lookup"><span data-stu-id="5589a-114">Arial Narrow Italic</span></span>  
  
-   <span data-ttu-id="5589a-115">Arial úzké tučné kurzíva</span><span class="sxs-lookup"><span data-stu-id="5589a-115">Arial Narrow Bold Italic</span></span>  
  
 <span data-ttu-id="5589a-116">Předtím, než můžete kreslení textu pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], budete muset vytvořit <xref:System.Drawing.FontFamily> objektu a <xref:System.Drawing.Font> objektu.</span><span class="sxs-lookup"><span data-stu-id="5589a-116">Before you can draw text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to construct a <xref:System.Drawing.FontFamily> object and a <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="5589a-117"><xref:System.Drawing.FontFamily> Objektu Určuje řez písma (například Arial) a <xref:System.Drawing.Font> objektu určuje velikost, stylu a jednotky.</span><span class="sxs-lookup"><span data-stu-id="5589a-117">The <xref:System.Drawing.FontFamily> object specifies the typeface (for example, Arial), and the <xref:System.Drawing.Font> object specifies the size, style, and units.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5589a-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="5589a-118">Example</span></span>  
 <span data-ttu-id="5589a-119">Následující příklad vytvoří regulární styl písmo Arial o velikosti 16 pixelů.</span><span class="sxs-lookup"><span data-stu-id="5589a-119">The following example constructs a regular style Arial font with a size of 16 pixels.</span></span> <span data-ttu-id="5589a-120">V následujícím kódu, první argument předaný <xref:System.Drawing.Font.%23ctor%2A> konstruktor je <xref:System.Drawing.FontFamily> objektu.</span><span class="sxs-lookup"><span data-stu-id="5589a-120">In the following code, the first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the <xref:System.Drawing.FontFamily> object.</span></span> <span data-ttu-id="5589a-121">Druhý argument určuje velikost písma. měřeno v jednotkách identifikovaný čtvrtý argument.</span><span class="sxs-lookup"><span data-stu-id="5589a-121">The second argument specifies the size of the font measured in units identified by the fourth argument.</span></span> <span data-ttu-id="5589a-122">Třetí argument identifikuje styl.</span><span class="sxs-lookup"><span data-stu-id="5589a-122">The third argument identifies the style.</span></span>  
  
 <span data-ttu-id="5589a-123"><xref:System.Drawing.GraphicsUnit.Pixel>je členem skupiny <xref:System.Drawing.GraphicsUnit> výčtu a <xref:System.Drawing.FontStyle.Regular> je členem skupiny <xref:System.Drawing.FontStyle> výčtu.</span><span class="sxs-lookup"><span data-stu-id="5589a-123"><xref:System.Drawing.GraphicsUnit.Pixel> is a member of the <xref:System.Drawing.GraphicsUnit> enumeration, and <xref:System.Drawing.FontStyle.Regular> is a member of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5589a-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5589a-124">Compiling the Code</span></span>  
 <span data-ttu-id="5589a-125">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="5589a-125">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5589a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5589a-126">See Also</span></span>  
 [<span data-ttu-id="5589a-127">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="5589a-127">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="5589a-128">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5589a-128">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
