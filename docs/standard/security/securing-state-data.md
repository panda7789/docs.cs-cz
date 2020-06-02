---
title: Zabezpečení stavových dat
description: Deklaruje stavová data jako privátní nebo interní proměnné pro omezení přístupu k ní. Tato data jsou stále k dispozici prostřednictvím reflexe, serializace a ladění.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: b7fcb520fe6fa28cc098c4e1cbb56ce7da759c11
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291042"
---
# <a name="securing-state-data"></a><span data-ttu-id="4dbe4-104">Zabezpečení stavových dat</span><span class="sxs-lookup"><span data-stu-id="4dbe4-104">Securing State Data</span></span>
<span data-ttu-id="4dbe4-105">Aplikace, které zpracovávají citlivá data nebo mohou učinit jakékoli rozhodnutí o zabezpečení, musí uchovávat tato data pod svým vlastním ovládacím prvkem a nemohou jiným potenciálně škodlivému kódu přistupovat přímo k datům.</span><span class="sxs-lookup"><span data-stu-id="4dbe4-105">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="4dbe4-106">Nejlepším způsobem, jak chránit data v paměti, je deklarovat data jako privátní nebo interní (s oborem omezeným na stejné sestavení).</span><span class="sxs-lookup"><span data-stu-id="4dbe4-106">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="4dbe4-107">I tato data však podléhají přístupu, na které byste měli vědět:</span><span class="sxs-lookup"><span data-stu-id="4dbe4-107">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="4dbe4-108">Pomocí mechanismů reflexe, vysoce důvěryhodného kódu, který může odkazovat na váš objekt, mohou získat a nastavit soukromé členy.</span><span class="sxs-lookup"><span data-stu-id="4dbe4-108">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="4dbe4-109">Pomocí serializace může vysoce důvěryhodný kód efektivně získat a nastavit soukromé členy, pokud mají přístup k odpovídajícím datům v serializované podobě objektu.</span><span class="sxs-lookup"><span data-stu-id="4dbe4-109">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="4dbe4-110">V části ladění lze tato data číst.</span><span class="sxs-lookup"><span data-stu-id="4dbe4-110">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="4dbe4-111">Ujistěte se, že žádná z vašich vlastních metod ani vlastností tyto hodnoty neúmyslně zveřejňuje.</span><span class="sxs-lookup"><span data-stu-id="4dbe4-111">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dbe4-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4dbe4-112">See also</span></span>

- [<span data-ttu-id="4dbe4-113">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="4dbe4-113">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
