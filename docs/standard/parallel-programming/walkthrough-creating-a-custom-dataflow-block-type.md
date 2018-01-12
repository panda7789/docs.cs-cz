---
title: "Postupy: Vytvoření bloku toku dat vlastního typu"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 54882ce5f646e9e790703e0951459a9fceac3bb6
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a><span data-ttu-id="2217f-102">Postupy: Vytvoření bloku toku dat vlastního typu</span><span class="sxs-lookup"><span data-stu-id="2217f-102">Walkthrough: Creating a Custom Dataflow Block Type</span></span>
<span data-ttu-id="2217f-103">Přestože knihovna toku dat TPL poskytuje několik typů bloku toku dat, které umožňují celou řadu funkcí, můžete také vytvořit vlastní bloku typy.</span><span class="sxs-lookup"><span data-stu-id="2217f-103">Although the TPL Dataflow Library provides several dataflow block types that enable a variety of functionality, you can also create custom block types.</span></span> <span data-ttu-id="2217f-104">Tento dokument popisuje, jak vytvořit typ bloku toku dat, který implementuje vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="2217f-104">This document describes how to create a dataflow block type that implements custom behavior.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2217f-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2217f-105">Prerequisites</span></span>  
 <span data-ttu-id="2217f-106">Čtení [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) před čtením tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2217f-106">Read [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) before you read this document.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a><span data-ttu-id="2217f-107">Definování posuvné okno bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="2217f-107">Defining the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="2217f-108">Vezměte v úvahu toku dat aplikace, která vyžaduje, aby vstupní hodnoty se uloží do vyrovnávací paměti a ve výstupu posuvné okno způsobem.</span><span class="sxs-lookup"><span data-stu-id="2217f-108">Consider a dataflow application that requires that input values be buffered and then output in a sliding window manner.</span></span> <span data-ttu-id="2217f-109">Například pro vstupní hodnoty {0, 1, 2, 3, 4, 5} a velikosti okna tří posuvné okno bloku toku dat vytváří pole výstup {0, 1, 2}, {1, 2, 3}, {2, 3, 4} a {3, 4, 5}.</span><span class="sxs-lookup"><span data-stu-id="2217f-109">For example, for the input values {0, 1, 2, 3, 4, 5} and a window size of three, a sliding window dataflow block produces the output arrays {0, 1, 2}, {1, 2, 3}, {2, 3, 4}, and {3, 4, 5}.</span></span> <span data-ttu-id="2217f-110">Následující části popisují dva způsoby, jak vytvořit typ bloku toku dat, který implementuje toto vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="2217f-110">The following sections describe two ways to create a dataflow block type that implements this custom behavior.</span></span> <span data-ttu-id="2217f-111">První způsob využívá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metoda kombinovat funkce <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektu a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> objektu do bloku jeden Šiřitel.</span><span class="sxs-lookup"><span data-stu-id="2217f-111">The first technique uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to combine the functionality of an <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object and an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object into one propagator block.</span></span> <span data-ttu-id="2217f-112">Druhý způsob spočívá definuje třídu, která je odvozena z <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> a kombinuje stávající funkce provádět vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="2217f-112">The second technique defines a class that derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> and combines existing functionality to perform custom behavior.</span></span>  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="2217f-113">Pomocí zapouzdření metoda definovat posuvné okno bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="2217f-113">Using the Encapsulate Method to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="2217f-114">Následující příklad používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metodu pro vytvoření blok Šiřitel z cíl a zdroj.</span><span class="sxs-lookup"><span data-stu-id="2217f-114">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to create a propagator block from a target and a source.</span></span> <span data-ttu-id="2217f-115">Blok Šiřitel umožňuje blok zdrojový a cílový blok tak, aby fungoval jako příjemce a odesílatele data.</span><span class="sxs-lookup"><span data-stu-id="2217f-115">A propagator block enables a source block and a target block to act as a receiver and sender of data.</span></span>  
  
 <span data-ttu-id="2217f-116">Tato metoda je užitečná, když potřebujete toku dat vlastního funkce, ale nechcete, aby typ, který poskytuje další metody, vlastnosti nebo pole.</span><span class="sxs-lookup"><span data-stu-id="2217f-116">This technique is useful when you require custom dataflow functionality, but you do not require a type that provides additional methods, properties, or fields.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="2217f-117">Odvozování z IPropagatorBlock k definování posuvné okno bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="2217f-117">Deriving from IPropagatorBlock to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="2217f-118">Následující příklad ukazuje `SlidingWindowBlock` třídy.</span><span class="sxs-lookup"><span data-stu-id="2217f-118">The following example shows the `SlidingWindowBlock` class.</span></span> <span data-ttu-id="2217f-119">Tato třída odvozená z <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> tak, aby může fungovat jako zdroj a cíl data.</span><span class="sxs-lookup"><span data-stu-id="2217f-119">This class derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> so that it can act as both a source and a target of data.</span></span> <span data-ttu-id="2217f-120">Jako v předchozím příkladu `SlidingWindowBlock` třída je založený na existující typy bloku toku dat.</span><span class="sxs-lookup"><span data-stu-id="2217f-120">As in the previous example, the `SlidingWindowBlock` class is built on existing dataflow block types.</span></span> <span data-ttu-id="2217f-121">Ale `SlidingWindowBlock` taky implementuje metody, které jsou vyžadované <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, a <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2217f-121">However, the `SlidingWindowBlock` class also implements the methods that are required by the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, and <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> interfaces.</span></span> <span data-ttu-id="2217f-122">Tyto metody všechny dál fungovat na členy typu bloku toku dat předdefinované.</span><span class="sxs-lookup"><span data-stu-id="2217f-122">These methods all forward work to the predefined dataflow block type members.</span></span> <span data-ttu-id="2217f-123">Například `Post` metoda odkládat údaje práce `m_target` datového člena, který je také <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="2217f-123">For example, the `Post` method defers work to the `m_target` data member, which is also an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object.</span></span>  
  
 <span data-ttu-id="2217f-124">Tato metoda je užitečná, když vyžadují toku dat vlastního funkce a také vyžaduje typ, který poskytuje další metody, vlastnosti nebo pole.</span><span class="sxs-lookup"><span data-stu-id="2217f-124">This technique is useful when you require custom dataflow functionality, and also require a type that provides additional methods, properties, or fields.</span></span> <span data-ttu-id="2217f-125">Například `SlidingWindowBlock` třída také odvozena z <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> tak, aby můžete získat <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> a <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2217f-125">For example, the `SlidingWindowBlock` class also derives from <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> so that it can provide the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> and <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> methods.</span></span> <span data-ttu-id="2217f-126">`SlidingWindowBlock` Třída také ukazuje rozšiřitelnost tím, že poskytuje `WindowSize` vlastnosti, která načte počet elementů v posuvné okno.</span><span class="sxs-lookup"><span data-stu-id="2217f-126">The `SlidingWindowBlock` class also demonstrates extensibility by providing the `WindowSize` property, which retrieves the number of elements in the sliding window.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a><span data-ttu-id="2217f-127">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="2217f-127">The Complete Example</span></span>  
 <span data-ttu-id="2217f-128">Následující příklad ukazuje kompletní kód v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="2217f-128">The following example shows the complete code for this walkthrough.</span></span> <span data-ttu-id="2217f-129">Také ukazuje, jak používat obě posuvné okno bloky v metodu, která zapisuje do bloku, načte z něj a zobrazí výsledky do konzoly.</span><span class="sxs-lookup"><span data-stu-id="2217f-129">It also demonstrates how to use the both sliding window blocks in a method that writes to the block, reads from it, and prints the results to the console.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2217f-130">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2217f-130">Compiling the Code</span></span>  
 <span data-ttu-id="2217f-131">Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.</span><span class="sxs-lookup"><span data-stu-id="2217f-131">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="2217f-132">**csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**</span><span class="sxs-lookup"><span data-stu-id="2217f-132">**csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="2217f-133">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**</span><span class="sxs-lookup"><span data-stu-id="2217f-133">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**</span></span>  

## <a name="see-also"></a><span data-ttu-id="2217f-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="2217f-134">See Also</span></span>  
 [<span data-ttu-id="2217f-135">Tok dat</span><span class="sxs-lookup"><span data-stu-id="2217f-135">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
