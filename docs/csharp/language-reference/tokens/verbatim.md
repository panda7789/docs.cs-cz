---
title: "@ (Referenční dokumentace jazyka C#)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology: devlang-csharp
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
ms.openlocfilehash: 30f937951557ba65971a752b414cce6b485149be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-c-reference"></a><span data-ttu-id="f92e7-102">@ (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f92e7-102">@ (C# Reference)</span></span>

<span data-ttu-id="f92e7-103">`@` Speciální znak slouží jako typu verbatim identifikátor.</span><span class="sxs-lookup"><span data-stu-id="f92e7-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="f92e7-104">Dá se následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="f92e7-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="f92e7-105">Chcete-li povolit klíčová slova jazyka C# má být použit jako identifikátory.</span><span class="sxs-lookup"><span data-stu-id="f92e7-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="f92e7-106">`@` Znak předpony element kódu, který kompilátor je interpretovat jako identifikátor, nikoli klíčové slovo C#.</span><span class="sxs-lookup"><span data-stu-id="f92e7-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="f92e7-107">Následující příklad používá `@` znak zadat identifikátor s názvem `for` používající v `for` smyčky.</span><span class="sxs-lookup"><span data-stu-id="f92e7-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="f92e7-108">Označuje, že řetězcový literál doslovné interpretovat.</span><span class="sxs-lookup"><span data-stu-id="f92e7-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="f92e7-109">`@` Definuje znak v této instanci *typu verbatim řetězcový literál*.</span><span class="sxs-lookup"><span data-stu-id="f92e7-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="f92e7-110">Jednoduchý řídicí sekvence (například `"\\"` pro zpětné lomítko), šestnáctková řídicí sekvence (, jako `"\x0041"` A velká písmena, a Unicode řídicí sekvence, jako například `"\u0041"` pro velká písmena A, se interpretují oznámena.</span><span class="sxs-lookup"><span data-stu-id="f92e7-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A, and Unicode escape sequences, such as `"\u0041"` for an uppercase A, are interpreted literally.</span></span> <span data-ttu-id="f92e7-111">Uvozovky řídicí sekvence (`""`) neinterpretuje oznámena; vyvolá jednoduché uvozovky.</span><span class="sxs-lookup"><span data-stu-id="f92e7-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="f92e7-112">V následujícím příkladu definuje dvě cesty k souborům identické, jeden s použitím regulárních řetězcový literál a dalších pomocí typu verbatim řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="f92e7-112">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="f92e7-113">Toto je jedna z více běžná použití služby typu verbatim textové literály.</span><span class="sxs-lookup"><span data-stu-id="f92e7-113">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="f92e7-114">Následující příklad ilustruje účinek definování regulární řetězcový literál a typu verbatim řetězcový literál, které obsahují znak stejné pořadí.</span><span class="sxs-lookup"><span data-stu-id="f92e7-114">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="f92e7-115">Chcete-li povolit kompilátoru k rozlišení mezi atributy v případě konfliktu názvů.</span><span class="sxs-lookup"><span data-stu-id="f92e7-115">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="f92e7-116">Atribut je typ, který je odvozen od <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="f92e7-116">An attribute is a type that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="f92e7-117">Jeho název typu obvykle zahrnuje přípona **atribut**, i když kompilátor nevynucuje touto konvencí.</span><span class="sxs-lookup"><span data-stu-id="f92e7-117">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="f92e7-118">Atribut může pak odkazovat v kódu buď jeho typ úplný název (například `[InfoAttribute]` nebo jeho zkrácený název (například `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="f92e7-118">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="f92e7-119">Ale ke konfliktu názvů v případě dva zkrátit názvy typů atributů jsou identické, a obsahuje jeden název typu **atribut** příponu ale dalších neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f92e7-119">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="f92e7-120">Například následující kód nepodaří kompilovat, protože kompilátor nemůže určit, zda `Info` nebo `InfoAttribute` je použit atribut `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="f92e7-120">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Main` method.</span></span>

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

   <span data-ttu-id="f92e7-121">Pokud typu verbatim identifikátor slouží k identifikaci `Info` atribut v příkladu se zkompiluje úspěšně.</span><span class="sxs-lookup"><span data-stu-id="f92e7-121">If the verbatim identifier is used to identify the `Info` attribute, the example compiles successfully.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a><span data-ttu-id="f92e7-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f92e7-122">See Also</span></span>  
 [<span data-ttu-id="f92e7-123">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f92e7-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f92e7-124">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f92e7-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f92e7-125">Speciální znaky jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f92e7-125">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)
