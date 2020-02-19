---
title: Zabezpečené a veřejné položky pole určené pouze pro čtení
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 2df4acc0606e4fe8fccee4a8acc6ab744dcbbb71
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452705"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="e3895-102">Zabezpečené a veřejné položky pole určené pouze pro čtení</span><span class="sxs-lookup"><span data-stu-id="e3895-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="e3895-103">Nikdy nepoužívejte pole veřejné pole jen pro čtení ze spravovaných knihoven k definování chování hranic nebo zabezpečení vašich aplikací, protože pole veřejné pole jen pro čtení lze upravovat.</span><span class="sxs-lookup"><span data-stu-id="e3895-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3895-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3895-104">Remarks</span></span>  

<span data-ttu-id="e3895-105">Některé třídy .NET obsahují veřejná pole jen pro čtení, která obsahují parametry hranice specifické pro platformu.</span><span class="sxs-lookup"><span data-stu-id="e3895-105">Some .NET classes include read-only public fields that contain platform-specific boundary parameters.</span></span> <span data-ttu-id="e3895-106">Například pole <xref:System.IO.Path.InvalidPathChars> je pole, které popisuje znaky, které nejsou povoleny v řetězci cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="e3895-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span> <span data-ttu-id="e3895-107">Celá řada podobných polí je k dispozici v rámci .NET.</span><span class="sxs-lookup"><span data-stu-id="e3895-107">Many similar fields are present throughout .NET.</span></span>  
  
 <span data-ttu-id="e3895-108">Hodnoty veřejných polí jen pro čtení, jako <xref:System.IO.Path.InvalidPathChars> lze upravit pomocí kódu nebo kódu, který sdílí doménu aplikace vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="e3895-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="e3895-109">Nepoužívejte pole veřejné pole jen pro čtení, jako je například, k definování chování hranic vašich aplikací.</span><span class="sxs-lookup"><span data-stu-id="e3895-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="e3895-110">Pokud tak učiníte, škodlivý kód může změnit definice hranic a použít váš kód neočekávaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="e3895-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="e3895-111">Ve verzi 2,0 a novějším .NET Framework byste měli použít metody, které vracejí nové pole namísto použití polí veřejné pole.</span><span class="sxs-lookup"><span data-stu-id="e3895-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="e3895-112">Například namísto použití pole <xref:System.IO.Path.InvalidPathChars> byste měli použít metodu <xref:System.IO.Path.GetInvalidPathChars%2A>.</span><span class="sxs-lookup"><span data-stu-id="e3895-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="e3895-113">Všimněte si, že typy .NET Framework nepoužívají veřejné pole k definování typů hranic interně.</span><span class="sxs-lookup"><span data-stu-id="e3895-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="e3895-114">Místo toho .NET Framework používá oddělená soukromá pole.</span><span class="sxs-lookup"><span data-stu-id="e3895-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="e3895-115">Změna hodnot těchto veřejných polí nezmění chování .NET Frameworkch typů.</span><span class="sxs-lookup"><span data-stu-id="e3895-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3895-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3895-116">See also</span></span>

- [<span data-ttu-id="e3895-117">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="e3895-117">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
