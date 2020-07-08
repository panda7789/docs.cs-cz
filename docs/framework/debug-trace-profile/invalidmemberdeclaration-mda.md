---
title: invalidMemberDeclaration – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění Invalidmemberdeclaration –, který se vyvolá, pokud se vrátí hodnota HRESULT do modelu COM bez volání spravované metody.
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: 5dbfba2baec3263d91746c06379438e97a81f005
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051711"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="2a084-103">invalidMemberDeclaration – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="2a084-103">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="2a084-104">`invalidMemberDeclaration`Je aktivován pomocník spravovaného ladění (MDA), který nahlásí chybu, ke které dojde při určení způsobu zařazení parametrů člena, který se má volat z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="2a084-104">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2a084-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="2a084-105">Symptoms</span></span>  
 <span data-ttu-id="2a084-106">Neúspěšná hodnota HRESULT se vrátí do modelu COM bez volání spravované metody.</span><span class="sxs-lookup"><span data-stu-id="2a084-106">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2a084-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="2a084-107">Cause</span></span>  
 <span data-ttu-id="2a084-108">Nejpravděpodobnější příčinou je nekompatibilní <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut u jednoho z parametrů.</span><span class="sxs-lookup"><span data-stu-id="2a084-108">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2a084-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="2a084-109">Resolution</span></span>  
 <span data-ttu-id="2a084-110">Zadejte platné <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy pro parametry.</span><span class="sxs-lookup"><span data-stu-id="2a084-110">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2a084-111">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="2a084-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="2a084-112">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="2a084-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2a084-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="2a084-113">Output</span></span>  
 <span data-ttu-id="2a084-114">Informační zpráva obsahující název člena, název typu a chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="2a084-114">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2a084-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="2a084-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a084-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a084-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="2a084-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="2a084-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="2a084-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="2a084-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
