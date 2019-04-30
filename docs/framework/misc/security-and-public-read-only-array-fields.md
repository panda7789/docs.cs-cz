---
title: Zabezpečené a veřejné položky pole určené pouze pro čtení
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19b5ad73150697c1442056642a1b11d504ecc426
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61869743"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="02e2f-102">Zabezpečené a veřejné položky pole určené pouze pro čtení</span><span class="sxs-lookup"><span data-stu-id="02e2f-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="02e2f-103">Nikdy nepoužívejte pole jen pro čtení veřejné pole ze spravované knihovny k definování hranice chování nebo zabezpečení vašich aplikací, protože veřejné pole jen pro čtení pole je možné upravit.</span><span class="sxs-lookup"><span data-stu-id="02e2f-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02e2f-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02e2f-104">Remarks</span></span>  
 <span data-ttu-id="02e2f-105">Některé třídy rozhraní .NET framework zahrnují jen pro čtení veřejné pole, které obsahují parametry specifické pro platformu hranice.</span><span class="sxs-lookup"><span data-stu-id="02e2f-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="02e2f-106">Například <xref:System.IO.Path.InvalidPathChars> pole je pole, která popisuje znaky, které nejsou povoleny v řetězci cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="02e2f-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="02e2f-107">Mnoho podobná pole jsou k dispozici v celém rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="02e2f-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="02e2f-108">Hodnoty veřejného polí jen pro čtení, jako jsou <xref:System.IO.Path.InvalidPathChars> můžete změnit váš kód nebo kód, který sdílí váš kód domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="02e2f-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="02e2f-109">Veřejné pole jen pro čtení pole tímto způsobem byste neměli používat k definování hranice chování vašich aplikací.</span><span class="sxs-lookup"><span data-stu-id="02e2f-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="02e2f-110">Pokud tak učiníte, škodlivý kód může změnit definice hranic a používat váš kód neočekávaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="02e2f-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="02e2f-111">Ve verzi 2.0 a novější rozhraní .NET Framework měli byste použít metody, které vracejí nové pole namísto veřejná pole.</span><span class="sxs-lookup"><span data-stu-id="02e2f-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="02e2f-112">Například místo použití <xref:System.IO.Path.InvalidPathChars> pole, měli byste použít <xref:System.IO.Path.GetInvalidPathChars%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="02e2f-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="02e2f-113">Všimněte si, že typy rozhraní .NET Framework nepoužívejte veřejná pole k definování typů hranic interně.</span><span class="sxs-lookup"><span data-stu-id="02e2f-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="02e2f-114">Místo toho rozhraní .NET Framework používá samostatné privátní pole.</span><span class="sxs-lookup"><span data-stu-id="02e2f-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="02e2f-115">Změna hodnot tyto veřejné polí nezmění chování typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="02e2f-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e2f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02e2f-116">See also</span></span>

- [<span data-ttu-id="02e2f-117">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="02e2f-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
