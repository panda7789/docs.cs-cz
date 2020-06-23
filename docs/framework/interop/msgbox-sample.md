---
title: MsgBox – ukázka
description: Podívejte se na ukázku předávání typů řetězců podle hodnot jako v parametrech pomocí OknoSeZprávou. Ukazuje, kdy použít pole EntryPoint, CharSet a ExactSpelling v rozhraní .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
ms.openlocfilehash: ccf882e1f801dd18e5b65a4279fc580d927dd29d
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904088"
---
# <a name="msgbox-sample"></a><span data-ttu-id="9e453-104">MsgBox – ukázka</span><span class="sxs-lookup"><span data-stu-id="9e453-104">MsgBox Sample</span></span>
<span data-ttu-id="9e453-105">Tento příklad znázorňuje, jakým způsobem lze předávat typy řetězců pomocí hodnoty jako parametry In a kdy lze použít pole <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> a <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>.</span><span class="sxs-lookup"><span data-stu-id="9e453-105">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="9e453-106">Příklad MsgBox používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="9e453-106">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="9e453-107">Objekt **MessageBox** byl exportován z User32.dll.</span><span class="sxs-lookup"><span data-stu-id="9e453-107">**MessageBox** exported from User32.dll.</span></span>  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 <span data-ttu-id="9e453-108">V tomto příkladu obsahuje třída `NativeMethods` spravovaný prototyp pro každou nespravovanou funkci volanou třídou `MsgBoxSample`.</span><span class="sxs-lookup"><span data-stu-id="9e453-108">In this sample, the `NativeMethods` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="9e453-109">Metody spravovaného prototypu `MsgBox`, `MsgBox2` a `MsgBox3` mají pro stejnou nespravovanou funkci odlišné deklarace.</span><span class="sxs-lookup"><span data-stu-id="9e453-109">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="9e453-110">Deklarace pro příklad `MsgBox2` vytváří v okně se zprávou nesprávný výstup, protože typ znaku, který je zadán jako ANSI, se neshoduje se vstupním bodem `MessageBoxW`, což je název funkce Unicode.</span><span class="sxs-lookup"><span data-stu-id="9e453-110">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="9e453-111">Deklarace pro `MsgBox3` vytvoří neshodu mezi poli **EntryPoint**, **CharSet**a **ExactSpelling** .</span><span class="sxs-lookup"><span data-stu-id="9e453-111">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="9e453-112">Při zavolání vyvolá pole `MsgBox3` výjimku.</span><span class="sxs-lookup"><span data-stu-id="9e453-112">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="9e453-113">Podrobné informace o pojmenovávání řetězců a zařazování názvů najdete v tématu [Určení znakové sady](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="9e453-113">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="9e453-114">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="9e453-114">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="9e453-115">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="9e453-115">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="9e453-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e453-116">See also</span></span>

- [<span data-ttu-id="9e453-117">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="9e453-117">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="9e453-118">Výchozí zařazování pro řetězce</span><span class="sxs-lookup"><span data-stu-id="9e453-118">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="9e453-119">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="9e453-119">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="9e453-120">Určení sady znaků</span><span class="sxs-lookup"><span data-stu-id="9e453-120">Specifying a Character Set</span></span>](specifying-a-character-set.md)
