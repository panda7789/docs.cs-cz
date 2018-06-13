---
title: MsgBox – ukázka
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3c4d38b60f349f0ecb87204cb980dd6681a8cc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388697"
---
# <a name="msgbox-sample"></a><span data-ttu-id="c7b6d-102">MsgBox – ukázka</span><span class="sxs-lookup"><span data-stu-id="c7b6d-102">MsgBox Sample</span></span>
<span data-ttu-id="c7b6d-103">Tento příklad znázorňuje, jakým způsobem lze předávat typy řetězců pomocí hodnoty jako parametry In a kdy lze použít pole <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> a <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>.</span><span class="sxs-lookup"><span data-stu-id="c7b6d-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="c7b6d-104">Příklad MsgBox používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="c7b6d-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="c7b6d-105">**MessageBox** exportovaný z User32.dll.</span><span class="sxs-lookup"><span data-stu-id="c7b6d-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="c7b6d-106">V tomto příkladu obsahuje třída `LibWrap` spravovaný prototyp pro každou nespravovanou funkci volanou třídou `MsgBoxSample`.</span><span class="sxs-lookup"><span data-stu-id="c7b6d-106">In this sample, the `LibWrap` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="c7b6d-107">Metody spravovaného prototypu `MsgBox`, `MsgBox2` a `MsgBox3` mají pro stejnou nespravovanou funkci odlišné deklarace.</span><span class="sxs-lookup"><span data-stu-id="c7b6d-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="c7b6d-108">Deklarace pro příklad `MsgBox2` vytváří v okně se zprávou nesprávný výstup, protože typ znaku, který je zadán jako ANSI, se neshoduje se vstupním bodem `MessageBoxW`, což je název funkce Unicode.</span><span class="sxs-lookup"><span data-stu-id="c7b6d-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="c7b6d-109">Deklarace pro `MsgBox3` vytvoří neshody mezi **EntryPoint**, **CharSet**, a **ExactSpelling** pole.</span><span class="sxs-lookup"><span data-stu-id="c7b6d-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="c7b6d-110">Při zavolání vyvolá pole `MsgBox3` výjimku.</span><span class="sxs-lookup"><span data-stu-id="c7b6d-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="c7b6d-111">Podrobné informace o řetězce pojmenovávání a název zařazování, najdete v části [zadání znaková sada](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="c7b6d-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="c7b6d-112">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="c7b6d-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="c7b6d-113">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="c7b6d-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c7b6d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7b6d-114">See Also</span></span>  
 [<span data-ttu-id="c7b6d-115">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="c7b6d-115">Marshaling Strings</span></span>](marshaling-strings.md)  
 <span data-ttu-id="c7b6d-116">[Datové typy vyvolání platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c7b6d-116">[Platform Invoke Data Types](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span></span>  
 [<span data-ttu-id="c7b6d-117">Výchozí zařazování pro řetězce</span><span class="sxs-lookup"><span data-stu-id="c7b6d-117">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)  
 [<span data-ttu-id="c7b6d-118">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="c7b6d-118">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="c7b6d-119">Určení znakové sady</span><span class="sxs-lookup"><span data-stu-id="c7b6d-119">Specifying a Character Set</span></span>](specifying-a-character-set.md)
