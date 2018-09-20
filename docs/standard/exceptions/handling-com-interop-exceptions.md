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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a17752257589ea4ee4d9e58182d4448f02f6460
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323114"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="5562d-102">Zpracování výjimek vzájemné spolupráce COM</span><span class="sxs-lookup"><span data-stu-id="5562d-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="5562d-103">Spravovaného a nespravovaného kódu můžou spolupracovat a zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="5562d-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="5562d-104">Pokud metoda vyvolá výjimku ve spravovaném kódu, modul common language runtime lze předat HRESULT objektu COM.</span><span class="sxs-lookup"><span data-stu-id="5562d-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="5562d-105">Jestliže metoda selže v nespravovaném kódu tak, že vrací selhání hodnoty HRESULT, modul runtime vyvolá výjimku, která může být zachycena spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="5562d-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="5562d-106">Modul runtime automaticky mapuje HRESULT z komunikace s objekty COM pro více specifické výjimky.</span><span class="sxs-lookup"><span data-stu-id="5562d-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="5562d-107">Například E_ACCESSDENIED stane <xref:System.UnauthorizedAccessException>, stane E_OUTOFMEMORY <xref:System.OutOfMemoryException>, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="5562d-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="5562d-108">Pokud je vlastní výsledek HRESULT nebo pokud neznámý modul runtime, modul runtime předá obecný <xref:System.Runtime.InteropServices.COMException> do klienta.</span><span class="sxs-lookup"><span data-stu-id="5562d-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="5562d-109">**ErrorCode** vlastnost **COMException** obsahuje hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5562d-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="5562d-110">Práce s IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="5562d-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="5562d-111">Při chybě je předán z modelu COM pro spravovaný kód, modul runtime naplní objekt výjimky s informacemi o chybě.</span><span class="sxs-lookup"><span data-stu-id="5562d-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="5562d-112">Objekty COM, které podporují IErrorInfo a vrátí výsledky HRESULT poskytnout tyto informace do spravovaného kódu výjimky.</span><span class="sxs-lookup"><span data-stu-id="5562d-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="5562d-113">Například modul runtime mapuje popisu v chybové zprávě modelu COM s výjimkou <xref:System.Exception.Message%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5562d-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="5562d-114">Pokud HRESULT neposkytuje žádné další informace o chybě, modul runtime vyplní mnoho vlastností výjimky s výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="5562d-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="5562d-115">Jestliže metoda selže v nespravovaném kódu, může být předán segment spravovaný kód výjimky.</span><span class="sxs-lookup"><span data-stu-id="5562d-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="5562d-116">Téma [výsledků HRESULT a výjimek](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) obsahuje tabulku, která ukazuje, jak HRESULTS mapují na objekty výjimek modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5562d-116">The topic [HRESULTS and Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="5562d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5562d-117">See also</span></span>

- [<span data-ttu-id="5562d-118">Výjimky</span><span class="sxs-lookup"><span data-stu-id="5562d-118">Exceptions</span></span>](index.md)
