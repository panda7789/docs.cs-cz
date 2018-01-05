---
title: "Postupy: Přidání dat do schránky"
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
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 452dfc5a9645e8f43ab583099deec60faa2d1b4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-data-to-the-clipboard"></a><span data-ttu-id="ac17d-102">Postupy: Přidání dat do schránky</span><span class="sxs-lookup"><span data-stu-id="ac17d-102">How to: Add Data to the Clipboard</span></span>
<span data-ttu-id="ac17d-103"><xref:System.Windows.Forms.Clipboard> Třída poskytuje metody, které můžete použít k interakci s funkcí schránky operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ac17d-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="ac17d-104">Mnoho aplikací používá schránky jako dočasné úložiště pro data.</span><span class="sxs-lookup"><span data-stu-id="ac17d-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="ac17d-105">Například textové editory používat schránku během operace vyjímání a vkládání.</span><span class="sxs-lookup"><span data-stu-id="ac17d-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="ac17d-106">Schránka je také užitečné pro přenos dat z jedné aplikace do jiné.</span><span class="sxs-lookup"><span data-stu-id="ac17d-106">The Clipboard is also useful for transferring data from one application to another.</span></span>  
  
 <span data-ttu-id="ac17d-107">Při přidání dat do schránky, můžete určit formát dat tak, aby ostatní aplikace poznáte data, pokud používají tohoto formátu.</span><span class="sxs-lookup"><span data-stu-id="ac17d-107">When you add data to the Clipboard, you can indicate the data format so that other applications can recognize the data if they can use that format.</span></span> <span data-ttu-id="ac17d-108">Můžete také přidat data do schránky v několika různých formátech zvyšte počet dalších aplikací, které mohou potenciálně používat data.</span><span class="sxs-lookup"><span data-stu-id="ac17d-108">You can also add data to the Clipboard in multiple different formats to increase the number of other applications that can potentially use the data.</span></span>  
  
 <span data-ttu-id="ac17d-109">Formát schránky je řetězec, který identifikuje formát tak, aby aplikace, která použije tento formát můžete načíst přidružená data.</span><span class="sxs-lookup"><span data-stu-id="ac17d-109">A Clipboard format is a string that identifies the format so that an application that uses that format can retrieve the associated data.</span></span> <span data-ttu-id="ac17d-110"><xref:System.Windows.Forms.DataFormats> Třída poskytuje názvy ve formátu předdefinované pro vaše použití.</span><span class="sxs-lookup"><span data-stu-id="ac17d-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="ac17d-111">Můžete také použít vlastní názvy ve formátu nebo použít typ objektu jako formát.</span><span class="sxs-lookup"><span data-stu-id="ac17d-111">You can also use your own format names or use the type of an object as its format.</span></span>  
  
 <span data-ttu-id="ac17d-112">Chcete-li přidat data do schránky. v jedné nebo více formátů, použijte <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ac17d-112">To add data to the Clipboard in one or multiple formats, use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method.</span></span> <span data-ttu-id="ac17d-113">Jakýkoli objekt můžete předat této metodě, ale chcete-li přidat data ve více formátech, je nejprve nutno přidat data na samostatný objekt navrženy pro práci s více formátů.</span><span class="sxs-lookup"><span data-stu-id="ac17d-113">You can pass any object to this method, but to add data in multiple formats, you must first add the data to a separate object designed to work with multiple formats.</span></span> <span data-ttu-id="ac17d-114">Obvykle budete přidávat data <xref:System.Windows.Forms.DataObject>, ale můžete použít libovolný typ, který implementuje <xref:System.Windows.Forms.IDataObject> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ac17d-114">Typically, you will add your data to a <xref:System.Windows.Forms.DataObject>, but you can use any type that implements the <xref:System.Windows.Forms.IDataObject> interface.</span></span>  
  
 <span data-ttu-id="ac17d-115">V [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], data přímo do schránky můžete přidat pomocí nové metody navržený tak, aby základní úlohy schránky jednodušší.</span><span class="sxs-lookup"><span data-stu-id="ac17d-115">In [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], you can add data directly to the Clipboard by using new methods designed to make basic Clipboard tasks easier.</span></span> <span data-ttu-id="ac17d-116">Pomocí těchto metod při práci s daty ve formátu jeden, běžné například textu.</span><span class="sxs-lookup"><span data-stu-id="ac17d-116">Use these methods when you work with data in a single, common format such as text.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac17d-117">Všechny aplikace systému Windows sdílet do schránky.</span><span class="sxs-lookup"><span data-stu-id="ac17d-117">All Windows-based applications share the Clipboard.</span></span> <span data-ttu-id="ac17d-118">Proto obsah se mohou změnit, když přejdete na jinou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ac17d-118">Therefore, the contents are subject to change when you switch to another application.</span></span>  
