---
title: "Postupy: Použití matice barev k transformaci jedné barvy"
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
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6c9273102dc8e8f0fe6be3e31d0f0b6e570c7af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a><span data-ttu-id="6d3d9-102">Postupy: Použití matice barev k transformaci jedné barvy</span><span class="sxs-lookup"><span data-stu-id="6d3d9-102">How to: Use a Color Matrix to Transform a Single Color</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="6d3d9-103">poskytuje <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> třídy pro ukládání a manipulace s nimi bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-103"> provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="6d3d9-104"><xref:System.Drawing.Image>a <xref:System.Drawing.Bitmap> objekty jako 32bitové číslo úložiště barva každý pixelů: 8 bitů jednotlivých červená, zelená, modrá a alfa.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-104"><xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects store the color of each pixel as a 32-bit number: 8 bits each for red, green, blue, and alpha.</span></span> <span data-ttu-id="6d3d9-105">Každý ze čtyř součástí je číslo od 0 do 255, kde 0 představuje žádné intenzitou a představující úplné intenzitou 255.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-105">Each of the four components is a number from 0 through 255, with 0 representing no intensity and 255 representing full intensity.</span></span> <span data-ttu-id="6d3d9-106">Komponentu alfa Určuje průhlednost barvy: 0 je zcela průhledné a je plně neprůhledného 255.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-106">The alpha component specifies the transparency of the color: 0 is fully transparent, and 255 is fully opaque.</span></span>  
  
 <span data-ttu-id="6d3d9-107">Barva vektor je 4-řazené kolekce členů ve formuláři (červená, zelená, modrá, alpha).</span><span class="sxs-lookup"><span data-stu-id="6d3d9-107">A color vector is a 4-tuple of the form (red, green, blue, alpha).</span></span> <span data-ttu-id="6d3d9-108">Například vektoru barvu (0, 255, 0, 255) představuje neprůhledného barvu, která nemá žádné red nebo blue, ale má zelená úplné intenzitou.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-108">For example, the color vector (0, 255, 0, 255) represents an opaque color that has no red or blue, but has green at full intensity.</span></span>  
  
 <span data-ttu-id="6d3d9-109">Jiné konvence pro představující barvy používá číslo 1 pro úplné intenzitou.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-109">Another convention for representing colors uses the number 1 for full intensity.</span></span> <span data-ttu-id="6d3d9-110">Pomocí této konvence, by barvu popsané v předchozím odstavci reprezentované pomocí vektoru (0, 1, 0, 1).</span><span class="sxs-lookup"><span data-stu-id="6d3d9-110">Using that convention, the color described in the preceding paragraph would be represented by the vector (0, 1, 0, 1).</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="6d3d9-111">Při provádění transformací barev, používá jako úplné intenzitou konvenci 1.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-111"> uses the convention of 1 as full intensity when it performs color transformations.</span></span>  
  
 <span data-ttu-id="6d3d9-112">Lineární transformace (otáčení, změnu velikosti a podobně) můžete použít barvu Vektorům vynásobením vektory barvu podle matice 4 x 4.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-112">You can apply linear transformations (rotation, scaling, and the like) to color vectors by multiplying the color vectors by a 4×4 matrix.</span></span> <span data-ttu-id="6d3d9-113">Matice 4 x 4 však nelze použít pro překlad (nelineární).</span><span class="sxs-lookup"><span data-stu-id="6d3d9-113">However, you cannot use a 4×4 matrix to perform a translation (nonlinear).</span></span> <span data-ttu-id="6d3d9-114">Pokud přidáte do každé vektorů barva fiktivní páté souřadnice (například číslo 1), můžete použít libovolnou kombinaci lineární transformace a překlady matice 5 × 5.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-114">If you add a dummy fifth coordinate (for example, the number 1) to each of the color vectors, you can use a 5×5 matrix to apply any combination of linear transformations and translations.</span></span> <span data-ttu-id="6d3d9-115">Transformace skládající se z lineární transformace, za nímž následuje překlad nazývá afinní transformace.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-115">A transformation consisting of a linear transformation followed by a translation is called an affine transformation.</span></span>  
  
 <span data-ttu-id="6d3d9-116">Předpokládejme například, že chcete spustit s barvou (0,2, 0,0, 0.4, 1.0) a použít následující transformace:</span><span class="sxs-lookup"><span data-stu-id="6d3d9-116">For example, suppose you want to start with the color (0.2, 0.0, 0.4, 1.0) and apply the following transformations:</span></span>  
  
1.  <span data-ttu-id="6d3d9-117">Double red součásti</span><span class="sxs-lookup"><span data-stu-id="6d3d9-117">Double the red component</span></span>  
  
