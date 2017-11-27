---
title: "Postupy: Testování rovnosti (identity) odkazů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2dbbd7c0e5ebb507ca3dda0f248d9f1c8f9595fe
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="04899-102">Postupy: Testování rovnosti (identity) odkazů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="04899-102">How to: Test for Reference Equality (Identity) (C# Programming Guide)</span></span>
<span data-ttu-id="04899-103">Pro podporu porovnání rovnosti referencí u typů není nutné implementovat žádnou vlastní logiku.</span><span class="sxs-lookup"><span data-stu-id="04899-103">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="04899-104">Tato funkce je poskytována pro všechny typy statickou metodou <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04899-104">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="04899-105">Následující příklad ukazuje, jak zjistit, jestli mají dvě proměnné *referenční rovnosti*, což znamená, že se vztahují ke stejnému objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="04899-105">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="04899-106">Příklad také ukazuje, proč <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> vždy vrátí pro typy hodnot hodnotu `false` a proč by nemělo být pro určení rovnosti řetězce použito <xref:System.Object.ReferenceEquals%2A>.</span><span class="sxs-lookup"><span data-stu-id="04899-106">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04899-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="04899-107">Example</span></span>  
 [!code-csharp[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 <span data-ttu-id="04899-108">Implementace `Equals` v univerzální základní třídě <xref:System.Object?displayProperty=nameWithType> také provádí kontrolu rovnosti reference, ale nejlepší možností je ji nepoužívat, protože pokud třída přepíše metodu, mohly by být výsledky neočekávané.</span><span class="sxs-lookup"><span data-stu-id="04899-108">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="04899-109">Totéž platí pro operátory `==` a `!=`.</span><span class="sxs-lookup"><span data-stu-id="04899-109">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="04899-110">Jsou-li nasazeny na typy referencí, provádí operátory == a `!=` ve výchozím chování kontrolu rovnosti reference.</span><span class="sxs-lookup"><span data-stu-id="04899-110">When they are operating on reference types, the default behavior of == and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="04899-111">Odvozené třídy však mohou operátor přetížit pro provedení kontroly rovnosti hodnoty.</span><span class="sxs-lookup"><span data-stu-id="04899-111">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="04899-112">Pokud je třeba zjistit, zda mají dva objekty stejnou rovnost reference, je pro snížení potenciálu výskytu chyby nejlepší použít <xref:System.Object.ReferenceEquals%2A>.</span><span class="sxs-lookup"><span data-stu-id="04899-112">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="04899-113">Konstantní řetězce v rámci stejného sestavení jsou vždy internovány modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="04899-113">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="04899-114">To znamená, že je zachována pouze jedna instance každého jedinečného textového literálu.</span><span class="sxs-lookup"><span data-stu-id="04899-114">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="04899-115">Modul runtime však nezaručuje, že jsou řetězce, které jsou vytvořeny v době běhu, internovány, a ani nezaručuje, že jsou internovány dva totožné konstantní řetězce v různých sestaveních.</span><span class="sxs-lookup"><span data-stu-id="04899-115">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04899-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="04899-116">See Also</span></span>  
 [<span data-ttu-id="04899-117">Porovnání rovnosti</span><span class="sxs-lookup"><span data-stu-id="04899-117">Equality Comparisons</span></span>](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
