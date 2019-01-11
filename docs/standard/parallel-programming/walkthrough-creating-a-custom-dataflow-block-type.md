---
title: 'Průvodce: Vytvoření typu blok vlastní toku dat'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 380bcb6d2a2846d09267eeb3a0d637469ce9fba5
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221086"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>Průvodce: Vytvoření typu blok vlastní toku dat
Přestože Knihovna TPL datového toku poskytuje několik typů bloků toku dat, které dovolují vytvářet různé funkce, můžete také vytvořit typy vlastních bloků. Tento dokument popisuje, jak vytvořit typ bloku toku dat, která implementuje vlastní chování.  
  
## <a name="prerequisites"></a>Požadavky  
 Čtení [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) předtím, než čtete tento dokument.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Definování posuvné okno bloku toku dat  
 Vezměte v úvahu aplikace toku dat, která vyžaduje, aby vstupní hodnoty být ukládány do vyrovnávací paměti a potom výstup v podobě posuvné okno. Například pro vstupní hodnoty {0, 1, 2, 3, 4, 5} a velikosti okna tří bloku toku dat posuvné okno vytváří výstupní pole {0, 1, 2}, {1, 2, 3}, {2, 3, 4} a {3, 4, 5}. V následujících částech jsou dva způsoby, jak vytvořit typ bloku toku dat, který implementuje toto vlastní chování. První technika pracuje <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metoda kombinovat funkce <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektu a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> do jednoho propagátor objektu. Druhý postup definuje třídu, která je odvozena z <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> a kombinuje existující funkce k provedení vlastní chování.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Použití zapouzdření metoda k definování posuvné okno bloku toku dat  
 V následujícím příkladu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metodu pro vytvoření propagátor z cíl a zdroj. Propagátor umožňuje zdrojový a cílový blok tak, aby fungoval jako příjemce a odesílatele data.  
  
 Tato technika je užitečná, pokud vyžadujete funkce vlastního toku dat, ale nechcete, aby typ, který poskytuje další metody, vlastnosti nebo pole.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Odvozování z IPropagatorBlock k definování posuvné okno bloku toku dat  
 Následující příklad ukazuje `SlidingWindowBlock` třídy. Tato třída je odvozena z <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> tak, aby může fungovat jako zdroj a cíl dat. Stejně jako v předchozím příkladu `SlidingWindowBlock` třídy je založený na existující typy bloků toku dat. Ale `SlidingWindowBlock` třída implementuje také metody, které jsou vyžadované <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, a <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> rozhraní. Tyto metody všechny předat dál pracujeme, abychom členy typu blok toku dat předdefinované. Například `Post` metoda odloží práce `m_target` datový člen, který je také <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> objektu.  
  
 Tato technika je užitečná, když mají funkce vlastního toku dat a také vyžadují typ, který poskytuje další metody, vlastnosti nebo pole. Například `SlidingWindowBlock` třídy také se odvozuje od <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> tak, aby mohl poskytnout <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> a <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> metody. `SlidingWindowBlock` Rozšíření třídy ukazuje také tím, že poskytuje `WindowSize` vlastnost, která získá počet elementů v posuvné okno.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní kód v tomto návodu. Také ukazuje, jak použít obě posuvné okno bloky v metodě, která zapisuje do bloku, načte z něj a zobrazí výsledky do konzoly.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` v jazyce Visual Basic) a pak spuštěním následujícího příkazu na příkazovém řádku pro vývojáře pro Visual Studio okno.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 Visual Basic  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  

## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
