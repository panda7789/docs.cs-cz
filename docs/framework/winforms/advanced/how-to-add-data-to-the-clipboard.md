---
title: 'Postupy: Přidání dat do schránky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: 0d9b82f01080d18353ecb91578a8005260bbe739
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044223"
---
# <a name="how-to-add-data-to-the-clipboard"></a><span data-ttu-id="65e88-102">Postupy: Přidání dat do schránky</span><span class="sxs-lookup"><span data-stu-id="65e88-102">How to: Add Data to the Clipboard</span></span>

<span data-ttu-id="65e88-103"><xref:System.Windows.Forms.Clipboard> Třída poskytuje metody, které můžete použít k interakci s funkcí schránky operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="65e88-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="65e88-104">Mnoho aplikací používá schránku jako dočasné úložiště pro data.</span><span class="sxs-lookup"><span data-stu-id="65e88-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="65e88-105">Například procesory aplikace Word používají schránku během operací vyjmutí a vložení.</span><span class="sxs-lookup"><span data-stu-id="65e88-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="65e88-106">Schránka je užitečná také pro přenos dat z jedné aplikace do jiné.</span><span class="sxs-lookup"><span data-stu-id="65e88-106">The Clipboard is also useful for transferring data from one application to another.</span></span>

<span data-ttu-id="65e88-107">Když do schránky přidáte data, můžete určit formát dat, aby ostatní aplikace mohli rozpoznat data v případě, že mohou použít tento formát.</span><span class="sxs-lookup"><span data-stu-id="65e88-107">When you add data to the Clipboard, you can indicate the data format so that other applications can recognize the data if they can use that format.</span></span> <span data-ttu-id="65e88-108">Můžete také přidat data do schránky v různých formátech a zvýšit tak počet dalších aplikací, které mohou data potenciálně používat.</span><span class="sxs-lookup"><span data-stu-id="65e88-108">You can also add data to the Clipboard in multiple different formats to increase the number of other applications that can potentially use the data.</span></span>

<span data-ttu-id="65e88-109">Formát schránky je řetězec, který určuje formát, aby aplikace, která používá tento formát, mohla načíst přidružená data.</span><span class="sxs-lookup"><span data-stu-id="65e88-109">A Clipboard format is a string that identifies the format so that an application that uses that format can retrieve the associated data.</span></span> <span data-ttu-id="65e88-110"><xref:System.Windows.Forms.DataFormats> Třída poskytuje předdefinované názvy formátů pro použití.</span><span class="sxs-lookup"><span data-stu-id="65e88-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="65e88-111">Můžete také použít vlastní názvy formátů nebo jako svůj formát použít typ objektu.</span><span class="sxs-lookup"><span data-stu-id="65e88-111">You can also use your own format names or use the type of an object as its format.</span></span>

<span data-ttu-id="65e88-112">Chcete-li přidat data do schránky v jednom nebo více formátech, použijte <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="65e88-112">To add data to the Clipboard in one or multiple formats, use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method.</span></span> <span data-ttu-id="65e88-113">Do této metody můžete předat libovolný objekt, ale chcete-li přidat data do více formátů, je nutné nejprve přidat data do samostatného objektu navrženého pro práci s více formáty.</span><span class="sxs-lookup"><span data-stu-id="65e88-113">You can pass any object to this method, but to add data in multiple formats, you must first add the data to a separate object designed to work with multiple formats.</span></span> <span data-ttu-id="65e88-114">Obvykle budete přidávat data do <xref:System.Windows.Forms.DataObject>, ale můžete použít jakýkoli typ, který <xref:System.Windows.Forms.IDataObject> implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="65e88-114">Typically, you will add your data to a <xref:System.Windows.Forms.DataObject>, but you can use any type that implements the <xref:System.Windows.Forms.IDataObject> interface.</span></span>

<span data-ttu-id="65e88-115">V .NET Framework 2,0 můžete přidat data přímo do schránky pomocí nových metod, které jsou navržené tak, aby byly snadno základní úlohy schránky.</span><span class="sxs-lookup"><span data-stu-id="65e88-115">In .NET Framework 2.0, you can add data directly to the Clipboard by using new methods designed to make basic Clipboard tasks easier.</span></span> <span data-ttu-id="65e88-116">Tyto metody použijte při práci s daty v jednom, běžném formátu, jako je text.</span><span class="sxs-lookup"><span data-stu-id="65e88-116">Use these methods when you work with data in a single, common format such as text.</span></span>

