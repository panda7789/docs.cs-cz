---
title: 'Postupy: Použití matice barev k transformaci jedné barvy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 78fc498b0689026fb74ec0c422948c1879495560
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342853"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a><span data-ttu-id="9ab52-102">Postupy: Použití matice barev k transformaci jedné barvy</span><span class="sxs-lookup"><span data-stu-id="9ab52-102">How to: Use a Color Matrix to Transform a Single Color</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="9ab52-103">poskytuje <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> třídy pro ukládání a manipulaci s obrázky.</span><span class="sxs-lookup"><span data-stu-id="9ab52-103">provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <xref:System.Drawing.Image> <span data-ttu-id="9ab52-104">a <xref:System.Drawing.Bitmap> objekty ukládání barvu každého obrazového bodu jako 32bitová čísla: 8 bity pro červená, zelená, modrá a alfa.</span><span class="sxs-lookup"><span data-stu-id="9ab52-104">and <xref:System.Drawing.Bitmap> objects store the color of each pixel as a 32-bit number: 8 bits each for red, green, blue, and alpha.</span></span> <span data-ttu-id="9ab52-105">Každý ze čtyř komponent je číslo od 0 do 255, kde 0 představuje žádné intenzity a 255 představující plné intenzity.</span><span class="sxs-lookup"><span data-stu-id="9ab52-105">Each of the four components is a number from 0 through 255, with 0 representing no intensity and 255 representing full intensity.</span></span> <span data-ttu-id="9ab52-106">Hodnota alfa Určuje průhlednost barvy: 0 je zcela transparentní, a je úplně neprůhledná 255.</span><span class="sxs-lookup"><span data-stu-id="9ab52-106">The alpha component specifies the transparency of the color: 0 is fully transparent, and 255 is fully opaque.</span></span>  
  
 <span data-ttu-id="9ab52-107">Barva vektor je 4-n-tice formuláře (červená, zelená, modrá, alfa).</span><span class="sxs-lookup"><span data-stu-id="9ab52-107">A color vector is a 4-tuple of the form (red, green, blue, alpha).</span></span> <span data-ttu-id="9ab52-108">Například vektor barvy (0, 255, 0, 255) představuje neprůhledné barvu nemá žádné červená a modrá, ale má zelená při plné intenzity.</span><span class="sxs-lookup"><span data-stu-id="9ab52-108">For example, the color vector (0, 255, 0, 255) represents an opaque color that has no red or blue, but has green at full intensity.</span></span>  
  
 <span data-ttu-id="9ab52-109">Jiné konvence pro zastoupení barvy používá číslo 1 pro plné intenzity.</span><span class="sxs-lookup"><span data-stu-id="9ab52-109">Another convention for representing colors uses the number 1 for full intensity.</span></span> <span data-ttu-id="9ab52-110">Pomocí této konvenci, barva je popsáno v předchozím odstavci by být reprezentována vektor (0, 1, 0, 1).</span><span class="sxs-lookup"><span data-stu-id="9ab52-110">Using that convention, the color described in the preceding paragraph would be represented by the vector (0, 1, 0, 1).</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="9ab52-111">používá konvenci 1 jako plné intenzity při provádění transformace barev.</span><span class="sxs-lookup"><span data-stu-id="9ab52-111">uses the convention of 1 as full intensity when it performs color transformations.</span></span>  
  
 <span data-ttu-id="9ab52-112">Lineární transformace (otočení, škálování a podobně) můžete použít barvu vektory vynásobením vektory barva podle matice 4 x 4.</span><span class="sxs-lookup"><span data-stu-id="9ab52-112">You can apply linear transformations (rotation, scaling, and the like) to color vectors by multiplying the color vectors by a 4×4 matrix.</span></span> <span data-ttu-id="9ab52-113">Matice 4 x 4 však nelze používat pro překlad (nelineárních).</span><span class="sxs-lookup"><span data-stu-id="9ab52-113">However, you cannot use a 4×4 matrix to perform a translation (nonlinear).</span></span> <span data-ttu-id="9ab52-114">Pokud chcete přidat fiktivní páté souřadnice (například číslo 1) ke každému barva vektorů, můžete použít libovolnou kombinaci lineární transformace a překlady matice 5 × 5.</span><span class="sxs-lookup"><span data-stu-id="9ab52-114">If you add a dummy fifth coordinate (for example, the number 1) to each of the color vectors, you can use a 5×5 matrix to apply any combination of linear transformations and translations.</span></span> <span data-ttu-id="9ab52-115">Transformace skládající se z lineární transformace, za nímž následuje překlad se nazývá afinní transformace.</span><span class="sxs-lookup"><span data-stu-id="9ab52-115">A transformation consisting of a linear transformation followed by a translation is called an affine transformation.</span></span>  
  
 <span data-ttu-id="9ab52-116">Předpokládejme například, že chcete začít s barvou (0.2, 0.0, 0.4, 1.0) a platí následující transformace:</span><span class="sxs-lookup"><span data-stu-id="9ab52-116">For example, suppose you want to start with the color (0.2, 0.0, 0.4, 1.0) and apply the following transformations:</span></span>  
  
1. <span data-ttu-id="9ab52-117">Double hodnota červené</span><span class="sxs-lookup"><span data-stu-id="9ab52-117">Double the red component</span></span>  
  
