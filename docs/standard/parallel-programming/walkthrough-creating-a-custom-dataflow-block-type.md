---
title: 'Postupy: Vytvoření bloku toku dat vlastního typu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
ms.openlocfilehash: cb953952bbed90edd2db799e92d44ec9f062babf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139878"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>Postupy: Vytvoření bloku toku dat vlastního typu
Přestože knihovna toku dat TPL poskytuje několik typů bloků toku dat, které umožňují různé funkce, můžete také vytvořit vlastní typy bloků. Tento dokument popisuje, jak vytvořit typ bloku toku dat, který implementuje vlastní chování.  
  
## <a name="prerequisites"></a>Požadavky  
 Před přečtením tohoto dokumentu si přečtěte [tok dat.](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Definování bloku datového toku posuvného okna  
 Zvažte aplikaci toku dat, která vyžaduje, aby vstupní hodnoty byly uloženy do vyrovnávací paměti a pak výstup v posuvné okno způsobem. Například pro vstupní hodnoty {0, 1, 2, 3, 4, 5} a velikost okna tři vytvoří blok datového toku posuvných oken výstupní pole {0, 1, 2}, {1, 2, 3}, {2, 3, 4} a {3, 4, 5}. Následující části popisují dva způsoby vytvoření typu bloku toku dat, který implementuje toto vlastní chování. První technika používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metodu ke kombinaci <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> funkce <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> objektu a objektu do jednoho bloku propagátoru. Druhá technika definuje třídu, která <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> je odvozena od a kombinuje existující funkce k provedení vlastního chování.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Použití metody zapouzdření k definování bloku datového toku posuvného okna  
 Následující příklad používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metodu k vytvoření bloku propagátoru z cíle a zdroje. Blok propagátoru umožňuje zdrojový blok a cílový blok fungovat jako příjemce a odesílatel dat.  
  
 Tato technika je užitečná, pokud požadujete vlastní funkce toku dat, ale nepotřebujete typ, který poskytuje další metody, vlastnosti nebo pole.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Odvození z IPropagatorBlock definovat posuvné okno datový tok bloku  
 Následující příklad ukazuje `SlidingWindowBlock` třídu. Tato třída je <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> odvozena z tak, aby mohla fungovat jako zdroj i cíl dat. Stejně jako v `SlidingWindowBlock` předchozím příkladu je třída postavena na existujících typech bloků toku dat. Třída `SlidingWindowBlock` však také implementuje metody, <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>které <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>jsou <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> požadovány , a rozhraní. Tyto metody všechny dopředí práci na předdefinované členy bloku toku dat. Metoda například `Post` odkládá práci `m_target` na datový člen, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> který je také objekt.  
  
 Tato technika je užitečná, když požadujete vlastní funkce toku dat a také potřebujete typ, který poskytuje další metody, vlastnosti nebo pole. Například `SlidingWindowBlock` třída také odvozuje tak, <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> aby <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> může poskytnout a metody. Třída `SlidingWindowBlock` také demonstruje rozšiřitelnost `WindowSize` poskytnutím vlastnosti, která načte počet prvků v posuvnéokno.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje úplný kód pro tento návod. Také ukazuje, jak použít oba posuvné okenní bloky v metodě, která zapisuje do bloku, čte z něj a vytiskne výsledky do konzoly.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="see-also"></a>Viz také

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
