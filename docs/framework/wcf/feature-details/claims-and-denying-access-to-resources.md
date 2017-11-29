---
title: "Deklarace a odepření přístupu k prostředkům"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b94c8b77cd659438ec26129137dd9b8cab056b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="claims-and-denying-access-to-resources"></a><span data-ttu-id="d96ee-102">Deklarace a odepření přístupu k prostředkům</span><span class="sxs-lookup"><span data-stu-id="d96ee-102">Claims and Denying Access to Resources</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="d96ee-103">podporuje mechanismus ověřování založené na deklaracích identity.</span><span class="sxs-lookup"><span data-stu-id="d96ee-103"> supports a claims-based authorization mechanism.</span></span> <span data-ttu-id="d96ee-104">A také povolení přístup k prostředkům na základě přítomnosti deklarací identity, systémy často odepřít přístup k prostředkům na základě přítomnosti deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="d96ee-104">As well as allowing access to resources based on the presence of claims, systems often deny access to resources based on the presence of claims.</span></span> <span data-ttu-id="d96ee-105">Tyto systémy měli zkontrolovat <xref:System.IdentityModel.Policy.AuthorizationContext> pro deklarace identity, jejichž výsledkem je před hledáním deklarace identity, jejichž výsledkem je povolen přístup odepřen přístup.</span><span class="sxs-lookup"><span data-stu-id="d96ee-105">Such systems should examine the <xref:System.IdentityModel.Policy.AuthorizationContext> for claims that result in access being denied before looking for claims that result in access being allowed.</span></span>  
  
 <span data-ttu-id="d96ee-106">Například může systém odepřít přístup k prostředku na každý, kdo má deklarace identity s typem z `Age`, napravo od <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>a hodnota prostředků `Under 21` pouze když tuto identitu má také deklarace identity typu `Name`, napravo od <xref:System.IdentityModel.Claims.Rights.Identity%2A>, a hodnota prostředků `Mallory`.</span><span class="sxs-lookup"><span data-stu-id="d96ee-106">For example, a system might deny access to a resource to anyone who has a claim with a type of `Age`, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource value of `Under 21` only when that identity also has a claim of type `Name`, a right of <xref:System.IdentityModel.Claims.Rights.Identity%2A>, and a resource value of `Mallory`.</span></span> <span data-ttu-id="d96ee-107">Jinými slovy, systém odepře přístup všem uživatelům, kteří je do 21 let a udělí přístup, pokud je název Mallory.</span><span class="sxs-lookup"><span data-stu-id="d96ee-107">Put another way, the system denies access to anyone who is under 21 years old and grants access when the name is Mallory.</span></span> <span data-ttu-id="d96ee-108">Toto správně implementovat sémantického, je důležité Hledat `Age` nejprve deklarace identity a určit, zda je stáří do 21 let.</span><span class="sxs-lookup"><span data-stu-id="d96ee-108">To correctly implement this semantic, it is important to look for the `Age` claim first and determine whether the age is under 21 years old.</span></span> <span data-ttu-id="d96ee-109">Jinak, pokud Mallory je v části 21, pak prostředku může mít udělen přístup výhradně na základě těchto `Name` deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="d96ee-109">Otherwise, if Mallory is under 21, then the resource may be granted access solely on the basis of the `Name` claim.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96ee-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d96ee-110">See Also</span></span>  
 [<span data-ttu-id="d96ee-111">Správa deklarací a autorizace s modelem Identity</span><span class="sxs-lookup"><span data-stu-id="d96ee-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="d96ee-112">Deklarace a tokeny</span><span class="sxs-lookup"><span data-stu-id="d96ee-112">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
