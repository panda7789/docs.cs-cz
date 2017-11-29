---
title: "Postupy: Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 375cab76063e4c77515d6b05b42f2d97ff3efc44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="227f1-102">Postupy: Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="227f1-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>
<span data-ttu-id="227f1-103">Následující příklad používá ukazatele kopírování bajtů z jednoho pole do jiné.</span><span class="sxs-lookup"><span data-stu-id="227f1-103">The following example uses pointers to copy bytes from one array to another.</span></span>  
  
 <span data-ttu-id="227f1-104">Tento příklad používá [unsafe](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo, které vám umožní použít ukazatele v `Copy` metoda.</span><span class="sxs-lookup"><span data-stu-id="227f1-104">This example uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="227f1-105">[Pevné](../../../csharp/language-reference/keywords/fixed-statement.md) příkaz se používá k deklaraci ukazatele na zdrojové a cílové pole.</span><span class="sxs-lookup"><span data-stu-id="227f1-105">The [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="227f1-106">To *PIN* umístění zdrojové a cílové maticových v paměti, aby nebude možné přesunout podle uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="227f1-106">This *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="227f1-107">Bloky paměti pro pole jsou Odepnout, kdy `fixed` blok dokončení.</span><span class="sxs-lookup"><span data-stu-id="227f1-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="227f1-108">Protože `Copy` metoda v tomto příkladu používá `unsafe` – klíčové slovo, se musí být zkompilovány s **/ unsafe** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="227f1-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the **/unsafe** compiler option.</span></span> <span data-ttu-id="227f1-109">Pokud chcete nastavit možnost v sadě Visual Studio, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="227f1-109">To set the option in Visual Studio, right-click the project name, and then click **Properties**.</span></span> <span data-ttu-id="227f1-110">Na **sestavení** vyberte **povolit nezabezpečený kód**.</span><span class="sxs-lookup"><span data-stu-id="227f1-110">On the **Build** tab, select **Allow unsafe code**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="227f1-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="227f1-111">Example</span></span>  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="227f1-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="227f1-112">See Also</span></span>  
 [<span data-ttu-id="227f1-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="227f1-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="227f1-114">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="227f1-114">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="227f1-115">/ unsafe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="227f1-115">/unsafe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)  
 [<span data-ttu-id="227f1-116">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="227f1-116">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
