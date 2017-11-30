---
title: "Postupy: Vytvoření soukromé kolekce písem"
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
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3016fb9a1b1d8466137bcaddb0b885c02c399baf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-private-font-collection"></a><span data-ttu-id="17810-102">Postupy: Vytvoření soukromé kolekce písem</span><span class="sxs-lookup"><span data-stu-id="17810-102">How to: Create a Private Font Collection</span></span>
<span data-ttu-id="17810-103"><xref:System.Drawing.Text.PrivateFontCollection> Třída dědí z <xref:System.Drawing.Text.FontCollection> abstraktní základní třída.</span><span class="sxs-lookup"><span data-stu-id="17810-103">The <xref:System.Drawing.Text.PrivateFontCollection> class inherits from the <xref:System.Drawing.Text.FontCollection> abstract base class.</span></span> <span data-ttu-id="17810-104">Můžete použít <xref:System.Drawing.Text.PrivateFontCollection> objekt udržovat sadu písem speciálně pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="17810-104">You can use a <xref:System.Drawing.Text.PrivateFontCollection> object to maintain a set of fonts specifically for your application.</span></span> <span data-ttu-id="17810-105">Kolekce privátní písem může zahrnovat nainstalovaný systém písma, jakož i písma, které nebyly nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="17810-105">A private font collection can include installed system fonts as well as fonts that have not been installed on the computer.</span></span> <span data-ttu-id="17810-106">Chcete-li přidat soubor písma na kolekci privátní písma, zavolejte <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> metodu <xref:System.Drawing.Text.PrivateFontCollection> objektu.</span><span class="sxs-lookup"><span data-stu-id="17810-106">To add a font file to a private font collection, call the <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> method of a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 <span data-ttu-id="17810-107"><xref:System.Drawing.Text.FontCollection.Families%2A> Vlastnost <xref:System.Drawing.Text.PrivateFontCollection> objekt obsahuje pole <xref:System.Drawing.FontFamily> objekty.</span><span class="sxs-lookup"><span data-stu-id="17810-107">The <xref:System.Drawing.Text.FontCollection.Families%2A> property of a <xref:System.Drawing.Text.PrivateFontCollection> object contains an array of <xref:System.Drawing.FontFamily> objects.</span></span>  
  
 <span data-ttu-id="17810-108">Počet rodiny písem v kolekci privátní písma není nutně stejný jako počet souborů písma, které jsou přidané do kolekce.</span><span class="sxs-lookup"><span data-stu-id="17810-108">The number of font families in a private font collection is not necessarily the same as the number of font files that have been added to the collection.</span></span> <span data-ttu-id="17810-109">Předpokládejme například, že se mají přidat soubory ArialBd.tff, Times.tff a TimesBd.tff do kolekce.</span><span class="sxs-lookup"><span data-stu-id="17810-109">For example, suppose you add the files ArialBd.tff, Times.tff, and TimesBd.tff to a collection.</span></span> <span data-ttu-id="17810-110">Bude tři soubory, ale pouze dvě řady v kolekci protože Times.tff a TimesBd.tff patří do stejné rodiny.</span><span class="sxs-lookup"><span data-stu-id="17810-110">There will be three files but only two families in the collection because Times.tff and TimesBd.tff belong to the same family.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17810-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="17810-111">Example</span></span>  
 <span data-ttu-id="17810-112">Následující příklad přidá následující soubory tři písma <xref:System.Drawing.Text.PrivateFontCollection> objektu:</span><span class="sxs-lookup"><span data-stu-id="17810-112">The following example adds the following three font files to a <xref:System.Drawing.Text.PrivateFontCollection> object:</span></span>  
  
-   <span data-ttu-id="17810-113">C:\\*systemroot*\Fonts\Arial.tff (Arial, regulární)</span><span class="sxs-lookup"><span data-stu-id="17810-113">C:\\*systemroot*\Fonts\Arial.tff (Arial, regular)</span></span>  
  
-   <span data-ttu-id="17810-114">C:\\*systemroot*\Fonts\CourBI.tff (Kurýrní nové, tučná kurzíva)</span><span class="sxs-lookup"><span data-stu-id="17810-114">C:\\*systemroot*\Fonts\CourBI.tff (Courier New, bold italic)</span></span>  
  
