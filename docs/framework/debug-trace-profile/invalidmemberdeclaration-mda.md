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
ms.openlocfilehash: 6033cd4178b2bc493794b5dcc527bc543ba24284
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216300"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="14fbc-102">invalidMemberDeclaration – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="14fbc-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="14fbc-103">Aktivuje se Pomocník s `invalidMemberDeclaration`em spravovaného ladění (MDA), který nahlásí chybu, ke které dojde při určení způsobu zařazení parametrů člena, který se má volat z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="14fbc-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="14fbc-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="14fbc-104">Symptoms</span></span>  
 <span data-ttu-id="14fbc-105">Neúspěšná hodnota HRESULT se vrátí do modelu COM bez volání spravované metody.</span><span class="sxs-lookup"><span data-stu-id="14fbc-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="14fbc-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="14fbc-106">Cause</span></span>  
 <span data-ttu-id="14fbc-107">Nejpravděpodobnější příčinou je nekompatibilní atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> u jednoho z parametrů.</span><span class="sxs-lookup"><span data-stu-id="14fbc-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="14fbc-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="14fbc-108">Resolution</span></span>  
 <span data-ttu-id="14fbc-109">Zadejte platné atributy <xref:System.Runtime.InteropServices.MarshalAsAttribute> u parametrů.</span><span class="sxs-lookup"><span data-stu-id="14fbc-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="14fbc-110">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="14fbc-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="14fbc-111">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="14fbc-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="14fbc-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="14fbc-112">Output</span></span>  
 <span data-ttu-id="14fbc-113">Informační zpráva obsahující název člena, název typu a chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="14fbc-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="14fbc-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="14fbc-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="14fbc-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="14fbc-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="14fbc-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="14fbc-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="14fbc-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="14fbc-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
