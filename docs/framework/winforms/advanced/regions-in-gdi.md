---
title: Oblasti v rozhraní GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
ms.openlocfilehash: 33d4f4ecca7b9d777fa4eab5b6d031de10f03ccc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076019"
---
# <a name="regions-in-gdi"></a><span data-ttu-id="732f4-102">Oblasti v rozhraní GDI+</span><span class="sxs-lookup"><span data-stu-id="732f4-102">Regions in GDI+</span></span>
<span data-ttu-id="732f4-103">Oblast je část oblasti zobrazení výstupního zařízení.</span><span class="sxs-lookup"><span data-stu-id="732f4-103">A region is a portion of the display area of an output device.</span></span> <span data-ttu-id="732f4-104">Oblasti mohou být jednoduché (jeden obdélník) nebo komplexní (kombinace mnohoúhelníků a uzavřené křivky).</span><span class="sxs-lookup"><span data-stu-id="732f4-104">Regions can be simple (a single rectangle) or complex (a combination of polygons and closed curves).</span></span> <span data-ttu-id="732f4-105">Následující obrázek znázorňuje dvě oblasti: jeden z obdélník, který je druhou vytvářejí na základě cesty.</span><span class="sxs-lookup"><span data-stu-id="732f4-105">The following illustration shows two regions: one constructed from a rectangle, and the other constructed from a path.</span></span>  
  
 <span data-ttu-id="732f4-106">![Regions](./media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span><span class="sxs-lookup"><span data-stu-id="732f4-106">![Regions](./media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span></span>  
  
## <a name="using-regions"></a><span data-ttu-id="732f4-107">Použití oblastí</span><span class="sxs-lookup"><span data-stu-id="732f4-107">Using Regions</span></span>  
 <span data-ttu-id="732f4-108">Oblasti se často používají pro oříznutí a testování průchodu.</span><span class="sxs-lookup"><span data-stu-id="732f4-108">Regions are often used for clipping and hit testing.</span></span> <span data-ttu-id="732f4-109">Výstřižek zahrnuje omezení kreslení v určité oblasti zobrazované oblasti, obvykle část, kterou je potřeba aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="732f4-109">Clipping involves restricting drawing to a certain region of the display area, usually the portion that needs to be updated.</span></span> <span data-ttu-id="732f4-110">Přístupů testování zahrnuje kontroly k určení, zda ukazatel je v určité oblasti obrazovky, když se stiskne tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="732f4-110">Hit testing involves checking to determine whether the cursor is in a certain region of the screen when a mouse button is pressed.</span></span>  
  
 <span data-ttu-id="732f4-111">Můžete vytvořit oblasti, obdélníku nebo cestu.</span><span class="sxs-lookup"><span data-stu-id="732f4-111">You can construct a region from a rectangle or a path.</span></span> <span data-ttu-id="732f4-112">Můžete také vytvořit komplexní oblasti kombinací stávajících oblastí.</span><span class="sxs-lookup"><span data-stu-id="732f4-112">You can also create complex regions by combining existing regions.</span></span> <span data-ttu-id="732f4-113"><xref:System.Drawing.Region> Třída poskytuje následující metody pro kombinování oblastí: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, a <xref:System.Drawing.Region.Complement%2A>.</span><span class="sxs-lookup"><span data-stu-id="732f4-113">The <xref:System.Drawing.Region> class provides the following methods for combining regions: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, and <xref:System.Drawing.Region.Complement%2A>.</span></span>  
  
 <span data-ttu-id="732f4-114">Průnik dvou oblastech je sada všech bodů, které patří do obou oblastech.</span><span class="sxs-lookup"><span data-stu-id="732f4-114">The intersection of two regions is the set of all points belonging to both regions.</span></span> <span data-ttu-id="732f4-115">Sjednocení je sada všech bodů, které patří do jedné nebo druhé nebo obou oblastech.</span><span class="sxs-lookup"><span data-stu-id="732f4-115">The union is the set of all points belonging to one or the other or both regions.</span></span> <span data-ttu-id="732f4-116">Doplněk oblast je sada všech bodů, které nejsou v oblasti.</span><span class="sxs-lookup"><span data-stu-id="732f4-116">The complement of a region is the set of all points that are not in the region.</span></span> <span data-ttu-id="732f4-117">Následující obrázek znázorňuje průniku a sjednocení dvou oblastech je znázorněno na předchozím obrázku.</span><span class="sxs-lookup"><span data-stu-id="732f4-117">The following illustration shows the intersection and union of the two regions shown in the preceding illustration.</span></span>  
  
 <span data-ttu-id="732f4-118">![Regions](./media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span><span class="sxs-lookup"><span data-stu-id="732f4-118">![Regions](./media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span></span>  
  
 <span data-ttu-id="732f4-119"><xref:System.Drawing.Region.Xor%2A> Metoda použitá pro dvojice oblasti, vytvoří oblast, která obsahuje všechny body, které patří do jedné oblasti nebo druhé, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="732f4-119">The <xref:System.Drawing.Region.Xor%2A> method, applied to a pair of regions, produces a region that contains all points that belong to one region or the other, but not both.</span></span> <span data-ttu-id="732f4-120"><xref:System.Drawing.Region.Exclude%2A> Metoda použitá pro dvojice oblasti, vytvoří oblast, která obsahuje všechny body v první oblasti, které nejsou v druhé oblasti.</span><span class="sxs-lookup"><span data-stu-id="732f4-120">The <xref:System.Drawing.Region.Exclude%2A> method, applied to a pair of regions, produces a region that contains all points in the first region that are not in the second region.</span></span> <span data-ttu-id="732f4-121">Následující obrázek znázorňuje oblastí, které jsou výsledkem použití <xref:System.Drawing.Region.Xor%2A> a <xref:System.Drawing.Region.Exclude%2A> metody do dvou oblastí, které jsou uvedené na začátku tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="732f4-121">The following illustration shows the regions that result from applying the <xref:System.Drawing.Region.Xor%2A> and <xref:System.Drawing.Region.Exclude%2A> methods to the two regions shown at the beginning of this topic.</span></span>  
  
 <span data-ttu-id="732f4-122">![Regions](./media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span><span class="sxs-lookup"><span data-stu-id="732f4-122">![Regions](./media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span></span>  
  
 <span data-ttu-id="732f4-123">K vyplnění oblasti, je nutné <xref:System.Drawing.Graphics> objektu, <xref:System.Drawing.Brush> objektu a <xref:System.Drawing.Region> objektu.</span><span class="sxs-lookup"><span data-stu-id="732f4-123">To fill a region, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Brush> object, and a <xref:System.Drawing.Region> object.</span></span> <span data-ttu-id="732f4-124"><xref:System.Drawing.Graphics> Objekt, který poskytuje <xref:System.Drawing.Graphics.FillRegion%2A> metody a <xref:System.Drawing.Brush> ukládá atributy výplň, například barvu nebo vzorek.</span><span class="sxs-lookup"><span data-stu-id="732f4-124">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.FillRegion%2A> method, and the <xref:System.Drawing.Brush> object stores attributes of the fill, such as color or pattern.</span></span> <span data-ttu-id="732f4-125">Následující příklad zkopíruje oblasti plnou barvou.</span><span class="sxs-lookup"><span data-stu-id="732f4-125">The following example fills a region with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#61](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="732f4-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="732f4-126">See also</span></span>

- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [<span data-ttu-id="732f4-127">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="732f4-127">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="732f4-128">Použití oblastí</span><span class="sxs-lookup"><span data-stu-id="732f4-128">Using Regions</span></span>](using-regions.md)
