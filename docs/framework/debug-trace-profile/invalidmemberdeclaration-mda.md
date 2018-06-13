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
ms.openlocfilehash: 0caa3add1a35d460527ce665352e5861df7d5d7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386334"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="07726-102">invalidMemberDeclaration – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="07726-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="07726-103">`invalidMemberDeclaration` Pomocník spravovaného ladění (MDA) je aktivováno zobrazovat chyby, ke kterému dochází při zjišťování, jak přeuspořádat parametry členem, abyste mohli volat z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="07726-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="07726-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="07726-104">Symptoms</span></span>  
 <span data-ttu-id="07726-105">Selhání HRESULT je vrácen do modelu COM bez spravovaného byla volání metody.</span><span class="sxs-lookup"><span data-stu-id="07726-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="07726-106">příčina</span><span class="sxs-lookup"><span data-stu-id="07726-106">Cause</span></span>  
 <span data-ttu-id="07726-107">Příčinou je pravděpodobně z důvodu nekompatibilní <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut na jeden z parametrů.</span><span class="sxs-lookup"><span data-stu-id="07726-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="07726-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="07726-108">Resolution</span></span>  
 <span data-ttu-id="07726-109">Zadejte platný <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributů na parametry.</span><span class="sxs-lookup"><span data-stu-id="07726-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="07726-110">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="07726-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="07726-111">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="07726-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="07726-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="07726-112">Output</span></span>  
 <span data-ttu-id="07726-113">Informační zpráva obsahujícího název člena, název typu a chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="07726-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="07726-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="07726-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="07726-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="07726-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="07726-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="07726-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="07726-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="07726-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
