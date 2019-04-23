---
title: invalidMemberDeclaration – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e5b4cb4a04a79a748f4ea2292bac67a88a6e9f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131284"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="273c7-102">invalidMemberDeclaration – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="273c7-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="273c7-103">`invalidMemberDeclaration` Pomocníka spravovaného ladění (MDA) se aktivuje oznámit chybu, ke které dojde při určování způsobu zařazení parametrů člena se bude volat z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="273c7-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="273c7-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="273c7-104">Symptoms</span></span>  
 <span data-ttu-id="273c7-105">Selhání HRESULT se vrátí do modelu COM bez spravované metody s byla volána.</span><span class="sxs-lookup"><span data-stu-id="273c7-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="273c7-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="273c7-106">Cause</span></span>  
 <span data-ttu-id="273c7-107">Příčinou je pravděpodobně z důvodu nekompatibilní <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributu na jeden z parametrů.</span><span class="sxs-lookup"><span data-stu-id="273c7-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="273c7-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="273c7-108">Resolution</span></span>  
 <span data-ttu-id="273c7-109">Zadejte platný <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy na parametry.</span><span class="sxs-lookup"><span data-stu-id="273c7-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="273c7-110">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="273c7-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="273c7-111">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="273c7-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="273c7-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="273c7-112">Output</span></span>  
 <span data-ttu-id="273c7-113">Informační zpráva obsahující členské jméno, název typu a chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="273c7-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="273c7-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="273c7-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="273c7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="273c7-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="273c7-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="273c7-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="273c7-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="273c7-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
