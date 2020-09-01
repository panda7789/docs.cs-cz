---
description: Reference pro @-C#
title: Reference pro @-C#
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: 7d78b28479ed6128321207073dc94976710f10b6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138901"
---
# <a name="-c-reference"></a><span data-ttu-id="810b1-103">@ (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="810b1-103">@ (C# Reference)</span></span>

<span data-ttu-id="810b1-104">`@`Speciální znak slouží jako doslovné identifikátor.</span><span class="sxs-lookup"><span data-stu-id="810b1-104">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="810b1-105">Dá se použít následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="810b1-105">It can be used in the following ways:</span></span>

1. <span data-ttu-id="810b1-106">Aby bylo možné použít klíčová slova jazyka C# jako identifikátory.</span><span class="sxs-lookup"><span data-stu-id="810b1-106">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="810b1-107">`@`Znak prefixuje prvek kódu, který kompilátor interpretuje jako identifikátor spíše než klíčové slovo jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="810b1-107">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="810b1-108">Následující příklad používá `@` znak k definování identifikátoru s názvem `for` , který používá ve `for` smyčce.</span><span class="sxs-lookup"><span data-stu-id="810b1-108">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="810b1-109">Pro indikaci, že řetězcový literál má být interpretován jako doslovné.</span><span class="sxs-lookup"><span data-stu-id="810b1-109">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="810b1-110">`@`Znak v této instanci definuje *doslovné řetězcový literál*.</span><span class="sxs-lookup"><span data-stu-id="810b1-110">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="810b1-111">Jednoduché řídicí sekvence (například pro `"\\"` zpětné lomítko), šestnáctkové řídicí sekvence (například `"\x0041"` pro velké písmeno a) a řídicí sekvence Unicode (například `"\u0041"` pro velké písmeno a) jsou interpretovány doslova.</span><span class="sxs-lookup"><span data-stu-id="810b1-111">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="810b1-112">Pouze řídicí sekvence uvozovky ( `""` ) nejsou interpretovány doslova; vytvoří jeden znak dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="810b1-112">Only a quote escape sequence (`""`) is not interpreted literally; it produces one double quotation mark.</span></span> <span data-ttu-id="810b1-113">Kromě toho nejsou v případě doslovnéch znakových sekvencí (a) kulaté závorky [řetězcové](interpolated.md) závorky `{{` `}}` interpretovány doslova; vytvoří jednoduché znaky složené závorky.</span><span class="sxs-lookup"><span data-stu-id="810b1-113">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="810b1-114">Následující příklad definuje dvě totožné cesty k souboru, jeden pomocí regulárního řetězcového literálu a druhý pomocí doslovného řetězcového literálu.</span><span class="sxs-lookup"><span data-stu-id="810b1-114">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="810b1-115">Toto je jedno z častých použití doslovnéch řetězcových literálů.</span><span class="sxs-lookup"><span data-stu-id="810b1-115">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="810b1-116">Následující příklad znázorňuje účinek definování regulárního řetězcového literálu a doslovného řetězcového literálu, který obsahuje identické sekvence znaků.</span><span class="sxs-lookup"><span data-stu-id="810b1-116">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="810b1-117">Aby kompilátor mohl v případě konfliktu pojmenování rozlišovat mezi atributy.</span><span class="sxs-lookup"><span data-stu-id="810b1-117">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="810b1-118">Atribut je třída, která je odvozena z <xref:System.Attribute> .</span><span class="sxs-lookup"><span data-stu-id="810b1-118">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="810b1-119">Název jeho typu obvykle obsahuje **atribut**přípony, i když kompilátor vynutil tuto konvenci.</span><span class="sxs-lookup"><span data-stu-id="810b1-119">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="810b1-120">Atribut pak může být odkazován v kódu buď jeho úplným názvem typu (například `[InfoAttribute]` nebo jeho zkráceným názvem (například `[Info]` ).</span><span class="sxs-lookup"><span data-stu-id="810b1-120">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="810b1-121">Konflikt pojmenování nastane, pokud jsou dva zkrácené názvy typů atributů identické a jeden název typu zahrnuje příponu **atributu** , ale druhá ne.</span><span class="sxs-lookup"><span data-stu-id="810b1-121">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="810b1-122">Například následující kód se nepodaří zkompilovat, protože kompilátor nemůže určit, zda `Info` `InfoAttribute` je atribut nebo použit pro `Example` třídu.</span><span class="sxs-lookup"><span data-stu-id="810b1-122">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="810b1-123">Další informace najdete v tématu [CS1614](../compiler-messages/cs1614.md) .</span><span class="sxs-lookup"><span data-stu-id="810b1-123">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="810b1-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="810b1-124">See also</span></span>

- [<span data-ttu-id="810b1-125">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="810b1-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="810b1-126">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="810b1-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="810b1-127">Speciální znaky jazyka C#</span><span class="sxs-lookup"><span data-stu-id="810b1-127">C# Special Characters</span></span>](./index.md)
