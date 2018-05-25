---
title: 'Postupy: Odkazování na typy .NET z modelu COM'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0333cd73240e685b46917d85afe0876532db3fd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="48fba-102">Postupy: Odkazování na typy .NET z modelu COM</span><span class="sxs-lookup"><span data-stu-id="48fba-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="48fba-103">Z hlediska kódu klienta a serveru jsou rozdíly mezi modelem COM a rozhraním .NET Framework z velké části nepostřehnutelné.</span><span class="sxs-lookup"><span data-stu-id="48fba-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="48fba-104">Klienti aplikace Microsoft Visual Basic mohou zobrazovat objekt rozhraní .NET v prohlížeči objektů, který vystavuje metody objektu a syntaxi, vlastnosti a pole přesně tak, jako by se jednalo o jakýkoli jiný objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="48fba-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="48fba-105">Proces importování knihovny typů je v případě klientů jazyka C++ poněkud složitější, ačkoli se pro exportování metadat do knihovny typů COM používají stejné nástroje.</span><span class="sxs-lookup"><span data-stu-id="48fba-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="48fba-106">Chcete-li objekt členy rozhraní .NET z nespravovaného klienta C++, odkaz na soubor TLB (vytvořeného s Tlbexp.exe) s **#import** – direktiva.</span><span class="sxs-lookup"><span data-stu-id="48fba-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="48fba-107">Při odkazování na knihovny typů z jazyka C++, musíte buď zadat **raw_interfaces_only –** možnost nebo import definice v základní knihovně tříd, Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="48fba-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="48fba-108">Postup importování knihovny</span><span class="sxs-lookup"><span data-stu-id="48fba-108">To import a library</span></span>  
  
-   <span data-ttu-id="48fba-109">Zadejte **raw_interfaces_only –** možnost **#import** – direktiva.</span><span class="sxs-lookup"><span data-stu-id="48fba-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="48fba-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="48fba-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="48fba-111">-nebo-</span><span class="sxs-lookup"><span data-stu-id="48fba-111">-or-</span></span>  
  
-   <span data-ttu-id="48fba-112">Zadejte také direktivu #import pro knihovnu Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="48fba-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="48fba-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="48fba-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="48fba-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="48fba-114">See Also</span></span>  
 [<span data-ttu-id="48fba-115">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="48fba-115">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="48fba-116">Registrování sestav pomocí modelu COM</span><span class="sxs-lookup"><span data-stu-id="48fba-116">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)  
 <span data-ttu-id="48fba-117">[Volání metody objekt .NET.](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="48fba-117">[Calling a .NET Object](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))</span></span>  
 <span data-ttu-id="48fba-118">[Nasazení aplikace pro přístup COM](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="48fba-118">[Deploying an Application for COM Access](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))</span></span>
