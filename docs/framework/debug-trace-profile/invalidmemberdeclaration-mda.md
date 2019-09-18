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
ms.openlocfilehash: fe15d718a9c5f91bfae4f37c04e726990e2fbd45
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052588"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="983bf-102">invalidMemberDeclaration – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="983bf-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="983bf-103">Je aktivován pomocník spravovaného ladění (MDA), který nahlásí chybu, ke které dojde při určení způsobu zařazení parametrů člena, který se má volat z modelu COM. `invalidMemberDeclaration`</span><span class="sxs-lookup"><span data-stu-id="983bf-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="983bf-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="983bf-104">Symptoms</span></span>  
 <span data-ttu-id="983bf-105">Neúspěšná hodnota HRESULT se vrátí do modelu COM bez volání spravované metody.</span><span class="sxs-lookup"><span data-stu-id="983bf-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="983bf-106">příčina</span><span class="sxs-lookup"><span data-stu-id="983bf-106">Cause</span></span>  
 <span data-ttu-id="983bf-107">Nejpravděpodobnější příčinou je nekompatibilní <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut u jednoho z parametrů.</span><span class="sxs-lookup"><span data-stu-id="983bf-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="983bf-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="983bf-108">Resolution</span></span>  
 <span data-ttu-id="983bf-109">Zadejte platné <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy pro parametry.</span><span class="sxs-lookup"><span data-stu-id="983bf-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="983bf-110">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="983bf-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="983bf-111">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="983bf-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="983bf-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="983bf-112">Output</span></span>  
 <span data-ttu-id="983bf-113">Informační zpráva obsahující název člena, název typu a chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="983bf-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="983bf-114">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="983bf-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="983bf-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="983bf-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="983bf-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="983bf-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="983bf-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="983bf-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
