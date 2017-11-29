---
title: "Zabezpečené a veřejné položky pole určené pouze pro čtení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ae2e9a7dd9e08344c254b52c7139c6d1dd2776a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="b671b-102">Zabezpečené a veřejné položky pole určené pouze pro čtení</span><span class="sxs-lookup"><span data-stu-id="b671b-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="b671b-103">Nikdy nepoužívejte jen pro čtení veřejné položky pole ze spravovaných knihoven k definování chování hranice nebo zabezpečení aplikací, protože lze upravit jen pro čtení veřejné položky pole.</span><span class="sxs-lookup"><span data-stu-id="b671b-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b671b-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b671b-104">Remarks</span></span>  
 <span data-ttu-id="b671b-105">Některé třídy rozhraní .NET framework obsahovat jen pro čtení veřejná pole obsahující parametry specifické pro platformu hranic.</span><span class="sxs-lookup"><span data-stu-id="b671b-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="b671b-106">Například <xref:System.IO.Path.InvalidPathChars> je pole, která popisuje znaky, které nejsou povoleny v řetězci cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="b671b-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="b671b-107">Mnoho podobné polí jsou k dispozici v rámci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b671b-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="b671b-108">Hodnoty veřejná pole jen pro čtení, například <xref:System.IO.Path.InvalidPathChars> mohou být upravena kód nebo kód, který sdílí doménu aplikace vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="b671b-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="b671b-109">Jen pro čtení veřejné položky pole takto byste neměli používat k definování hranice chování vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b671b-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="b671b-110">Pokud tak učiníte, škodlivý kód můžete změnit definice hranic a použít kód neočekávaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="b671b-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="b671b-111">Ve verzi 2.0 a později rozhraní .NET Framework měli byste použít metody, které vrací nové pole místo použití veřejné položky pole.</span><span class="sxs-lookup"><span data-stu-id="b671b-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="b671b-112">Například místo použití <xref:System.IO.Path.InvalidPathChars> pole, měli byste použít <xref:System.IO.Path.GetInvalidPathChars%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="b671b-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="b671b-113">Všimněte si, že typy rozhraní .NET Framework nepoužívejte veřejná pole k definování typů hranic interně.</span><span class="sxs-lookup"><span data-stu-id="b671b-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="b671b-114">Místo toho rozhraní .NET Framework používá oddělené soukromé položky.</span><span class="sxs-lookup"><span data-stu-id="b671b-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="b671b-115">Změna hodnoty těchto polí veřejné nezmění chování typů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b671b-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b671b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b671b-116">See Also</span></span>  
 [<span data-ttu-id="b671b-117">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="b671b-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
