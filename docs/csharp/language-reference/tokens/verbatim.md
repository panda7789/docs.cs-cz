---
title: '@ (Referenční dokumentace jazyka C#)'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d6da87159e3ec9184eaa76ad069102204e2fcfc
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192209"
---
# <a name="-c-reference"></a><span data-ttu-id="ad10b-102">@ (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ad10b-102">@ (C# Reference)</span></span>

<span data-ttu-id="ad10b-103">`@` Speciální znak slouží jako doslovný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="ad10b-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="ad10b-104">Je možné následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="ad10b-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="ad10b-105">Povolit klíčová slova jazyka C# má být použit jako identifikátory.</span><span class="sxs-lookup"><span data-stu-id="ad10b-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="ad10b-106">`@` Znak předpon prvek kódu, který kompilátor, je interpretováno jako identifikátor místo klíčového slova jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="ad10b-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="ad10b-107">V následujícím příkladu `@` znak definovat identifikátor s názvem `for` používající v `for` smyčky.</span><span class="sxs-lookup"><span data-stu-id="ad10b-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="ad10b-108">Označuje, že řetězcového literálu verbatim interpretovat.</span><span class="sxs-lookup"><span data-stu-id="ad10b-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="ad10b-109">`@` Definuje znak v tomto případě *doslovný řetězec literálu*.</span><span class="sxs-lookup"><span data-stu-id="ad10b-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="ad10b-110">Jednoduchá řídící sekvence (například `"\\"` pro zpětné lomítko), hexadecimální řídicí sekvence (, jako `"\x0041"` pro velká A) a řídicí sekvence Unicode (například `"\u0041"` pro velká A) jsou interpretovány literálně.</span><span class="sxs-lookup"><span data-stu-id="ad10b-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="ad10b-111">Nabídky řídicí sekvence (`""`) nebyl interpretován doslovně; vytvoří jednoduchou uvozovku.</span><span class="sxs-lookup"><span data-stu-id="ad10b-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="ad10b-112">Kromě toho v případě verbatim [interpolovaný řetězec](interpolated.md) složenou závorku řídicí sekvence (`{{` a `}}`) nejsou interpretován doslovně; vytvářejí jednu složenou závorku znaků.</span><span class="sxs-lookup"><span data-stu-id="ad10b-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="ad10b-113">Následující příklad definuje dvě cesty k souborům identické, pomocí regulárních řetězcový literál a druhý s použitím doslovný řetězec literálu.</span><span class="sxs-lookup"><span data-stu-id="ad10b-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="ad10b-114">Toto je jeden z více běžná použití služby verbatim řetězcové literály.</span><span class="sxs-lookup"><span data-stu-id="ad10b-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="ad10b-115">Následující příklad ukazuje účinek definování regulárního řetězcový literál a doslovný řetězec literálu, které obsahují stejné znakové sekvence.</span><span class="sxs-lookup"><span data-stu-id="ad10b-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="ad10b-116">Umožňuje kompilátoru k rozlišení mezi atributy v případě konfliktu názvů.</span><span class="sxs-lookup"><span data-stu-id="ad10b-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="ad10b-117">Atribut je třída, která je odvozena z <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="ad10b-117">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="ad10b-118">Obvykle obsahuje příponu názvu typu **atribut**, i když kompilátor nevynucuje Tato konvence.</span><span class="sxs-lookup"><span data-stu-id="ad10b-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="ad10b-119">Atribut může poté odkazovat v kódu, buď pomocí jeho úplný název typu (například `[InfoAttribute]` nebo jeho zkrácený název (například `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="ad10b-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="ad10b-120">Ale ke konfliktu názvů v případě dvou zkrátila názvy typů atributů jsou identické, a zahrnuje jeden název typu **atribut** příponu, ale druhá ne.</span><span class="sxs-lookup"><span data-stu-id="ad10b-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="ad10b-121">Například následující kód nejde zkompilovat, protože kompilátor nemůže určit, jestli `Info` nebo `InfoAttribute` atribut aplikován `Example` třídy.</span><span class="sxs-lookup"><span data-stu-id="ad10b-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="ad10b-122">Zobrazit [CS1614](../compiler-messages/cs1614.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="ad10b-122">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="ad10b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad10b-123">See Also</span></span>

- [<span data-ttu-id="ad10b-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ad10b-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="ad10b-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ad10b-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ad10b-126">Speciální znaky v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ad10b-126">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)