-   <span data-ttu-id="17810-115">C:\\*systemroot*\Fonts\TimesBd.tff (Times New Roman, tučně)</span><span class="sxs-lookup"><span data-stu-id="17810-115">C:\\*systemroot*\Fonts\TimesBd.tff (Times New Roman, bold)</span></span>  
  
 <span data-ttu-id="17810-116">Kód načte pole <xref:System.Drawing.FontFamily> objekty z <xref:System.Drawing.Text.FontCollection.Families%2A> vlastnost <xref:System.Drawing.Text.PrivateFontCollection> objektu.</span><span class="sxs-lookup"><span data-stu-id="17810-116">The code retrieves an array of <xref:System.Drawing.FontFamily> objects from the <xref:System.Drawing.Text.FontCollection.Families%2A> property of the <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 <span data-ttu-id="17810-117">Pro každou <xref:System.Drawing.FontFamily> objekt v kolekci, volání kódu <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> metodu pro určení, zda jsou k dispozici různé styly (obyčejný, tučné, kurzíva, tučná kurzíva, podtržení a přeškrtnutí).</span><span class="sxs-lookup"><span data-stu-id="17810-117">For each <xref:System.Drawing.FontFamily> object in the collection, the code calls the <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> method to determine whether various styles (regular, bold, italic, bold italic, underline, and strikeout) are available.</span></span> <span data-ttu-id="17810-118">Argumenty předaný <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> metoda jsou členy <xref:System.Drawing.FontStyle> výčtu.</span><span class="sxs-lookup"><span data-stu-id="17810-118">The arguments passed to the <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> method are members of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 <span data-ttu-id="17810-119">Pokud je k dispozici, kombinaci danou rodinu nebo styl <xref:System.Drawing.Font> objekt se vytvoří pomocí této rodiny a stylu.</span><span class="sxs-lookup"><span data-stu-id="17810-119">If a given family/style combination is available, a <xref:System.Drawing.Font> object is constructed using that family and style.</span></span> <span data-ttu-id="17810-120">První argument předaný <xref:System.Drawing.Font.%23ctor%2A> konstruktor je název rodiny písem (není <xref:System.Drawing.FontFamily> objektu stejně jako v případě pro jiné variace <xref:System.Drawing.Font.%23ctor%2A> konstruktor).</span><span class="sxs-lookup"><span data-stu-id="17810-120">The first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the font family name (not a <xref:System.Drawing.FontFamily> object as is the case for other variations of the <xref:System.Drawing.Font.%23ctor%2A> constructor).</span></span> <span data-ttu-id="17810-121">Po <xref:System.Drawing.Font> vytvoření objektu, je předána <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> třída zobrazíte název rodiny společně s název stylu.</span><span class="sxs-lookup"><span data-stu-id="17810-121">After the <xref:System.Drawing.Font> object is constructed, it is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class to display the family name along with the name of the style.</span></span>  
  
 <span data-ttu-id="17810-122">Výstup následující kód je podobná výstupní vidět na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="17810-122">The output of the following code is similar to the output shown in the following illustration.</span></span>  
  
 <span data-ttu-id="17810-123">![Text písem](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")</span><span class="sxs-lookup"><span data-stu-id="17810-123">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")</span></span>  
  
 <span data-ttu-id="17810-124">Arial.tff (která byla přidána do kolekce privátní písem v následujícím příkladu kódu) je v souboru Arial regulární styl písma.</span><span class="sxs-lookup"><span data-stu-id="17810-124">Arial.tff (which was added to the private font collection in the following code example) is the font file for the Arial regular style.</span></span> <span data-ttu-id="17810-125">Upozorňujeme však, že program výstup ukazuje několik dostupných stylů než regular pro typu Arial.</span><span class="sxs-lookup"><span data-stu-id="17810-125">Note, however, that the program output shows several available styles other than regular for the Arial font family.</span></span> <span data-ttu-id="17810-126">Je to způsobeno [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete simulovat tučné, kurzíva a Tučná kurzíva styly ze standardního stylu.</span><span class="sxs-lookup"><span data-stu-id="17810-126">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can simulate the bold, italic, and bold italic styles from the regular style.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="17810-127">Můžete také vytvořit podtržení a přeškrtnutí ze standardního stylu.</span><span class="sxs-lookup"><span data-stu-id="17810-127"> can also produce underlines and strikeouts from the regular style.</span></span>  
  
 <span data-ttu-id="17810-128">Podobně [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete simulovat styl tučné kurzíva z tučné styl nebo styl kurzíva.</span><span class="sxs-lookup"><span data-stu-id="17810-128">Similarly, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can simulate the bold italic style from either the bold style or the italic style.</span></span> <span data-ttu-id="17810-129">Výstup programu ukazuje, že styl tučné kurzíva je k dispozici pro rodinu časy, i když je jedinou TimesBd.tff (Times New Roman, tučné) časy soubor v kolekci.</span><span class="sxs-lookup"><span data-stu-id="17810-129">The program output shows that the bold italic style is available for the Times family even though TimesBd.tff (Times New Roman, bold) is the only Times file in the collection.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="17810-130">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="17810-130">Compiling the Code</span></span>  
 <span data-ttu-id="17810-131">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="17810-131">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17810-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="17810-132">See Also</span></span>  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 [<span data-ttu-id="17810-133">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="17810-133">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
