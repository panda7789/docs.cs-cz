---
title: Zabezpečené a veřejné položky pole určené pouze pro čtení
description: Přečtěte si, proč byste se měli vyhnout použití veřejných polí pole jen pro čtení k definování chování hranic nebo zabezpečení vašich aplikací.
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 0a6a82c2c88fe61bd34c0accb831f018cf8702fc
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281430"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="c3ac3-103">Zabezpečené a veřejné položky pole určené pouze pro čtení</span><span class="sxs-lookup"><span data-stu-id="c3ac3-103">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="c3ac3-104">Nikdy nepoužívejte pole veřejné pole jen pro čtení ze spravovaných knihoven k definování chování hranic nebo zabezpečení vašich aplikací, protože pole veřejné pole jen pro čtení lze upravovat.</span><span class="sxs-lookup"><span data-stu-id="c3ac3-104">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3ac3-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3ac3-105">Remarks</span></span>  

<span data-ttu-id="c3ac3-106">Některé třídy .NET obsahují veřejná pole jen pro čtení, která obsahují parametry hranice specifické pro platformu.</span><span class="sxs-lookup"><span data-stu-id="c3ac3-106">Some .NET classes include read-only public fields that contain platform-specific boundary parameters.</span></span> <span data-ttu-id="c3ac3-107">Například <xref:System.IO.Path.InvalidPathChars> pole je pole, které popisuje znaky, které nejsou povoleny v řetězci cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="c3ac3-107">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span> <span data-ttu-id="c3ac3-108">Celá řada podobných polí je k dispozici v rámci .NET.</span><span class="sxs-lookup"><span data-stu-id="c3ac3-108">Many similar fields are present throughout .NET.</span></span>  
  
 <span data-ttu-id="c3ac3-109">Hodnoty veřejných polí jen pro čtení, jako je <xref:System.IO.Path.InvalidPathChars> lze upravit pomocí kódu nebo kódu, který sdílí doménu aplikace vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="c3ac3-109">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="c3ac3-110">Nepoužívejte pole veřejné pole jen pro čtení, jako je například, k definování chování hranic vašich aplikací.</span><span class="sxs-lookup"><span data-stu-id="c3ac3-110">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="c3ac3-111">Pokud tak učiníte, škodlivý kód může změnit definice hranic a použít váš kód neočekávaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="c3ac3-111">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="c3ac3-112">Ve verzi 2,0 a novějším .NET Framework byste měli použít metody, které vracejí nové pole namísto použití polí veřejné pole.</span><span class="sxs-lookup"><span data-stu-id="c3ac3-112">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="c3ac3-113">Například namísto použití <xref:System.IO.Path.InvalidPathChars> pole byste měli použít <xref:System.IO.Path.GetInvalidPathChars%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="c3ac3-113">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="c3ac3-114">Všimněte si, že typy .NET Framework nepoužívají veřejné pole k definování typů hranic interně.</span><span class="sxs-lookup"><span data-stu-id="c3ac3-114">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="c3ac3-115">Místo toho .NET Framework používá oddělená soukromá pole.</span><span class="sxs-lookup"><span data-stu-id="c3ac3-115">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="c3ac3-116">Změna hodnot těchto veřejných polí nezmění chování .NET Frameworkch typů.</span><span class="sxs-lookup"><span data-stu-id="c3ac3-116">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ac3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3ac3-117">See also</span></span>

- [<span data-ttu-id="c3ac3-118">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="c3ac3-118">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
