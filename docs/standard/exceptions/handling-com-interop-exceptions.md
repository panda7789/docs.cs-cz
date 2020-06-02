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
ms.openlocfilehash: 9c8eb374058ddbd2ba3d866079f0f40b292b69ea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286103"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="6b32e-102">Zpracování výjimek vzájemné spolupráce COM</span><span class="sxs-lookup"><span data-stu-id="6b32e-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="6b32e-103">Spravovaný a nespravovaný kód může spolupracovat na zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="6b32e-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="6b32e-104">Pokud metoda vyvolá výjimku ve spravovaném kódu, modul CLR (Common Language Runtime) může předat HRESULT objektu COM.</span><span class="sxs-lookup"><span data-stu-id="6b32e-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="6b32e-105">Pokud metoda selže v nespravovaném kódu vrácením chyby HRESULT, modul runtime vyvolá výjimku, která může být zachycena spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="6b32e-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="6b32e-106">Modul runtime automaticky mapuje HRESULT z zprostředkovatele komunikace s objekty COM na konkrétnější výjimky.</span><span class="sxs-lookup"><span data-stu-id="6b32e-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="6b32e-107">Například E_ACCESSDENIED se bude <xref:System.UnauthorizedAccessException> E_OUTOFMEMORY <xref:System.OutOfMemoryException> a tak dále.</span><span class="sxs-lookup"><span data-stu-id="6b32e-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="6b32e-108">Pokud je HRESULT vlastní výsledek nebo pokud je neznámý pro modul runtime, modul runtime předá <xref:System.Runtime.InteropServices.COMException> klientovi Obecné.</span><span class="sxs-lookup"><span data-stu-id="6b32e-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="6b32e-109">Vlastnost **ErrorCode** třídy **COMEXCEPTION** obsahuje hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="6b32e-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="6b32e-110">Práce s IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="6b32e-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="6b32e-111">Pokud je předána chyba z modelu COM do spravovaného kódu, modul runtime naplní objekt výjimky informacemi o chybě.</span><span class="sxs-lookup"><span data-stu-id="6b32e-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="6b32e-112">Objekty modelu COM, které podporují IErrorInfo a vracejí hodnoty HRESULT, poskytují tyto informace pro výjimky spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6b32e-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="6b32e-113">Například modul runtime mapuje popis z chyby COM na <xref:System.Exception.Message%2A> vlastnost výjimky.</span><span class="sxs-lookup"><span data-stu-id="6b32e-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="6b32e-114">Pokud HRESULT neposkytuje žádné další informace o chybě, modul runtime vyplní mnoho vlastností výjimky výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="6b32e-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="6b32e-115">Pokud metoda v nespravovaném kódu dojde k chybě, může být výjimka předána spravovanému segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="6b32e-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="6b32e-116">Téma [HRESULTS a Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) obsahuje tabulku, která ukazuje, jak jsou HRESULTS mapovány na objekty výjimek za běhu.</span><span class="sxs-lookup"><span data-stu-id="6b32e-116">The topic [HRESULTS and Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="6b32e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b32e-117">See also</span></span>

- [<span data-ttu-id="6b32e-118">Výjimky</span><span class="sxs-lookup"><span data-stu-id="6b32e-118">Exceptions</span></span>](index.md)
