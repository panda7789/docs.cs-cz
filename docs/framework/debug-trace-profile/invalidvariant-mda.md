---
title: invalidVariant – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c34f160b643a0431168097d3832357b4ac6e4557
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052564"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="02c2b-102">invalidVariant – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="02c2b-102">invalidVariant MDA</span></span>
<span data-ttu-id="02c2b-103">Pokud při volání z nativního nebo nespravovaného kódu do `VARIANT` spravovaného kódu dojde k neplatné struktuře, aktivuje se pomocník spravovanéholadění(MDA).`invalidVariant`</span><span class="sxs-lookup"><span data-stu-id="02c2b-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="02c2b-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="02c2b-104">Symptoms</span></span>  
 <span data-ttu-id="02c2b-105">Neočekávané chování během přechodu mezi nativním a spravovaným kódem, který zahrnuje zařazování `VARIANT` do objektu.</span><span class="sxs-lookup"><span data-stu-id="02c2b-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="02c2b-106">příčina</span><span class="sxs-lookup"><span data-stu-id="02c2b-106">Cause</span></span>  
 <span data-ttu-id="02c2b-107">Nativní kód předá poškozenou `VARIANT` strukturu spravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="02c2b-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="02c2b-108">Modul runtime se pokusí ho zařadit `VARIANT` do objektu a aktivovat objekt MDA, `VARIANT` Pokud není platný.</span><span class="sxs-lookup"><span data-stu-id="02c2b-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="02c2b-109">`VARIANT`Příklady neplatných s zahrnují `VARIANT` `VARTYPE` a VT_EMPTY &#124; VT_BYREF nebo `VARIANT` s `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="02c2b-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="02c2b-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="02c2b-110">Resolution</span></span>  
 <span data-ttu-id="02c2b-111">Nativní nebo nespravovaný kód, `VARIANT` `VARIANT` který projde, musí zajistit, aby byl správně vytvořen a inicializován.</span><span class="sxs-lookup"><span data-stu-id="02c2b-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="02c2b-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="02c2b-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="02c2b-113">MDA nemá žádný vliv na chování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="02c2b-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="02c2b-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="02c2b-114">Output</span></span>  
 <span data-ttu-id="02c2b-115">Zpráva MDA označující, že modul runtime zjistil neplatnou `VARIANT` chybu předanou spravovanému modulu spravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="02c2b-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="02c2b-116">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="02c2b-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02c2b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02c2b-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="02c2b-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="02c2b-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="02c2b-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="02c2b-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
