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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139878"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>Postupy: Vytvoření bloku toku dat vlastního typu
I když knihovna rozhraní TPL Dataflow nabízí několik typů bloků toku dat, které umožňují nejrůznější funkce, můžete také vytvořit vlastní typy bloků. Tento dokument popisuje, jak vytvořit typ bloku toku dat, který implementuje vlastní chování.  
  
## <a name="prerequisites"></a>Požadavky  
 Před čtením tohoto dokumentu si přečtěte [tok](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dat.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Definování posunutého bloku toku dat okna  
 Vezměte v úvahu aplikaci toku dat, která vyžaduje, aby vstupní hodnoty byly uloženy do vyrovnávací paměti a následně výstupem v posuvných oknech. Například pro vstupní hodnoty {0, 1, 2, 3, 4, 5} a velikost okna tři se posuňte blok toku dat posunutého okna vytvoří výstupní pole {0, 1, 2}, {1, 2, 3}, {2, 3, 4} a {3, 4, 5}. Následující části popisují dva způsoby, jak vytvořit typ bloku toku dat, který implementuje toto vlastní chování. První technika používá metodu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> pro kombinování funkcí objektu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> a objektu <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> do jednoho bloku šiřitelu. Druhá technika definuje třídu, která je odvozena z <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> a kombinuje stávající funkce pro provádění vlastního chování.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Použití metody zapouzdření k definování posunutého bloku toku dat okna  
 Následující příklad používá metodu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> pro vytvoření bloku šiřitelu z cíle a zdroje. Blok šíření umožňuje, aby zdrojový blok a cílový blok fungovaly jako přijímač a odesílatel dat.  
  
 Tato technika je užitečná, pokud požadujete vlastní funkci toku dat, ale nevyžadujete typ, který poskytuje další metody, vlastnosti nebo pole.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Odvození z IPropagatorBlock k definování posunutého bloku toku dat posuvných oken  
 Následující příklad ukazuje třídu `SlidingWindowBlock`. Tato třída je odvozena z <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> tak, aby mohla sloužit jako zdroj i jako cíl dat. Jak je uvedeno v předchozím příkladu, třída `SlidingWindowBlock` je postavená na stávajících typech bloků toku dat. Nicméně třída `SlidingWindowBlock` také implementuje metody, které jsou vyžadovány rozhraním <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>a <xref:System.Threading.Tasks.Dataflow.IDataflowBlock>. Tyto metody předají veškerou práci na předdefinované členy typu bloku toku dat. Například metoda `Post` odloží práci na datový člen `m_target`, což je také objekt <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.  
  
 Tato technika je užitečná v případě, že požadujete vlastní funkci toku dat a také vyžaduje typ, který poskytuje další metody, vlastnosti nebo pole. Například třída `SlidingWindowBlock` také odvozuje z <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601>, aby mohla poskytovat metody <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> a <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A>. Třída `SlidingWindowBlock` také ukazuje rozšiřitelnost tím, že poskytuje vlastnost `WindowSize`, která načítá počet prvků v posuvných oknech.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní kód pro tento návod. Ukazuje také, jak použít posuvné bloky oken v metodě, která zapisuje do bloku, čte z něj a vytiskne výsledky do konzoly.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
