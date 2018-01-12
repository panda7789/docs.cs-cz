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
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>Postupy: Vytvoření bloku toku dat vlastního typu
Přestože knihovna toku dat TPL poskytuje několik typů bloku toku dat, které umožňují celou řadu funkcí, můžete také vytvořit vlastní bloku typy. Tento dokument popisuje, jak vytvořit typ bloku toku dat, který implementuje vlastní chování.  
  
## <a name="prerequisites"></a>Požadavky  
 Čtení [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) před čtením tohoto dokumentu.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Definování posuvné okno bloku toku dat  
 Vezměte v úvahu toku dat aplikace, která vyžaduje, aby vstupní hodnoty se uloží do vyrovnávací paměti a ve výstupu posuvné okno způsobem. Například pro vstupní hodnoty {0, 1, 2, 3, 4, 5} a velikosti okna tří posuvné okno bloku toku dat vytváří pole výstup {0, 1, 2}, {1, 2, 3}, {2, 3, 4} a {3, 4, 5}. Následující části popisují dva způsoby, jak vytvořit typ bloku toku dat, který implementuje toto vlastní chování. První způsob využívá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metoda kombinovat funkce <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektu a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> objektu do bloku jeden Šiřitel. Druhý způsob spočívá definuje třídu, která je odvozena z <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> a kombinuje stávající funkce provádět vlastní chování.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Pomocí zapouzdření metoda definovat posuvné okno bloku toku dat  
 Následující příklad používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metodu pro vytvoření blok Šiřitel z cíl a zdroj. Blok Šiřitel umožňuje blok zdrojový a cílový blok tak, aby fungoval jako příjemce a odesílatele data.  
  
 Tato metoda je užitečná, když potřebujete toku dat vlastního funkce, ale nechcete, aby typ, který poskytuje další metody, vlastnosti nebo pole.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Odvozování z IPropagatorBlock k definování posuvné okno bloku toku dat  
 Následující příklad ukazuje `SlidingWindowBlock` třídy. Tato třída odvozená z <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> tak, aby může fungovat jako zdroj a cíl data. Jako v předchozím příkladu `SlidingWindowBlock` třída je založený na existující typy bloku toku dat. Ale `SlidingWindowBlock` taky implementuje metody, které jsou vyžadované <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, a <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> rozhraní. Tyto metody všechny dál fungovat na členy typu bloku toku dat předdefinované. Například `Post` metoda odkládat údaje práce `m_target` datového člena, který je také <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> objektu.  
  
 Tato metoda je užitečná, když vyžadují toku dat vlastního funkce a také vyžaduje typ, který poskytuje další metody, vlastnosti nebo pole. Například `SlidingWindowBlock` třída také odvozena z <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> tak, aby můžete získat <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> a <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> metody. `SlidingWindowBlock` Třída také ukazuje rozšiřitelnost tím, že poskytuje `WindowSize` vlastnosti, která načte počet elementů v posuvné okno.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní kód v tomto návodu. Také ukazuje, jak používat obě posuvné okno bloky v metodu, která zapisuje do bloku, načte z něj a zobrazí výsledky do konzoly.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  

## <a name="see-also"></a>Viz také  
 [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
