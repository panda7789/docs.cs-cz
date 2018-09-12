---
title: Zabezpečení stavových dat
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c821177ca897e617885425217ac0b6659b5ea6e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44493586"
---
# <a name="securing-state-data"></a><span data-ttu-id="fd515-102">Zabezpečení stavových dat</span><span class="sxs-lookup"><span data-stu-id="fd515-102">Securing State Data</span></span>
<span data-ttu-id="fd515-103">Aplikace, které zpracovávají citlivé údaje nebo provádět jakýkoli druh rozhodnutí o zabezpečení je třeba ponechat data v rámci své vlastní ovládací prvek a nelze povolit další kódu potenciálně škodlivý přistupovat k datům.</span><span class="sxs-lookup"><span data-stu-id="fd515-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="fd515-104">Nejlepší způsob, jak chránit data v paměti je deklarovat jako privátní nebo interní (s rozsahem omezené na stejné sestavení) proměnné.</span><span class="sxs-lookup"><span data-stu-id="fd515-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="fd515-105">Však i tato data jsou v souladu s přístupu, které byste měli vědět:</span><span class="sxs-lookup"><span data-stu-id="fd515-105">However, even this data is subject to access you should be aware of:</span></span>  
  
-   <span data-ttu-id="fd515-106">Pomocí reflexe mechanismů, vysoce důvěryhodným kódem, který může odkazovat na objekt získat a nastavit privátní členy.</span><span class="sxs-lookup"><span data-stu-id="fd515-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
-   <span data-ttu-id="fd515-107">Pomocí serializace, vysoce důvěryhodným kódem můžete efektivně získat a nastavit privátní členy, pokud má přístup k odpovídající data ve formuláři serializovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="fd515-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
-   <span data-ttu-id="fd515-108">V průběhu ladění, můžete tato data přečíst.</span><span class="sxs-lookup"><span data-stu-id="fd515-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="fd515-109">Ujistěte se, že žádná z vlastní metody nebo vlastnosti neúmyslně zpřístupňuje tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fd515-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd515-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd515-110">See also</span></span>

- [<span data-ttu-id="fd515-111">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="fd515-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
