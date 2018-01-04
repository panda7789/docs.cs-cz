---
title: "Postupy: Načtení dat ze schránky"
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
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c009efe743865896341da268bd14bf24158df46d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a><span data-ttu-id="fd8f6-102">Postupy: Načtení dat ze schránky</span><span class="sxs-lookup"><span data-stu-id="fd8f6-102">How to: Retrieve Data from the Clipboard</span></span>
<span data-ttu-id="fd8f6-103"><xref:System.Windows.Forms.Clipboard> Třída poskytuje metody, které můžete použít k interakci s funkcí schránky operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="fd8f6-104">Mnoho aplikací používá schránky jako dočasné úložiště pro data.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="fd8f6-105">Například textové editory používat schránku během operace vyjímání a vkládání.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="fd8f6-106">Schránky je také užitečné pro přenos informací z jedné aplikace do jiné.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-106">The Clipboard is also useful for transferring information from one application to another.</span></span>  
  
 <span data-ttu-id="fd8f6-107">Některé aplikace ukládat data do schránky a zvýšit počet dalších aplikací, které mohou potenciálně používat data ve více formátech.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-107">Some applications store data on the Clipboard in multiple formats to increase the number of other applications that can potentially use the data.</span></span> <span data-ttu-id="fd8f6-108">Formát schránky je řetězec, který identifikuje formátu.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-108">A Clipboard format is a string that identifies the format.</span></span> <span data-ttu-id="fd8f6-109">Aplikace, která používá identifikovaných formát můžete načíst přidružená data do schránky.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-109">An application that uses the identified format can retrieve the associated data on the Clipboard.</span></span> <span data-ttu-id="fd8f6-110"><xref:System.Windows.Forms.DataFormats> Třída poskytuje názvy ve formátu předdefinované pro vaše použití.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="fd8f6-111">Můžete také použít vlastní názvy ve formátu nebo použijte typ objektu jako formát.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-111">You can also use your own format names or use an object's type as its format.</span></span> <span data-ttu-id="fd8f6-112">Informace o přidání dat do schránky najdete v tématu [postupy: přidání dat do schránky](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).</span><span class="sxs-lookup"><span data-stu-id="fd8f6-112">For information about adding data to the Clipboard, see [How to: Add Data to the Clipboard](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).</span></span>  
  
 <span data-ttu-id="fd8f6-113">Pokud chcete zjistit, zda schránky obsahuje data v určitém formátu, použijte jednu z `Contains` *formátu* metody nebo <xref:System.Windows.Forms.Clipboard.GetData%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-113">To determine whether the Clipboard contains data in a particular format, use one of the `Contains`*Format* methods or the <xref:System.Windows.Forms.Clipboard.GetData%2A> method.</span></span> <span data-ttu-id="fd8f6-114">Pokud chcete načíst data ze schránky, použijte jednu z `Get` *formátu* metody nebo <xref:System.Windows.Forms.Clipboard.GetData%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-114">To retrieve data from the Clipboard, use one of the `Get`*Format* methods or the <xref:System.Windows.Forms.Clipboard.GetData%2A> method.</span></span> <span data-ttu-id="fd8f6-115">Tyto metody jsou v nové [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd8f6-115">These methods are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
 <span data-ttu-id="fd8f6-116">Pro přístup k datům ze schránky pomocí verze starší než [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], použijte <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> metoda a volání metody vrácený <xref:System.Windows.Forms.IDataObject>.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-116">To access data from the Clipboard by using versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], use the <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> method and call the methods of the returned <xref:System.Windows.Forms.IDataObject>.</span></span> <span data-ttu-id="fd8f6-117">Pokud chcete zjistit, jestli konkrétní formát je k dispozici v vráceného objektu, například volání <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-117">To determine whether a particular format is available in the returned object, for example, call the <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd8f6-118">Všechny aplikace systému Windows sdílet systému schránky.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-118">All Windows-based applications share the system Clipboard.</span></span> <span data-ttu-id="fd8f6-119">Proto obsah se mohou změnit, když přejdete na jinou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-119">Therefore, the contents are subject to change when you switch to another application.</span></span>  
>   
>  <span data-ttu-id="fd8f6-120"><xref:System.Windows.Forms.Clipboard> Třídu lze použít pouze v vláken nastavit na jedno vlákno apartment (STA) režimu.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-120">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="fd8f6-121">Chcete-li použít tuto třídu, ověřte, zda vaše `Main` metoda je označena <xref:System.STAThreadAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-121">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="fd8f6-122">K načtení dat ze schránky v jednom, běžné formátu</span><span class="sxs-lookup"><span data-stu-id="fd8f6-122">To retrieve data from the Clipboard in a single, common format</span></span>  
  
1.  <span data-ttu-id="fd8f6-123">Použití <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, nebo <xref:System.Windows.Forms.Clipboard.GetText%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-123">Use the <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, or <xref:System.Windows.Forms.Clipboard.GetText%2A> method.</span></span> <span data-ttu-id="fd8f6-124">Volitelně můžete pomocí odpovídající `Contains` *formát* metody nejprve k určení, zda jsou k dispozici v určitém formátu data.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-124">Optionally, use the corresponding `Contains`*Format* methods first to determine whether data is available in a particular format.</span></span> <span data-ttu-id="fd8f6-125">Tyto metody jsou k dispozici pouze v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd8f6-125">These methods are available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a><span data-ttu-id="fd8f6-126">K načtení dat ze schránky ve vlastním formátu</span><span class="sxs-lookup"><span data-stu-id="fd8f6-126">To retrieve data from the Clipboard in a custom format</span></span>  
  
1.  <span data-ttu-id="fd8f6-127">Použití <xref:System.Windows.Forms.Clipboard.GetData%2A> metodu s názvem vlastní formát.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-127">Use the <xref:System.Windows.Forms.Clipboard.GetData%2A> method with a custom format name.</span></span> <span data-ttu-id="fd8f6-128">Tato metoda je k dispozici pouze v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd8f6-128">This method is available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     <span data-ttu-id="fd8f6-129">Můžete také použít předdefinované formátu názvy s <xref:System.Windows.Forms.Clipboard.SetData%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-129">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="fd8f6-130">Další informace naleznete v tématu <xref:System.Windows.Forms.DataFormats>.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-130">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a><span data-ttu-id="fd8f6-131">K načtení dat ze schránky ve více formátech</span><span class="sxs-lookup"><span data-stu-id="fd8f6-131">To retrieve data from the Clipboard in multiple formats</span></span>  
  
1.  <span data-ttu-id="fd8f6-132">Použití <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fd8f6-132">Use the <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> method.</span></span> <span data-ttu-id="fd8f6-133">Tato metoda musí používat k načtení dat ze schránky na verze starší než [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd8f6-133">You must use this method to retrieve data from the Clipboard on versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="fd8f6-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd8f6-134">See Also</span></span>  
 [<span data-ttu-id="fd8f6-135">Operace přetažení a podpora schránky</span><span class="sxs-lookup"><span data-stu-id="fd8f6-135">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [<span data-ttu-id="fd8f6-136">Postupy: Přidání dat do schránky</span><span class="sxs-lookup"><span data-stu-id="fd8f6-136">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)
