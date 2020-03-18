---
title: Zabezpečení stavových dat
description: Deklarujte data stavu jako soukromé nebo interní proměnné, které omezí přístup k nim. Tato data lze stále přistupovat prostřednictvím reflexe, serializace a ladění.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: f95bf409f7eef8c2636d3c180d2bbd95fbc689c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186828"
---
# <a name="securing-state-data"></a><span data-ttu-id="13f64-104">Zabezpečení stavových dat</span><span class="sxs-lookup"><span data-stu-id="13f64-104">Securing State Data</span></span>
<span data-ttu-id="13f64-105">Aplikace, které zpracovávají citlivá data nebo dělají jakékoli rozhodnutí o zabezpečení, musí tato data uchovávat pod vlastní kontrolou a nemohou povolit přímý přístup k datům jinému potenciálně škodlivému kódu.</span><span class="sxs-lookup"><span data-stu-id="13f64-105">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="13f64-106">Nejlepší způsob, jak chránit data v paměti je deklarovat data jako soukromé nebo interní (s rozsahem omezena na stejné sestavení) proměnné.</span><span class="sxs-lookup"><span data-stu-id="13f64-106">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="13f64-107">Nicméně, i tyto údaje jsou předmětem přístupu, měli byste si být vědomi:</span><span class="sxs-lookup"><span data-stu-id="13f64-107">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="13f64-108">Pomocí reflexe mechanismy, vysoce důvěryhodný kód, který může odkazovat na objekt můžete získat a nastavit soukromé členy.</span><span class="sxs-lookup"><span data-stu-id="13f64-108">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="13f64-109">Pomocí serializace může vysoce důvěryhodný kód efektivně získat a nastavit soukromé členy, pokud má přístup k odpovídajícím datům v serializované podobě objektu.</span><span class="sxs-lookup"><span data-stu-id="13f64-109">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="13f64-110">Při ladění lze tato data číst.</span><span class="sxs-lookup"><span data-stu-id="13f64-110">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="13f64-111">Ujistěte se, že žádné z vlastních metod nebo vlastností neúmyslně nezveřejňuje tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="13f64-111">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f64-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="13f64-112">See also</span></span>

- [<span data-ttu-id="13f64-113">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="13f64-113">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