> [!NOTE]
> <span data-ttu-id="65e88-117">Všechny aplikace založené na systému Windows sdílejí schránku.</span><span class="sxs-lookup"><span data-stu-id="65e88-117">All Windows-based applications share the Clipboard.</span></span> <span data-ttu-id="65e88-118">Proto se obsah může změnit při přepnutí na jinou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="65e88-118">Therefore, the contents are subject to change when you switch to another application.</span></span>
>
> <span data-ttu-id="65e88-119">Třída <xref:System.Windows.Forms.Clipboard> se dá použít jenom v vláknech nastavených na režim sta (Single Thread Apartment).</span><span class="sxs-lookup"><span data-stu-id="65e88-119">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="65e88-120">Chcete-li použít tuto třídu, ujistěte `Main` se, že je vaše <xref:System.STAThreadAttribute> Metoda označena atributem.</span><span class="sxs-lookup"><span data-stu-id="65e88-120">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>
>
> <span data-ttu-id="65e88-121">Objekt musí být serializovatelný, aby jej bylo možné umístit do schránky.</span><span class="sxs-lookup"><span data-stu-id="65e88-121">An object must be serializable for it to be put on the Clipboard.</span></span> <span data-ttu-id="65e88-122">Chcete-li vytvořit serializovatelný typ, označte jej <xref:System.SerializableAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="65e88-122">To make a type serializable, mark it with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="65e88-123">Pokud předáte Neserializovatelný objekt metodě schránky, metoda selže bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="65e88-123">If you pass a non-serializable object to a Clipboard method, the method will fail without throwing an exception.</span></span> <span data-ttu-id="65e88-124">Další informace o serializaci naleznete v <xref:System.Runtime.Serialization>tématu.</span><span class="sxs-lookup"><span data-stu-id="65e88-124">For more information about serialization, see <xref:System.Runtime.Serialization>.</span></span>

### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="65e88-125">Přidání dat do schránky v jednom společném formátu</span><span class="sxs-lookup"><span data-stu-id="65e88-125">To add data to the Clipboard in a single, common format</span></span>

1. <span data-ttu-id="65e88-126">Použijte metodu <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A> ,,<xref:System.Windows.Forms.Clipboard.SetImage%2A>nebo .<xref:System.Windows.Forms.Clipboard.SetText%2A> <xref:System.Windows.Forms.Clipboard.SetAudio%2A></span><span class="sxs-lookup"><span data-stu-id="65e88-126">Use the <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, or <xref:System.Windows.Forms.Clipboard.SetText%2A> method.</span></span> <span data-ttu-id="65e88-127">Tyto metody jsou k dispozici pouze v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="65e88-127">These methods are available only in .NET Framework 2.0.</span></span>

    [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
    [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]

### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a><span data-ttu-id="65e88-128">Přidání dat do schránky ve vlastním formátu</span><span class="sxs-lookup"><span data-stu-id="65e88-128">To add data to the Clipboard in a custom format</span></span>

1. <span data-ttu-id="65e88-129"><xref:System.Windows.Forms.Clipboard.SetData%2A> Použijte metodu s názvem vlastního formátu.</span><span class="sxs-lookup"><span data-stu-id="65e88-129">Use the <xref:System.Windows.Forms.Clipboard.SetData%2A> method with a custom format name.</span></span> <span data-ttu-id="65e88-130">Tato metoda je k dispozici pouze v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="65e88-130">This method is available only in .NET Framework 2.0.</span></span>

    <span data-ttu-id="65e88-131">Můžete také použít předdefinované názvy formátů s <xref:System.Windows.Forms.Clipboard.SetData%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="65e88-131">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="65e88-132">Další informace naleznete v tématu <xref:System.Windows.Forms.DataFormats>.</span><span class="sxs-lookup"><span data-stu-id="65e88-132">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>

    [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
    [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a><span data-ttu-id="65e88-133">Přidání dat do schránky v několika formátech</span><span class="sxs-lookup"><span data-stu-id="65e88-133">To add data to the Clipboard in multiple formats</span></span>

1. <span data-ttu-id="65e88-134">Použijte metodu <xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType> a předejte <xref:System.Windows.Forms.DataObject> ji, která obsahuje vaše data.</span><span class="sxs-lookup"><span data-stu-id="65e88-134">Use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType> method and pass in a <xref:System.Windows.Forms.DataObject> that contains your data.</span></span> <span data-ttu-id="65e88-135">Tuto metodu je nutné použít, pokud chcete do schránky přidat data ve verzích starších než .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="65e88-135">You must use this method to add data to the Clipboard on versions earlier than .NET Framework 2.0.</span></span>

    [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
    [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

## <a name="see-also"></a><span data-ttu-id="65e88-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65e88-136">See also</span></span>

- [<span data-ttu-id="65e88-137">Operace přetažení a podpora schránky</span><span class="sxs-lookup"><span data-stu-id="65e88-137">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
- [<span data-ttu-id="65e88-138">Postupy: Načtení dat ze schránky</span><span class="sxs-lookup"><span data-stu-id="65e88-138">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
