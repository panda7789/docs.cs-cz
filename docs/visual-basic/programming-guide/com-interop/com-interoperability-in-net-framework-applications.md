---
title: "Interoperabilita modelů COM v aplikacích .NET Framework (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9347f7771e0e86f9a19cbec94ef59dcf1bdb250
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="87e57-102">Interoperabilita modelů COM v aplikacích .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87e57-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="87e57-103">Pokud chcete použít objekty COM a .NET Framework objekty ve stejné aplikaci, budete muset vyřešit rozdíly v tom, jak existují objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="87e57-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="87e57-104">Objekt rozhraní .NET Framework je umístěn ve spravované paměti – paměť řízené modul common language runtime – a může podle potřeby přesunout modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="87e57-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="87e57-105">Objekt COM se nachází v nespravované paměti a neočekává přesunout do jiného umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="87e57-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="87e57-106">a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] poskytují nástroje pro řízení interakce těchto spravovaných a nespravovaných součásti.</span><span class="sxs-lookup"><span data-stu-id="87e57-106"> and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="87e57-107">Další informace o spravovaném kódu najdete v tématu [modul Common Language Runtime](../../../standard/clr.md).</span><span class="sxs-lookup"><span data-stu-id="87e57-107">For more information about managed code, see [Common Language Runtime](../../../standard/clr.md).</span></span>  
  
 <span data-ttu-id="87e57-108">Kromě použití objektů COM v aplikacích .NET, můžete také použít [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vyvíjet objekty, které jsou přístupné z nespravovaného kódu pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="87e57-108">In addition to using COM objects in .NET applications, you may also want to use [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="87e57-109">Odkazy na této stránce obsahují podrobné informace o interakcích mezi objekty modelu COM a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87e57-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="87e57-110">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="87e57-110">Related Sections</span></span>  
 [<span data-ttu-id="87e57-111">Zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="87e57-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="87e57-112">Obsahuje odkazy na témata týkající se interoperabilita modelů COM v jazyce Visual Basic, včetně COM objekty, ActiveX – ovládací prvky, knihovny DLL Win32, spravované objekty a dědičnosti objektů COM.</span><span class="sxs-lookup"><span data-stu-id="87e57-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="87e57-113">Chyba obálky zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="87e57-113">COM Interop Wrapper Error</span></span>](/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="87e57-114">Popisuje důsledky a možnosti, pokud systém projektu nelze vytvořit obálku vzájemná funkční spolupráce COM pro konkrétní součást.</span><span class="sxs-lookup"><span data-stu-id="87e57-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="87e57-115">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="87e57-115">Interoperating with Unmanaged Code</span></span>](https://msdn.microsoft.com/library/sd10k43k)  
 <span data-ttu-id="87e57-116">Stručně popisuje některé z potíží interakce mezi spravovanými a nespravovanými kódu a obsahuje odkazy na další studie.</span><span class="sxs-lookup"><span data-stu-id="87e57-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="87e57-117">COM – obálky</span><span class="sxs-lookup"><span data-stu-id="87e57-117">COM Wrappers</span></span>](../../../framework/interop/com-wrappers.md)  
 <span data-ttu-id="87e57-118">Popisuje běhové obálky s možností, které umožňují spravovaného kódu k volání metody modelu COM, a COM – obálky s možností, které klientům COM k volání metody objekt .NET.</span><span class="sxs-lookup"><span data-stu-id="87e57-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="87e57-119">Interoperabilita modelů COM Upřesnit</span><span class="sxs-lookup"><span data-stu-id="87e57-119">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="87e57-120">Obsahuje odkazy na témata týkající se funkční spolupráce COM s ohledem na obálky, výjimky, dědičnosti, dělení na vlákna, události, převody a zařazování.</span><span class="sxs-lookup"><span data-stu-id="87e57-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="87e57-121">Tlbimp.exe (Importér knihovny)</span><span class="sxs-lookup"><span data-stu-id="87e57-121">Tlbimp.exe (Type Library Importer)</span></span>](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 <span data-ttu-id="87e57-122">Popisuje nástroje, které můžete použít pro převod definic typů v rámci knihovny typů COM nalezen do ekvivalentní definice v běžné sestavení modulu runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="87e57-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
