---
title: "Zabezpečení stavových dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bd41f5174f426e723ea7e069eaee8f2d367625a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="securing-state-data"></a><span data-ttu-id="10190-102">Zabezpečení stavových dat</span><span class="sxs-lookup"><span data-stu-id="10190-102">Securing State Data</span></span>
<span data-ttu-id="10190-103">Aplikace, které zpracovávají důvěrná data nebo se přesvědčte, jakýkoli druh rozhodnutí týkající se zabezpečení je třeba ponechat data v rámci své vlastní ovládací prvek a nelze povolit další potenciálně škodlivého kódu, chcete-li získat přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="10190-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="10190-104">Nejlepší způsob, jak chránit data v paměti je deklarovat data jako soukromý nebo interní (s rozsahem omezené na stejném sestavení) proměnné.</span><span class="sxs-lookup"><span data-stu-id="10190-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="10190-105">Ale i tato data jsou přístupná, byste měli vědět:</span><span class="sxs-lookup"><span data-stu-id="10190-105">However, even this data is subject to access you should be aware of:</span></span>  
  
-   <span data-ttu-id="10190-106">Pomocí reflexe mechanismy, vysoce důvěryhodný kód, který může odkazovat objektu získat a nastavte soukromé členy.</span><span class="sxs-lookup"><span data-stu-id="10190-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
-   <span data-ttu-id="10190-107">Pomocí serializace, vysoce důvěryhodný kód můžete efektivně získat a nastavit soukromé členy, pokud má přístup k odpovídající data ve formuláři serializovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="10190-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
-   <span data-ttu-id="10190-108">V části ladění, můžete tato data přečíst.</span><span class="sxs-lookup"><span data-stu-id="10190-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="10190-109">Zajistěte, aby že žádné metody nebo vlastnosti neúmyslně zpřístupňuje tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="10190-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10190-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="10190-110">See Also</span></span>  
 [<span data-ttu-id="10190-111">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="10190-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
