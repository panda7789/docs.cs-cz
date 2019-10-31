---
title: Odkaz na C# @
ms.custom: seodec18
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: 6f9f16b2639cd9ea57ee7a3030deabf4c1decfbb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101563"
---
# <a name="-c-reference"></a><span data-ttu-id="dfa29-102">@ (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="dfa29-102">@ (C# Reference)</span></span>

<span data-ttu-id="dfa29-103">`@` speciální znak slouží jako doslovné identifikátor.</span><span class="sxs-lookup"><span data-stu-id="dfa29-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="dfa29-104">Dá se použít následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="dfa29-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="dfa29-105">Aby se C# klíčová slova mohla používat jako identifikátory.</span><span class="sxs-lookup"><span data-stu-id="dfa29-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="dfa29-106">`@` znak předponu prvku kódu, který kompilátor interpretuje jako identifikátor spíše než C# klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="dfa29-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="dfa29-107">Následující příklad používá `@` znak k definování identifikátoru s názvem `for`, který používá ve `for` smyčce.</span><span class="sxs-lookup"><span data-stu-id="dfa29-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="dfa29-108">Pro indikaci, že řetězcový literál má být interpretován jako doslovné.</span><span class="sxs-lookup"><span data-stu-id="dfa29-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="dfa29-109">Znak `@` v této instanci definuje *doslovné řetězcový literál*.</span><span class="sxs-lookup"><span data-stu-id="dfa29-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="dfa29-110">Jednoduché řídicí sekvence (například `"\\"` pro zpětné lomítko), šestnáctkové řídicí sekvence (například `"\x0041"` pro velké písmeno A) a řídicí sekvence Unicode (například `"\u0041"` pro velké písmeno A) jsou interpretovány doslova.</span><span class="sxs-lookup"><span data-stu-id="dfa29-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="dfa29-111">Pouze sekvence escape v uvozovkách (`""`) nejsou interpretovány doslova; Vytvoří jednoduchou uvozovku.</span><span class="sxs-lookup"><span data-stu-id="dfa29-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="dfa29-112">Kromě toho nejsou v případě doslovného počtu znakových sekvencí [řetězcové](interpolated.md) závorky (`{{` a `}}`) interpretovány doslova; poskytují jednoduché znaky složených závorek.</span><span class="sxs-lookup"><span data-stu-id="dfa29-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="dfa29-113">Následující příklad definuje dvě totožné cesty k souboru, jeden pomocí regulárního řetězcového literálu a druhý pomocí doslovného řetězcového literálu.</span><span class="sxs-lookup"><span data-stu-id="dfa29-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="dfa29-114">Toto je jedno z častých použití doslovnéch řetězcových literálů.</span><span class="sxs-lookup"><span data-stu-id="dfa29-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="dfa29-115">Následující příklad znázorňuje účinek definování regulárního řetězcového literálu a doslovného řetězcového literálu, který obsahuje identické sekvence znaků.</span><span class="sxs-lookup"><span data-stu-id="dfa29-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="dfa29-116">Aby kompilátor mohl v případě konfliktu pojmenování rozlišovat mezi atributy.</span><span class="sxs-lookup"><span data-stu-id="dfa29-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="dfa29-117">Atribut je třída, která je odvozena z <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="dfa29-117">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="dfa29-118">Název jeho typu obvykle obsahuje **atribut**přípony, i když kompilátor vynutil tuto konvenci.</span><span class="sxs-lookup"><span data-stu-id="dfa29-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="dfa29-119">Atribut pak může být odkazován v kódu buď jeho úplným názvem typu (například `[InfoAttribute]` nebo jeho zkráceným názvem (například `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="dfa29-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="dfa29-120">Konflikt pojmenování nastane, pokud jsou dva zkrácené názvy typů atributů identické a jeden název typu zahrnuje příponu **atributu** , ale druhá ne.</span><span class="sxs-lookup"><span data-stu-id="dfa29-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="dfa29-121">Například následující kód se nepodaří zkompilovat, protože kompilátor nemůže určit, zda je atribut `Info` nebo `InfoAttribute` použit pro třídu `Example`.</span><span class="sxs-lookup"><span data-stu-id="dfa29-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="dfa29-122">Další informace najdete v tématu [CS1614](../compiler-messages/cs1614.md) .</span><span class="sxs-lookup"><span data-stu-id="dfa29-122">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="dfa29-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfa29-123">See also</span></span>

- [<span data-ttu-id="dfa29-124">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="dfa29-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dfa29-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dfa29-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dfa29-126">Speciální znaky v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dfa29-126">C# Special Characters</span></span>](./index.md)
