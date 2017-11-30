---
title: "Spolupráce s nespravovaným kódem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2db5b8c2425637e24086f54e8ef69b0e5aac3633
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="15c88-102">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="15c88-102">Interoperating with Unmanaged Code</span></span>
<span data-ttu-id="15c88-103">Rozhraní .NET Framework zvýší úroveň interakci s COM komponenty modelu COM + služby, knihovny externích typů a mnoho služeb operačního systému.</span><span class="sxs-lookup"><span data-stu-id="15c88-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="15c88-104">Datové typy, metoda podpisy a zpracování chyb mechanismy liší mezi spravovanými a nespravovanými objektové modely.</span><span class="sxs-lookup"><span data-stu-id="15c88-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="15c88-105">Pro zjednodušení vzájemná spolupráce mezi součástmi rozhraní .NET Framework a nespravovaného kódu a usnadňují cesty migrace, modul common language runtime ukrývá od klientů a serverů rozdíly v těchto modelů objektu.</span><span class="sxs-lookup"><span data-stu-id="15c88-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>  
  
 <span data-ttu-id="15c88-106">Kód, který spouští pod kontrolou modulu runtime nazývá spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="15c88-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="15c88-107">Kód, který je spuštěn mimo modul runtime naopak se nazývá nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="15c88-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="15c88-108">COM – součásti ActiveX rozhraní a funkcí rozhraní API Win32 jsou příklady nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="15c88-108">COM components, ActiveX interfaces, and Win32 API functions are examples of unmanaged code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15c88-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="15c88-109">In This Section</span></span>  
 [<span data-ttu-id="15c88-110">Spolupráce s nespravovaným kódem postupy</span><span class="sxs-lookup"><span data-stu-id="15c88-110">Interoperating with Unmanaged Code How-to Topics</span></span>](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 <span data-ttu-id="15c88-111">Obsahuje odkazy na všechny postupy v rámcová dokumentace pro spolupráce s nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="15c88-111">Provides links to all How-to topics found in the conceptual documentation for interoperating with unmanaged code.</span></span>  
  
 [<span data-ttu-id="15c88-112">Vystavení součástí COM v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="15c88-112">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 <span data-ttu-id="15c88-113">Popisuje, jak komponenty modelu COM v aplikacích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15c88-113">Describes how to use COM components from .NET Framework applications.</span></span>  
  
 [<span data-ttu-id="15c88-114">Vystavení součástí .NET Framework do modelu COM</span><span class="sxs-lookup"><span data-stu-id="15c88-114">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="15c88-115">Popisuje způsob použití součásti rozhraní .NET Framework z aplikace modelu COM.</span><span class="sxs-lookup"><span data-stu-id="15c88-115">Describes how to use .NET Framework components from COM applications.</span></span>  
  
 [<span data-ttu-id="15c88-116">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="15c88-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="15c88-117">Popisuje, jak volat nespravovaný volání funkcí knihovny DLL pomocí platformy.</span><span class="sxs-lookup"><span data-stu-id="15c88-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="15c88-118">Aspekty návrhu pro spolupráci</span><span class="sxs-lookup"><span data-stu-id="15c88-118">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 <span data-ttu-id="15c88-119">Poskytuje tipy pro zápis integrované COM – součásti.</span><span class="sxs-lookup"><span data-stu-id="15c88-119">Provides tips for writing integrated COM components.</span></span>  
  
 [<span data-ttu-id="15c88-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="15c88-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 <span data-ttu-id="15c88-121">Popisuje zařazování pro vyvolání zprostředkovatel komunikace s objekty COM a platformu.</span><span class="sxs-lookup"><span data-stu-id="15c88-121">Describes marshaling for COM interop and platform invoke.</span></span>  
  
 [<span data-ttu-id="15c88-122">Postupy: mapování výsledků HRESULT a výjimek</span><span class="sxs-lookup"><span data-stu-id="15c88-122">How to: Map HRESULTs and Exceptions</span></span>](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 <span data-ttu-id="15c88-123">Popisuje mapování mezi výjimky a jejich hodnoty HRESULT.</span><span class="sxs-lookup"><span data-stu-id="15c88-123">Describes the mapping between exceptions and HRESULTs.</span></span>  
  
 [<span data-ttu-id="15c88-124">Spolupráce pomocí obecných typů</span><span class="sxs-lookup"><span data-stu-id="15c88-124">Interoperating Using Generic Types</span></span>](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 <span data-ttu-id="15c88-125">Popisuje chování při použití v zprostředkovatel komunikace s objekty COM – obecné typy.</span><span class="sxs-lookup"><span data-stu-id="15c88-125">Describes the behavior of generic types when used in COM interop.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="15c88-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="15c88-126">Related Sections</span></span>  
 [<span data-ttu-id="15c88-127">Interoperabilita modelů COM Upřesnit</span><span class="sxs-lookup"><span data-stu-id="15c88-127">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="15c88-128">Obsahuje odkazy na další informace o zahrnutí komponenty modelu COM do své aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15c88-128">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>