2. <span data-ttu-id="9ab52-118">Přidání do komponenty červené, zelené a modré 0.2</span><span class="sxs-lookup"><span data-stu-id="9ab52-118">Add 0.2 to the red, green, and blue components</span></span>  
  
 <span data-ttu-id="9ab52-119">Následující násobení matic provede pár transformace v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="9ab52-119">The following matrix multiplication will perform the pair of transformations in the order listed.</span></span>  
  
 <span data-ttu-id="9ab52-120">![Přebarvení](./media/recoloring01.gif "recoloring01")</span><span class="sxs-lookup"><span data-stu-id="9ab52-120">![Recoloring](./media/recoloring01.gif "recoloring01")</span></span>  
  
 <span data-ttu-id="9ab52-121">Prvky matice barev jsou indexovány pomocí řádku a potom sloupce (počítáno od nuly).</span><span class="sxs-lookup"><span data-stu-id="9ab52-121">The elements of a color matrix are indexed (zero-based) by row and then column.</span></span> <span data-ttu-id="9ab52-122">Například, položku pátý řádek a třetí sloupec matice M udávají M [4] [2].</span><span class="sxs-lookup"><span data-stu-id="9ab52-122">For example, the entry in the fifth row and third column of matrix M is denoted by M[4][2].</span></span>  
  
 <span data-ttu-id="9ab52-123">5 × 5 jednotkovou matici (viz následující obrázek) má 1s na diagonální a 0s všude, kde jiný.</span><span class="sxs-lookup"><span data-stu-id="9ab52-123">The 5×5 identity matrix (shown in the following illustration) has 1s on the diagonal and 0s everywhere else.</span></span> <span data-ttu-id="9ab52-124">Pokud je barva vektor vynásobit jednotkovou matici, barva vektoru se nezmění.</span><span class="sxs-lookup"><span data-stu-id="9ab52-124">If you multiply a color vector by the identity matrix, the color vector does not change.</span></span> <span data-ttu-id="9ab52-125">Pohodlný způsob, jak tvoří matice barev transformace je začít s jednotkovou matici a proveďte malou změnu, která vytváří svou požadovanou transformaci.</span><span class="sxs-lookup"><span data-stu-id="9ab52-125">A convenient way to form the matrix of a color transformation is to start with the identity matrix and make a small change that produces the desired transformation.</span></span>  
  
 <span data-ttu-id="9ab52-126">![Přebarvení](./media/recoloring02.gif "recoloring02")</span><span class="sxs-lookup"><span data-stu-id="9ab52-126">![Recoloring](./media/recoloring02.gif "recoloring02")</span></span>  
  
 <span data-ttu-id="9ab52-127">Podrobnější diskuzi o matice a transformace, najdete v článku [systém souřadnic a transformace](coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="9ab52-127">For a more detailed discussion of matrices and transformations, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ab52-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ab52-128">Example</span></span>  
 <span data-ttu-id="9ab52-129">Následující příklad používá image, která je všechny jednu barvu (0.2, 0.0, 0.4, 1.0) a platí transformace je popsáno v předchozích odstavcích.</span><span class="sxs-lookup"><span data-stu-id="9ab52-129">The following example takes an image that is all one color (0.2, 0.0, 0.4, 1.0) and applies the transformation described in the preceding paragraphs.</span></span>  
  
 <span data-ttu-id="9ab52-130">Následující obrázek znázorňuje původní obrázek na levé straně a transformovaná image na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="9ab52-130">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="9ab52-131">![Colors](./media/colortrans1.png "colortrans1")</span><span class="sxs-lookup"><span data-stu-id="9ab52-131">![Colors](./media/colortrans1.png "colortrans1")</span></span>  
  
 <span data-ttu-id="9ab52-132">Kód v následujícím příkladu používá následující kroky provést přebarvení:</span><span class="sxs-lookup"><span data-stu-id="9ab52-132">The code in the following example uses the following steps to perform the recoloring:</span></span>  
  
1. <span data-ttu-id="9ab52-133">Inicializace <xref:System.Drawing.Imaging.ColorMatrix> objektu.</span><span class="sxs-lookup"><span data-stu-id="9ab52-133">Initialize a <xref:System.Drawing.Imaging.ColorMatrix> object.</span></span>  
  
2. <span data-ttu-id="9ab52-134">Vytvoření <xref:System.Drawing.Imaging.ImageAttributes> objektu a předejte <xref:System.Drawing.Imaging.ColorMatrix> objektu <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metodu <xref:System.Drawing.Imaging.ImageAttributes> objektu.</span><span class="sxs-lookup"><span data-stu-id="9ab52-134">Create an <xref:System.Drawing.Imaging.ImageAttributes> object and pass the <xref:System.Drawing.Imaging.ColorMatrix> object to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object.</span></span>  
  
3. <span data-ttu-id="9ab52-135">Předání <xref:System.Drawing.Imaging.ImageAttributes> objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="9ab52-135">Pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ab52-136">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9ab52-136">Compiling the Code</span></span>  
 <span data-ttu-id="9ab52-137">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="9ab52-137">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab52-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ab52-138">See also</span></span>

- [<span data-ttu-id="9ab52-139">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="9ab52-139">Recoloring Images</span></span>](recoloring-images.md)
- [<span data-ttu-id="9ab52-140">Systém souřadnic a transformace</span><span class="sxs-lookup"><span data-stu-id="9ab52-140">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
