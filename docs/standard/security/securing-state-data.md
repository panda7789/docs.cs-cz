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
ms.openlocfilehash: c30bd2fe9e1ed371be2db60739d3b329fea788c7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705896"
---
# <a name="securing-state-data"></a><span data-ttu-id="1c8c7-102">Zabezpečení stavových dat</span><span class="sxs-lookup"><span data-stu-id="1c8c7-102">Securing State Data</span></span>
<span data-ttu-id="1c8c7-103">Aplikace, které zpracovávají citlivá data nebo mohou učinit jakékoli rozhodnutí o zabezpečení, musí uchovávat tato data pod svým vlastním ovládacím prvkem a nemohou jiným potenciálně škodlivému kódu přistupovat přímo k datům.</span><span class="sxs-lookup"><span data-stu-id="1c8c7-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="1c8c7-104">Nejlepším způsobem, jak chránit data v paměti, je deklarovat data jako privátní nebo interní (s oborem omezeným na stejné sestavení).</span><span class="sxs-lookup"><span data-stu-id="1c8c7-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="1c8c7-105">I tato data však podléhají přístupu, na které byste měli vědět:</span><span class="sxs-lookup"><span data-stu-id="1c8c7-105">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="1c8c7-106">Pomocí mechanismů reflexe, vysoce důvěryhodného kódu, který může odkazovat na váš objekt, mohou získat a nastavit soukromé členy.</span><span class="sxs-lookup"><span data-stu-id="1c8c7-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="1c8c7-107">Pomocí serializace může vysoce důvěryhodný kód efektivně získat a nastavit soukromé členy, pokud mají přístup k odpovídajícím datům v serializované podobě objektu.</span><span class="sxs-lookup"><span data-stu-id="1c8c7-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="1c8c7-108">V části ladění lze tato data číst.</span><span class="sxs-lookup"><span data-stu-id="1c8c7-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="1c8c7-109">Ujistěte se, že žádná z vašich vlastních metod ani vlastností tyto hodnoty neúmyslně zveřejňuje.</span><span class="sxs-lookup"><span data-stu-id="1c8c7-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c8c7-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c8c7-110">See also</span></span>

- [<span data-ttu-id="1c8c7-111">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="1c8c7-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
