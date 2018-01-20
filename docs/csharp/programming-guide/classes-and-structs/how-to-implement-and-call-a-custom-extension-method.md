---
title: "Postupy: Implementace a volání vlastní metody rozšíření (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a277412c69d26f20721381d9cfa839c7f082f2f2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="02beb-102">Postupy: Implementace a volání vlastní metody rozšíření (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="02beb-102">How to: Implement and Call a Custom Extension Method (C# Programming Guide)</span></span>
<span data-ttu-id="02beb-103">Toto téma ukazuje, jak implementovat vlastní metody rozšíření pro jakýkoli typ rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="02beb-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="02beb-104">Kód klienta můžete použít rozšiřující metody přidat odkaz na knihovnu DLL, která je obsahuje, a přidáním [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktiva, která určuje obor názvů, ve kterém jsou definovány rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="02beb-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../../csharp/language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="02beb-105">K definování a volání metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="02beb-105">To define and call the extension method</span></span>  
  
1.  <span data-ttu-id="02beb-106">Definování statického [třída](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) tak, aby obsahovala metodě rozšíření.</span><span class="sxs-lookup"><span data-stu-id="02beb-106">Define a static [class](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="02beb-107">Třída musí být viditelná pro kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="02beb-107">The class must be visible to client code.</span></span> <span data-ttu-id="02beb-108">Další informace o usnadnění pravidla najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="02beb-108">For more information about accessibility rules, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
2.  <span data-ttu-id="02beb-109">Implementace metody rozšíření jako statickou metodu s alespoň viditelná stejně jako obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="02beb-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3.  <span data-ttu-id="02beb-110">První parametr metody Určuje typ, který zpracovává metodu; ho musí předcházet [to](../../../csharp/language-reference/keywords/this.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="02beb-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../../csharp/language-reference/keywords/this.md) modifier.</span></span>  
  
4.  <span data-ttu-id="02beb-111">Přidejte kód volání `using` – direktiva k určení [obor názvů](../../../csharp/language-reference/keywords/namespace.md) obsahující rozšíření metoda třída.</span><span class="sxs-lookup"><span data-stu-id="02beb-111">In the calling code, add a `using` directive to specify the [namespace](../../../csharp/language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5.  <span data-ttu-id="02beb-112">Volání metody, jako kdyby byly metody instance typu.</span><span class="sxs-lookup"><span data-stu-id="02beb-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="02beb-113">Upozorňujeme, že první parametr není zadán voláním kódu, protože představuje typ, na kterém se používá operátor a kompilátor již zná typ objektu.</span><span class="sxs-lookup"><span data-stu-id="02beb-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="02beb-114">Budete muset zadat argumenty pro parametry 2 prostřednictvím `n`.</span><span class="sxs-lookup"><span data-stu-id="02beb-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02beb-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="02beb-115">Example</span></span>  
 <span data-ttu-id="02beb-116">Následující příklad implementuje metody rozšíření s názvem `WordCount` v `CustomExtensions.StringExtension` třídy.</span><span class="sxs-lookup"><span data-stu-id="02beb-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="02beb-117">Metoda zpracovává <xref:System.String> třídy, která je zadána jako první parametr metody.</span><span class="sxs-lookup"><span data-stu-id="02beb-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="02beb-118">`CustomExtensions` Obor názvů je importovat do oboru názvů aplikací a metoda je volána v rámci `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="02beb-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02beb-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="02beb-119">Compiling the Code</span></span>  
 <span data-ttu-id="02beb-120">Pokud chcete spustit tento kód, zkopírujte a vložte ho do Visual C# projektu konzolové aplikace vytvořené v [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02beb-120">To run this code, copy and paste it into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="02beb-121">Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a obsahuje odkaz na System.Core.dll a `using` direktivy pro System.Linq.</span><span class="sxs-lookup"><span data-stu-id="02beb-121">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="02beb-122">Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="02beb-122">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="02beb-123">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="02beb-123">.NET Framework Security</span></span>  
 <span data-ttu-id="02beb-124">Rozšiřující metody k dispozici žádná konkrétní bezpečnostní ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="02beb-124">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="02beb-125">Se nikdy slouží k zosobnění existující metody podle typu, protože jsou vyřešeny všechny kolize názvů považuje instance nebo statickou metodu definované vlastní typ.</span><span class="sxs-lookup"><span data-stu-id="02beb-125">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="02beb-126">Rozšiřující metody nelze přístup k žádným privátní datům ve třídě rozšířené.</span><span class="sxs-lookup"><span data-stu-id="02beb-126">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02beb-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="02beb-127">See Also</span></span>  
 [<span data-ttu-id="02beb-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="02beb-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="02beb-129">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="02beb-129">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [<span data-ttu-id="02beb-130">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="02beb-130">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="02beb-131">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="02beb-131">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="02beb-132">protected</span><span class="sxs-lookup"><span data-stu-id="02beb-132">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="02beb-133">internal</span><span class="sxs-lookup"><span data-stu-id="02beb-133">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 [<span data-ttu-id="02beb-134">public</span><span class="sxs-lookup"><span data-stu-id="02beb-134">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="02beb-135">this</span><span class="sxs-lookup"><span data-stu-id="02beb-135">this</span></span>](../../../csharp/language-reference/keywords/this.md)  
 [<span data-ttu-id="02beb-136">namespace</span><span class="sxs-lookup"><span data-stu-id="02beb-136">namespace</span></span>](../../../csharp/language-reference/keywords/namespace.md)
