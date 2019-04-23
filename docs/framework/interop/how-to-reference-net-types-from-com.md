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
ms.openlocfilehash: 1e033ba4b3b98367452b355363058adc7f1a5887
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198397"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="31f65-102">Postupy: Odkazování na typy .NET z modelu COM</span><span class="sxs-lookup"><span data-stu-id="31f65-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="31f65-103">Z hlediska kódu klienta a serveru jsou rozdíly mezi modelem COM a rozhraním .NET Framework z velké části nepostřehnutelné.</span><span class="sxs-lookup"><span data-stu-id="31f65-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="31f65-104">Klienti aplikace Microsoft Visual Basic mohou zobrazovat objekt rozhraní .NET v prohlížeči objektů, který vystavuje metody objektu a syntaxi, vlastnosti a pole přesně tak, jako by se jednalo o jakýkoli jiný objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="31f65-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="31f65-105">Proces importování knihovny typů je v případě klientů jazyka C++ poněkud složitější, ačkoli se pro exportování metadat do knihovny typů COM používají stejné nástroje.</span><span class="sxs-lookup"><span data-stu-id="31f65-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="31f65-106">K odkazování členy objektu rozhraní .NET z nespravovaného klienta jazyka C++, odkazu na soubor TLB (vytvořený pomocí Tlbexp.exe) s **#import** směrnice.</span><span class="sxs-lookup"><span data-stu-id="31f65-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="31f65-107">Při odkazování na knihovnu typů z C++, je nutné zadat buď **raw_interfaces_only** možnost nebo importovat definice do knihovny základních tříd Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="31f65-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="31f65-108">Postup importování knihovny</span><span class="sxs-lookup"><span data-stu-id="31f65-108">To import a library</span></span>  
  
-   <span data-ttu-id="31f65-109">Zadejte **raw_interfaces_only** možnost **#import** směrnice.</span><span class="sxs-lookup"><span data-stu-id="31f65-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="31f65-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="31f65-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="31f65-111">-nebo-</span><span class="sxs-lookup"><span data-stu-id="31f65-111">-or-</span></span>  
  
-   <span data-ttu-id="31f65-112">Zadejte také direktivu #import pro knihovnu Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="31f65-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="31f65-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="31f65-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="31f65-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31f65-114">See also</span></span>

- [<span data-ttu-id="31f65-115">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="31f65-115">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="31f65-116">Registrování sestav pomocí modelu COM</span><span class="sxs-lookup"><span data-stu-id="31f65-116">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="31f65-117">[Volání objektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="31f65-117">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="31f65-118">[Nasazení aplikace pro přístup k modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="31f65-118">[Deploying an Application for COM Access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