2.  <span data-ttu-id="6d3d9-118">Přidání do komponenty červené, zelené a modré 0,2</span><span class="sxs-lookup"><span data-stu-id="6d3d9-118">Add 0.2 to the red, green, and blue components</span></span>  
  
 <span data-ttu-id="6d3d9-119">Následující násobení matic provede dvojice transformace v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-119">The following matrix multiplication will perform the pair of transformations in the order listed.</span></span>  
  
 <span data-ttu-id="6d3d9-120">![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span><span class="sxs-lookup"><span data-stu-id="6d3d9-120">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span></span>  
  
 <span data-ttu-id="6d3d9-121">Elementy matice barev jsou indexované podle řádku a potom sloupce (počítáno od nuly).</span><span class="sxs-lookup"><span data-stu-id="6d3d9-121">The elements of a color matrix are indexed (zero-based) by row and then column.</span></span> <span data-ttu-id="6d3d9-122">Například záznam v páté řádků a třetí sloupec matice M odlišené M [4] [2].</span><span class="sxs-lookup"><span data-stu-id="6d3d9-122">For example, the entry in the fifth row and third column of matrix M is denoted by M[4][2].</span></span>  
  
 <span data-ttu-id="6d3d9-123">(Viz následující obrázek) matice identity 5 × 5 má hodnotami 1 na diagonálních a 0s everywhere else.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-123">The 5×5 identity matrix (shown in the following illustration) has 1s on the diagonal and 0s everywhere else.</span></span> <span data-ttu-id="6d3d9-124">Pokud jste barva vektoru vynásobit matice identity, barva vektoru se nezmění.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-124">If you multiply a color vector by the identity matrix, the color vector does not change.</span></span> <span data-ttu-id="6d3d9-125">Vhodný způsob k formuláři matice barev transformace je začínat matice identity a provedení malé změny, která vytvoří požadovanou transformaci.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-125">A convenient way to form the matrix of a color transformation is to start with the identity matrix and make a small change that produces the desired transformation.</span></span>  
  
 <span data-ttu-id="6d3d9-126">![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span><span class="sxs-lookup"><span data-stu-id="6d3d9-126">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span></span>  
  
 <span data-ttu-id="6d3d9-127">Podrobnější diskuzi o matice a transformace, v tématu [systém souřadnic a transformace](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="6d3d9-127">For a more detailed discussion of matrices and transformations, see [Coordinate Systems and Transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d3d9-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d3d9-128">Example</span></span>  
 <span data-ttu-id="6d3d9-129">V následujícím příkladu má obrázek, který je všechny jedné barvy (0,2, 0,0, 0.4, 1.0) a použije transformaci popsané v předchozích odstavcích.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-129">The following example takes an image that is all one color (0.2, 0.0, 0.4, 1.0) and applies the transformation described in the preceding paragraphs.</span></span>  
  
 <span data-ttu-id="6d3d9-130">Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii transformovaných na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-130">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="6d3d9-131">![Barvy](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span><span class="sxs-lookup"><span data-stu-id="6d3d9-131">![Colors](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span></span>  
  
 <span data-ttu-id="6d3d9-132">Kód v následujícím příkladu používá k provedení přebarvení následující kroky:</span><span class="sxs-lookup"><span data-stu-id="6d3d9-132">The code in the following example uses the following steps to perform the recoloring:</span></span>  
  
1.  <span data-ttu-id="6d3d9-133">Inicializace <xref:System.Drawing.Imaging.ColorMatrix> objektu.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-133">Initialize a <xref:System.Drawing.Imaging.ColorMatrix> object.</span></span>  
  
2.  <span data-ttu-id="6d3d9-134">Vytvoření <xref:System.Drawing.Imaging.ImageAttributes> objektu a předejte <xref:System.Drawing.Imaging.ColorMatrix> do objektu <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metodu <xref:System.Drawing.Imaging.ImageAttributes> objektu.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-134">Create an <xref:System.Drawing.Imaging.ImageAttributes> object and pass the <xref:System.Drawing.Imaging.ColorMatrix> object to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object.</span></span>  
  
3.  <span data-ttu-id="6d3d9-135">Předat <xref:System.Drawing.Imaging.ImageAttributes> do objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-135">Pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6d3d9-136">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6d3d9-136">Compiling the Code</span></span>  
 <span data-ttu-id="6d3d9-137">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6d3d9-137">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3d9-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d3d9-138">See Also</span></span>  
 [<span data-ttu-id="6d3d9-139">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="6d3d9-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="6d3d9-140">Systém souřadnic a transformace</span><span class="sxs-lookup"><span data-stu-id="6d3d9-140">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
