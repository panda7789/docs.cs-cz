---
title: 'Postupy: Vytváření rodin písem a písem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: b651671e525ae5cfc365a392b96d258ac835a21c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708551"
---
# <a name="how-to-construct-font-families-and-fonts"></a><span data-ttu-id="2582b-102">Postupy: Vytváření rodin písem a písem</span><span class="sxs-lookup"><span data-stu-id="2582b-102">How to: Construct Font Families and Fonts</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="2582b-103">písma se stejný druh písma šifry, ale různé styly seskupí do rodiny písem.</span><span class="sxs-lookup"><span data-stu-id="2582b-103">groups fonts with the same typeface but different styles into font families.</span></span> <span data-ttu-id="2582b-104">Řada Arial písmo obsahuje například následující písma:</span><span class="sxs-lookup"><span data-stu-id="2582b-104">For example, the Arial font family contains the following fonts:</span></span>  
  
-   <span data-ttu-id="2582b-105">Arial standardní</span><span class="sxs-lookup"><span data-stu-id="2582b-105">Arial Regular</span></span>  
  
-   <span data-ttu-id="2582b-106">Arial tučného písma</span><span class="sxs-lookup"><span data-stu-id="2582b-106">Arial Bold</span></span>  
  
-   <span data-ttu-id="2582b-107">Arial kurzíva</span><span class="sxs-lookup"><span data-stu-id="2582b-107">Arial Italic</span></span>  
  
-   <span data-ttu-id="2582b-108">Arial tučná kurzíva</span><span class="sxs-lookup"><span data-stu-id="2582b-108">Arial Bold Italic</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="2582b-109">používá čtyři styly formuláře rodin: pravidelných, tučné, kurzíva a Tučná kurzíva.</span><span class="sxs-lookup"><span data-stu-id="2582b-109">uses four styles to form families: regular, bold, italic, and bold italic.</span></span> <span data-ttu-id="2582b-110">Přídavných jmen, jako *zúžit* a *zaokrouhlí* nejsou považovány za styly; místo toho jsou součástí název rodiny.</span><span class="sxs-lookup"><span data-stu-id="2582b-110">Adjectives such as *narrow* and *rounded* are not considered styles; rather they are part of the family name.</span></span> <span data-ttu-id="2582b-111">Arial úzký například je rodina písem s následující členy:</span><span class="sxs-lookup"><span data-stu-id="2582b-111">For example, Arial Narrow is a font family with the following members:</span></span>  
  
-   <span data-ttu-id="2582b-112">Arial úzký standardní</span><span class="sxs-lookup"><span data-stu-id="2582b-112">Arial Narrow Regular</span></span>  
  
-   <span data-ttu-id="2582b-113">Arial úzký tučného písma</span><span class="sxs-lookup"><span data-stu-id="2582b-113">Arial Narrow Bold</span></span>  
  
-   <span data-ttu-id="2582b-114">Arial úzký kurzíva</span><span class="sxs-lookup"><span data-stu-id="2582b-114">Arial Narrow Italic</span></span>  
  
-   <span data-ttu-id="2582b-115">Arial úzký tučná kurzíva</span><span class="sxs-lookup"><span data-stu-id="2582b-115">Arial Narrow Bold Italic</span></span>  
  
 <span data-ttu-id="2582b-116">Předtím, než můžete kreslení textu pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], je potřeba vytvořit <xref:System.Drawing.FontFamily> objektu a <xref:System.Drawing.Font> objektu.</span><span class="sxs-lookup"><span data-stu-id="2582b-116">Before you can draw text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to construct a <xref:System.Drawing.FontFamily> object and a <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="2582b-117"><xref:System.Drawing.FontFamily> Objekt Určuje řez písma (například Arial) a <xref:System.Drawing.Font> objekt určuje velikost, styl a jednotky.</span><span class="sxs-lookup"><span data-stu-id="2582b-117">The <xref:System.Drawing.FontFamily> object specifies the typeface (for example, Arial), and the <xref:System.Drawing.Font> object specifies the size, style, and units.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2582b-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="2582b-118">Example</span></span>  
 <span data-ttu-id="2582b-119">Následující příklad vytvoří regulárních styl Arial písmo o velikosti 16 pixelů.</span><span class="sxs-lookup"><span data-stu-id="2582b-119">The following example constructs a regular style Arial font with a size of 16 pixels.</span></span> <span data-ttu-id="2582b-120">V následujícím kódu, první argument předaný metodě <xref:System.Drawing.Font.%23ctor%2A> konstruktor je <xref:System.Drawing.FontFamily> objektu.</span><span class="sxs-lookup"><span data-stu-id="2582b-120">In the following code, the first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the <xref:System.Drawing.FontFamily> object.</span></span> <span data-ttu-id="2582b-121">Druhý argument určuje velikost písma měřenou v jednotkách identifikovaný čtvrtý argument.</span><span class="sxs-lookup"><span data-stu-id="2582b-121">The second argument specifies the size of the font measured in units identified by the fourth argument.</span></span> <span data-ttu-id="2582b-122">Třetí argument určuje styl.</span><span class="sxs-lookup"><span data-stu-id="2582b-122">The third argument identifies the style.</span></span>  
  
 <span data-ttu-id="2582b-123"><xref:System.Drawing.GraphicsUnit.Pixel> je členem skupiny <xref:System.Drawing.GraphicsUnit> výčtu, a <xref:System.Drawing.FontStyle.Regular> je členem skupiny <xref:System.Drawing.FontStyle> výčtu.</span><span class="sxs-lookup"><span data-stu-id="2582b-123"><xref:System.Drawing.GraphicsUnit.Pixel> is a member of the <xref:System.Drawing.GraphicsUnit> enumeration, and <xref:System.Drawing.FontStyle.Regular> is a member of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2582b-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2582b-124">Compiling the Code</span></span>  
 <span data-ttu-id="2582b-125">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="2582b-125">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2582b-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2582b-126">See also</span></span>
- [<span data-ttu-id="2582b-127">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="2582b-127">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="2582b-128">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2582b-128">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
