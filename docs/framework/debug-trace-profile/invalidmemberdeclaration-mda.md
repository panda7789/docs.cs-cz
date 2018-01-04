---
title: "invalidMemberDeclaration – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4f625cbc7d7c46eee5b2eb8d7e47d4a5754fc26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="eb538-102">invalidMemberDeclaration – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="eb538-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="eb538-103">`invalidMemberDeclaration` Pomocník spravovaného ladění (MDA) je aktivováno zobrazovat chyby, ke kterému dochází při zjišťování, jak přeuspořádat parametry členem, abyste mohli volat z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="eb538-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="eb538-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="eb538-104">Symptoms</span></span>  
 <span data-ttu-id="eb538-105">Selhání HRESULT je vrácen do modelu COM bez spravovaného byla volání metody.</span><span class="sxs-lookup"><span data-stu-id="eb538-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="eb538-106">příčina</span><span class="sxs-lookup"><span data-stu-id="eb538-106">Cause</span></span>  
 <span data-ttu-id="eb538-107">Příčinou je pravděpodobně z důvodu nekompatibilní <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut na jeden z parametrů.</span><span class="sxs-lookup"><span data-stu-id="eb538-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="eb538-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="eb538-108">Resolution</span></span>  
 <span data-ttu-id="eb538-109">Zadejte platný <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributů na parametry.</span><span class="sxs-lookup"><span data-stu-id="eb538-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="eb538-110">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="eb538-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="eb538-111">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="eb538-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="eb538-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="eb538-112">Output</span></span>  
 <span data-ttu-id="eb538-113">Informační zpráva obsahujícího název člena, název typu a chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="eb538-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="eb538-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="eb538-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb538-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb538-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="eb538-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="eb538-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="eb538-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="eb538-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
