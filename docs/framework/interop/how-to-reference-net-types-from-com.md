---
title: 'Postupy: Odkazování na typy .NET z modelu COM'
description: Odkazování na typy .NET z modelu COM. Klienti VB můžou zobrazit objekt .NET v prohlížeči objektů, ale klienti C++ musí odkazovat na soubor TLB s \# direktivou import.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
ms.openlocfilehash: f8d052c7b9bac9c4bab61ab1950e9e89a7c73912
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618958"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="64f2a-104">Postupy: Odkazování na typy .NET z modelu COM</span><span class="sxs-lookup"><span data-stu-id="64f2a-104">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="64f2a-105">Z hlediska kódu klienta a serveru jsou rozdíly mezi modelem COM a rozhraním .NET Framework z velké části nepostřehnutelné.</span><span class="sxs-lookup"><span data-stu-id="64f2a-105">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="64f2a-106">Klienti aplikace Microsoft Visual Basic mohou zobrazovat objekt rozhraní .NET v prohlížeči objektů, který vystavuje metody objektu a syntaxi, vlastnosti a pole přesně tak, jako by se jednalo o jakýkoli jiný objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="64f2a-106">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="64f2a-107">Proces importování knihovny typů je v případě klientů jazyka C++ poněkud složitější, ačkoli se pro exportování metadat do knihovny typů COM používají stejné nástroje.</span><span class="sxs-lookup"><span data-stu-id="64f2a-107">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="64f2a-108">Chcete-li odkazovat na členy objektu .NET z nespravovaného klienta jazyka C++, odkazujte na soubor TLB (vytvořený pomocí Tlbexp.exe) s direktivou **#import** .</span><span class="sxs-lookup"><span data-stu-id="64f2a-108">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="64f2a-109">Při odkazování na knihovnu typů z jazyka C++, je nutné buď zadat možnost **raw_interfaces_only** , nebo importovat definice v knihovně základní třídy mscorlib. tlb.</span><span class="sxs-lookup"><span data-stu-id="64f2a-109">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="64f2a-110">Postup importování knihovny</span><span class="sxs-lookup"><span data-stu-id="64f2a-110">To import a library</span></span>  
  
- <span data-ttu-id="64f2a-111">Zadejte možnost **raw_interfaces_only** v direktivě **#import** .</span><span class="sxs-lookup"><span data-stu-id="64f2a-111">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="64f2a-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="64f2a-112">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="64f2a-113">-nebo-</span><span class="sxs-lookup"><span data-stu-id="64f2a-113">-or-</span></span>  
  
- <span data-ttu-id="64f2a-114">Zadejte také direktivu #import pro knihovnu Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="64f2a-114">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="64f2a-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="64f2a-115">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="64f2a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64f2a-116">See also</span></span>

- [<span data-ttu-id="64f2a-117">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="64f2a-117">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="64f2a-118">Registrování sestav pomocí modelu COM</span><span class="sxs-lookup"><span data-stu-id="64f2a-118">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="64f2a-119">[Volání objektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="64f2a-119">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="64f2a-120">[Nasazení aplikace pro přístup k modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="64f2a-120">[Deploying an Application for COM Access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
