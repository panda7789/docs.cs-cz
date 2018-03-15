---
title: "@ (Referenční dokumentace jazyka C#)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b62231afc3014f9fc2b9ac7bd39168f40e12c8d
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="-c-reference"></a><span data-ttu-id="ef791-102">@ (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ef791-102">@ (C# Reference)</span></span>

<span data-ttu-id="ef791-103">`@` Speciální znak slouží jako typu verbatim identifikátor.</span><span class="sxs-lookup"><span data-stu-id="ef791-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="ef791-104">Dá se následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="ef791-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="ef791-105">Chcete-li povolit klíčová slova jazyka C# má být použit jako identifikátory.</span><span class="sxs-lookup"><span data-stu-id="ef791-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="ef791-106">`@` Znak předpony element kódu, který kompilátor je interpretovat jako identifikátor, nikoli klíčové slovo C#.</span><span class="sxs-lookup"><span data-stu-id="ef791-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="ef791-107">Následující příklad používá `@` znak zadat identifikátor s názvem `for` používající v `for` smyčky.</span><span class="sxs-lookup"><span data-stu-id="ef791-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="ef791-108">Označuje, že řetězcový literál doslovné interpretovat.</span><span class="sxs-lookup"><span data-stu-id="ef791-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="ef791-109">`@` Definuje znak v této instanci *typu verbatim řetězcový literál*.</span><span class="sxs-lookup"><span data-stu-id="ef791-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="ef791-110">Jednoduchý řídicí sekvence (například `"\\"` pro zpětné lomítko), šestnáctková řídicí sekvence (, jako `"\x0041"` A velká písmena, a Unicode řídicí sekvence, jako například `"\u0041"` pro velká písmena A, se interpretují oznámena.</span><span class="sxs-lookup"><span data-stu-id="ef791-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A, and Unicode escape sequences, such as `"\u0041"` for an uppercase A, are interpreted literally.</span></span> <span data-ttu-id="ef791-111">Uvozovky řídicí sekvence (`""`) neinterpretuje oznámena; vyvolá jednoduché uvozovky.</span><span class="sxs-lookup"><span data-stu-id="ef791-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="ef791-112">V následujícím příkladu definuje dvě cesty k souborům identické, jeden s použitím regulárních řetězcový literál a dalších pomocí typu verbatim řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="ef791-112">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="ef791-113">Toto je jedna z více běžná použití služby typu verbatim textové literály.</span><span class="sxs-lookup"><span data-stu-id="ef791-113">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="ef791-114">Následující příklad ilustruje účinek definování regulární řetězcový literál a typu verbatim řetězcový literál, které obsahují znak stejné pořadí.</span><span class="sxs-lookup"><span data-stu-id="ef791-114">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="ef791-115">Chcete-li povolit kompilátoru k rozlišení mezi atributy v případě konfliktu názvů.</span><span class="sxs-lookup"><span data-stu-id="ef791-115">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="ef791-116">Atribut je typ, který je odvozen od <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="ef791-116">An attribute is a type that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="ef791-117">Jeho název typu obvykle zahrnuje přípona **atribut**, i když kompilátor nevynucuje touto konvencí.</span><span class="sxs-lookup"><span data-stu-id="ef791-117">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="ef791-118">Atribut může pak odkazovat v kódu buď jeho typ úplný název (například `[InfoAttribute]` nebo jeho zkrácený název (například `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="ef791-118">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="ef791-119">Ale ke konfliktu názvů v případě dva zkrátit názvy typů atributů jsou identické, a obsahuje jeden název typu **atribut** příponu ale dalších neexistuje.</span><span class="sxs-lookup"><span data-stu-id="ef791-119">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="ef791-120">Například následující kód nepodaří kompilovat, protože kompilátor nemůže určit, zda `Info` nebo `InfoAttribute` je použit atribut `Example` – třída.</span><span class="sxs-lookup"><span data-stu-id="ef791-120">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span>

   ```csharp
   using System;

   [AttributeUsage(AttributeTargets.Class)]
   public class Info : Attribute
   {
      private string information;
      
      public Info(string info)
      {
          information = info;
      }
   }

   [AttributeUsage(AttributeTargets.Method)]
   public class InfoAttribute : Attribute
   {
      private string information;
      
      public InfoAttribute(string info)
      {
          information = info;
      }
   }

   [Info("A simple executable.")]
   public class Example
   {
      [InfoAttribute("The entry point.")]
      public static void Main()
      {
      }
   }
   ```  

   <span data-ttu-id="ef791-121">Pokud typu verbatim identifikátor slouží k identifikaci `Info` atribut v příkladu se zkompiluje úspěšně.</span><span class="sxs-lookup"><span data-stu-id="ef791-121">If the verbatim identifier is used to identify the `Info` attribute, the example compiles successfully.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a><span data-ttu-id="ef791-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef791-122">See Also</span></span>  
 [<span data-ttu-id="ef791-123">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ef791-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ef791-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ef791-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ef791-125">Speciální znaky v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ef791-125">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)
