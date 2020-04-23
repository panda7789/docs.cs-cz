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
ms.openlocfilehash: 0223cb25b933cc84af49aa86d90259fdf1fd3efc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124175"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="2bb46-102">Postupy: Odkazování na typy .NET z modelu COM</span><span class="sxs-lookup"><span data-stu-id="2bb46-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="2bb46-103">Z hlediska kódu klienta a serveru jsou rozdíly mezi modelem COM a rozhraním .NET Framework z velké části nepostřehnutelné.</span><span class="sxs-lookup"><span data-stu-id="2bb46-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="2bb46-104">Klienti aplikace Microsoft Visual Basic mohou zobrazovat objekt rozhraní .NET v prohlížeči objektů, který vystavuje metody objektu a syntaxi, vlastnosti a pole přesně tak, jako by se jednalo o jakýkoli jiný objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="2bb46-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="2bb46-105">Proces importování knihovny typů je v případě klientů jazyka C++ poněkud složitější, ačkoli se pro exportování metadat do knihovny typů COM používají stejné nástroje.</span><span class="sxs-lookup"><span data-stu-id="2bb46-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="2bb46-106">Chcete-li odkazovat na členy objektu .NET z nespravovaného klienta jazyka C++, odkazujte na soubor TLB (vytvořený pomocí Tlbexp. exe) pomocí direktivy **#import** .</span><span class="sxs-lookup"><span data-stu-id="2bb46-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="2bb46-107">Při odkazování na knihovnu typů z jazyka C++, je nutné buď zadat možnost **raw_interfaces_only** , nebo importovat definice v knihovně základní třídy mscorlib. tlb.</span><span class="sxs-lookup"><span data-stu-id="2bb46-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="2bb46-108">Postup importování knihovny</span><span class="sxs-lookup"><span data-stu-id="2bb46-108">To import a library</span></span>  
  
- <span data-ttu-id="2bb46-109">Zadejte možnost **raw_interfaces_only** v direktivě **#import** .</span><span class="sxs-lookup"><span data-stu-id="2bb46-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="2bb46-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2bb46-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="2bb46-111">-nebo-</span><span class="sxs-lookup"><span data-stu-id="2bb46-111">-or-</span></span>  
  
- <span data-ttu-id="2bb46-112">Zadejte také direktivu #import pro knihovnu Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="2bb46-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="2bb46-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2bb46-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2bb46-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bb46-114">See also</span></span>

- [<span data-ttu-id="2bb46-115">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="2bb46-115">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="2bb46-116">Registrování sestav pomocí modelu COM</span><span class="sxs-lookup"><span data-stu-id="2bb46-116">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="2bb46-117">[Volání objektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2bb46-117">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="2bb46-118">[Nasazení aplikace pro přístup k modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2bb46-118">[Deploying an Application for COM Access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
