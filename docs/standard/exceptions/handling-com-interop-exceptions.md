---
title: Zpracování výjimek vzájemné spolupráce COM
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
ms.openlocfilehash: 17cd739ac40b43bdd4a93b83a4ab9d0d92400e2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708929"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="495a1-102">Zpracování výjimek vzájemné spolupráce COM</span><span class="sxs-lookup"><span data-stu-id="495a1-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="495a1-103">Spravovaný a nespravovaný kód může spolupracovat na zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="495a1-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="495a1-104">Pokud metoda vyvolá výjimku ve spravovaném kódu, může soubor Runtime společného jazyka předat objektu COM.</span><span class="sxs-lookup"><span data-stu-id="495a1-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="495a1-105">Pokud metoda selže v nespravovaném kódu vrácením selhání HRESULT, runtime vyvolá výjimku, která může být zachycena spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="495a1-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="495a1-106">Runtime automaticky mapuje HRESULT z komop na konkrétnější výjimky.</span><span class="sxs-lookup"><span data-stu-id="495a1-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="495a1-107">Například E_ACCESSDENIED <xref:System.UnauthorizedAccessException>se stane <xref:System.OutOfMemoryException>, E_OUTOFMEMORY se stane a tak dále.</span><span class="sxs-lookup"><span data-stu-id="495a1-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="495a1-108">Pokud HRESULT je vlastní výsledek nebo pokud není znám a runtime, <xref:System.Runtime.InteropServices.COMException> runtime předá obecné klientovi.</span><span class="sxs-lookup"><span data-stu-id="495a1-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="495a1-109">Vlastnost **ErrorCode** **výjimky COMException** obsahuje hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="495a1-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="495a1-110">Práce s IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="495a1-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="495a1-111">Při předání chyby z com spravovaného kódu, runtime naplní objekt výjimky s informacemi o chybě.</span><span class="sxs-lookup"><span data-stu-id="495a1-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="495a1-112">Objekty COM, které podporují IErrorInfo a vrátí funkce HRESULTS, poskytují tyto informace výjimkám spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="495a1-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="495a1-113">Například runtime mapuje popis z chyby COM <xref:System.Exception.Message%2A> na vlastnost výjimky.</span><span class="sxs-lookup"><span data-stu-id="495a1-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="495a1-114">Pokud HRESULT poskytuje žádné další informace o chybě, runtime vyplní mnoho vlastností výjimky s výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="495a1-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="495a1-115">Pokud metoda selže v nespravovaném kódu, může být výjimka předána segmentu spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="495a1-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="495a1-116">Téma [HRESULTS a Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) obsahuje tabulku zobrazující, jak HRESULTS mapuje na objekty výjimek za běhu.</span><span class="sxs-lookup"><span data-stu-id="495a1-116">The topic [HRESULTS and Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="495a1-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="495a1-117">See also</span></span>

- [<span data-ttu-id="495a1-118">Výjimky</span><span class="sxs-lookup"><span data-stu-id="495a1-118">Exceptions</span></span>](index.md)