>   
>  <span data-ttu-id="ac17d-119"><xref:System.Windows.Forms.Clipboard> Třídu lze použít pouze v vláken nastavit na jedno vlákno apartment (STA) režimu.</span><span class="sxs-lookup"><span data-stu-id="ac17d-119">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="ac17d-120">Chcete-li použít tuto třídu, ověřte, zda vaše `Main` metoda je označena <xref:System.STAThreadAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="ac17d-120">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>  
>   
>  <span data-ttu-id="ac17d-121">Objekt musí být serializovatelný pro něj k uvedení do schránky.</span><span class="sxs-lookup"><span data-stu-id="ac17d-121">An object must be serializable for it to be put on the Clipboard.</span></span> <span data-ttu-id="ac17d-122">Chcete-li typu serializable, označte ji s <xref:System.SerializableAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="ac17d-122">To make a type serializable, mark it with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="ac17d-123">Pokud předáte objekt neserializovatelných metoda schránky, metoda selže bez způsobení výjimky.</span><span class="sxs-lookup"><span data-stu-id="ac17d-123">If you pass a non-serializable object to a Clipboard method, the method will fail without throwing an exception.</span></span> <span data-ttu-id="ac17d-124">Další informace o serializaci najdete v tématu <xref:System.Runtime.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="ac17d-124">For more information about serialization, see <xref:System.Runtime.Serialization>.</span></span>  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="ac17d-125">Chcete-li přidat data do schránky. v jedné, běžné formátu</span><span class="sxs-lookup"><span data-stu-id="ac17d-125">To add data to the Clipboard in a single, common format</span></span>  
  
1.  <span data-ttu-id="ac17d-126">Použití <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, nebo <xref:System.Windows.Forms.Clipboard.SetText%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ac17d-126">Use the <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, or <xref:System.Windows.Forms.Clipboard.SetText%2A> method.</span></span> <span data-ttu-id="ac17d-127">Tyto metody jsou k dispozici pouze v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac17d-127">These methods are available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a><span data-ttu-id="ac17d-128">Chcete-li přidat data do schránky ve vlastním formátu</span><span class="sxs-lookup"><span data-stu-id="ac17d-128">To add data to the Clipboard in a custom format</span></span>  
  
1.  <span data-ttu-id="ac17d-129">Použití <xref:System.Windows.Forms.Clipboard.SetData%2A> metodu s názvem vlastní formát.</span><span class="sxs-lookup"><span data-stu-id="ac17d-129">Use the <xref:System.Windows.Forms.Clipboard.SetData%2A> method with a custom format name.</span></span> <span data-ttu-id="ac17d-130">Tato metoda je k dispozici pouze v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac17d-130">This method is available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     <span data-ttu-id="ac17d-131">Můžete také použít předdefinované formátu názvy s <xref:System.Windows.Forms.Clipboard.SetData%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ac17d-131">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="ac17d-132">Další informace naleznete v tématu <xref:System.Windows.Forms.DataFormats>.</span><span class="sxs-lookup"><span data-stu-id="ac17d-132">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a><span data-ttu-id="ac17d-133">Chcete-li přidat data do schránky ve více formátech</span><span class="sxs-lookup"><span data-stu-id="ac17d-133">To add data to the Clipboard in multiple formats</span></span>  
  
1.  <span data-ttu-id="ac17d-134">Použití <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> metoda a předejte jí <xref:System.Windows.Forms.DataObject> která obsahuje vaše data.</span><span class="sxs-lookup"><span data-stu-id="ac17d-134">Use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method and pass in a <xref:System.Windows.Forms.DataObject> that contains your data.</span></span> <span data-ttu-id="ac17d-135">Tato metoda nutné použít k přidání dat do schránky ve verzích starších než [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac17d-135">You must use this method to add data to the Clipboard on versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="ac17d-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac17d-136">See Also</span></span>  
 [<span data-ttu-id="ac17d-137">Operace přetažení a podpora schránky</span><span class="sxs-lookup"><span data-stu-id="ac17d-137">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [<span data-ttu-id="ac17d-138">Postupy: Načtení dat ze schránky</span><span class="sxs-lookup"><span data-stu-id="ac17d-138">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)
