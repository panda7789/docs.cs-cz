---
title: Interoperabilita modelů COM v aplikacích .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: ceef4255321e208911a16db0227890bc6654b8c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642920"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="d7521-102">Interoperabilita modelů COM v aplikacích .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7521-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="d7521-103">Pokud chcete použít objekty COM a .NET Framework objekty ve stejné aplikaci, budete muset vyřešit rozdíly v tom, jak existují objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="d7521-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="d7521-104">Objekt rozhraní .NET Framework je umístěn ve spravované paměti – paměť řízené modul common language runtime – a může podle potřeby přesunout modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="d7521-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="d7521-105">Objekt COM se nachází v nespravované paměti a neočekává přesunout do jiného umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="d7521-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> <span data-ttu-id="d7521-106">Visual Studio a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] poskytují nástroje pro řízení interakce těchto spravovaných a nespravovaných součásti.</span><span class="sxs-lookup"><span data-stu-id="d7521-106">Visual Studio and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="d7521-107">Další informace o spravovaném kódu najdete v tématu [modul Common Language Runtime](../../../standard/clr.md).</span><span class="sxs-lookup"><span data-stu-id="d7521-107">For more information about managed code, see [Common Language Runtime](../../../standard/clr.md).</span></span>  
  
 <span data-ttu-id="d7521-108">Kromě použití objektů COM v aplikacích .NET, můžete také pomocí jazyka Visual Basic pro vývoj objekty, které jsou přístupné z nespravovaného kódu pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d7521-108">In addition to using COM objects in .NET applications, you may also want to use Visual Basic to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="d7521-109">Odkazy na této stránce obsahují podrobné informace o interakcích mezi objekty modelu COM a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7521-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d7521-110">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d7521-110">Related Sections</span></span>  
 [<span data-ttu-id="d7521-111">Zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="d7521-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="d7521-112">Obsahuje odkazy na témata týkající se interoperabilita modelů COM v jazyce Visual Basic, včetně COM objekty, ActiveX – ovládací prvky, knihovny DLL Win32, spravované objekty a dědičnosti objektů COM.</span><span class="sxs-lookup"><span data-stu-id="d7521-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="d7521-113">Chyba obálky zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="d7521-113">COM Interop Wrapper Error</span></span>](/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="d7521-114">Popisuje důsledky a možnosti, pokud systém projektu nelze vytvořit obálku vzájemná funkční spolupráce COM pro konkrétní součást.</span><span class="sxs-lookup"><span data-stu-id="d7521-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="d7521-115">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="d7521-115">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="d7521-116">Stručně popisuje některé z potíží interakce mezi spravovanými a nespravovanými kódu a obsahuje odkazy na další studie.</span><span class="sxs-lookup"><span data-stu-id="d7521-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="d7521-117">COM – obálky</span><span class="sxs-lookup"><span data-stu-id="d7521-117">COM Wrappers</span></span>](../../../framework/interop/com-wrappers.md)  
 <span data-ttu-id="d7521-118">Popisuje běhové obálky s možností, které umožňují spravovaného kódu k volání metody modelu COM, a COM – obálky s možností, které klientům COM k volání metody objekt .NET.</span><span class="sxs-lookup"><span data-stu-id="d7521-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="d7521-119">Interoperabilita modelů COM Upřesnit</span><span class="sxs-lookup"><span data-stu-id="d7521-119">Advanced COM Interoperability</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="d7521-120">Obsahuje odkazy na témata týkající se funkční spolupráce COM s ohledem na obálky, výjimky, dědičnosti, dělení na vlákna, události, převody a zařazování.</span><span class="sxs-lookup"><span data-stu-id="d7521-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="d7521-121">Tlbimp.exe (importér knihovny typů)</span><span class="sxs-lookup"><span data-stu-id="d7521-121">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 <span data-ttu-id="d7521-122">Popisuje nástroje, které můžete použít pro převod definic typů v rámci knihovny typů COM nalezen do ekvivalentní definice v běžné sestavení modulu runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="d7521-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
