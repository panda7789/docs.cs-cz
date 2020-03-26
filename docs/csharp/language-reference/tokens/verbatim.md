---
title: '@ - C# Odkaz'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: b37f77273e767a5e5292e7707933892f57811d2a
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291764"
---
# <a name="-c-reference"></a><span data-ttu-id="2671b-102">@ (Odkaz na C#)</span><span class="sxs-lookup"><span data-stu-id="2671b-102">@ (C# Reference)</span></span>

<span data-ttu-id="2671b-103">Speciální `@` znak slouží jako doslovný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="2671b-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="2671b-104">Může být použit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="2671b-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="2671b-105">Chcete-li povolit c# klíčová slova, která mají být použita jako identifikátory.</span><span class="sxs-lookup"><span data-stu-id="2671b-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="2671b-106">Znak `@` předponuje element kódu, který kompilátor interpretuje jako identifikátor, nikoli klíčové slovo Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="2671b-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="2671b-107">Následující příklad používá `@` znak k definování `for` identifikátoru s `for` názvem, který používá ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="2671b-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="2671b-108">Chcete-li označit, že literál řetězce má být interpretován doslovně.</span><span class="sxs-lookup"><span data-stu-id="2671b-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="2671b-109">Znak `@` v této instanci definuje *doslovný řetězec literál*.</span><span class="sxs-lookup"><span data-stu-id="2671b-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="2671b-110">Jednoduché sekvence escape (například `"\\"` pro zpětné lomítko), šestnáctkové sekvence `"\x0041"` escape (například pro velké A) a `"\u0041"` sekvence escape Unicode (například pro velké A) jsou interpretovány doslova.</span><span class="sxs-lookup"><span data-stu-id="2671b-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="2671b-111">Pouze uvozovky`""`escape sekvence ( ) není interpretován doslovně; vytvoří jednu dvojitou uvozovku.</span><span class="sxs-lookup"><span data-stu-id="2671b-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces one double quotation mark.</span></span> <span data-ttu-id="2671b-112">Navíc v případě doslovné [interpolované řetězce](interpolated.md) složená závorka escape sekvence (`{{` a `}}`) nejsou interpretovány doslovně; vytvářejí znaky s jednou závorkou.</span><span class="sxs-lookup"><span data-stu-id="2671b-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="2671b-113">Následující příklad definuje dvě identické cesty k souborům, jednu pomocí literálu normálního řetězce a druhou pomocí doslovného literálu řetězce.</span><span class="sxs-lookup"><span data-stu-id="2671b-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="2671b-114">Toto je jeden z více běžných použití doslovných řetězcových literál.</span><span class="sxs-lookup"><span data-stu-id="2671b-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="2671b-115">Následující příklad ilustruje účinek definování normálního řetězcového literálu a doslovného literálu řetězce, které obsahují identické sekvence znaků.</span><span class="sxs-lookup"><span data-stu-id="2671b-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="2671b-116">Chcete-li povolit kompilátoru rozlišovat mezi atributy v případech konfliktu názvů.</span><span class="sxs-lookup"><span data-stu-id="2671b-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="2671b-117">Atribut je třída, která <xref:System.Attribute>je odvozena od .</span><span class="sxs-lookup"><span data-stu-id="2671b-117">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="2671b-118">Jeho název typu obvykle zahrnuje atribut přípony **,** i když kompilátor nevynucuje tuto konvenci.</span><span class="sxs-lookup"><span data-stu-id="2671b-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="2671b-119">Atribut pak může být odkazován v kódu buď jeho `[InfoAttribute]` úplný název typu (například nebo jeho zkrácený název `[Info]`(například).</span><span class="sxs-lookup"><span data-stu-id="2671b-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="2671b-120">Konflikt pojmenování však dochází, pokud dva zkrácené názvy typů atributů jsou identické a jeden název typu obsahuje příponu **Attribute,** ale druhý ne.</span><span class="sxs-lookup"><span data-stu-id="2671b-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="2671b-121">Například následující kód se nezdaří kompilovat, `Info` protože `InfoAttribute` kompilátor `Example` nelze určit, zda je atribut nebo použit a třída.</span><span class="sxs-lookup"><span data-stu-id="2671b-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="2671b-122">Další informace naleznete v [tématu CS1614.](../compiler-messages/cs1614.md)</span><span class="sxs-lookup"><span data-stu-id="2671b-122">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="2671b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="2671b-123">See also</span></span>

- [<span data-ttu-id="2671b-124">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2671b-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2671b-125">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2671b-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2671b-126">Speciální znaky v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2671b-126">C# Special Characters</span></span>](./index.md)
