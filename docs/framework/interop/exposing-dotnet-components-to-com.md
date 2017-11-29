---
title: "Vystavení komponent architektury .NET Framework pro COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9451504b64ddaa8dc0ea6b3a0754257b2c8b3824
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="e4209-102">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="e4209-102">Exposing .NET Framework Components to COM</span></span>
<span data-ttu-id="e4209-103">Zápis typ formátu .NET a využívání tohoto typu z nespravovaného kódu jsou odlišné aktivity pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="e4209-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="e4209-104">Tato část popisuje několik tipy pro vytvoření spravovaného kódu, které spolupracuje s klienty COM:</span><span class="sxs-lookup"><span data-stu-id="e4209-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>  
  
-   <span data-ttu-id="e4209-105">[Kvalifikace typů .NET pro spolupráci](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="e4209-105">[Qualifying .NET types for interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
     <span data-ttu-id="e4209-106">Všechny spravované typy, metody, vlastnosti, pole a události, které chcete vystavit do modelu COM musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="e4209-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="e4209-107">Typy musí mít veřejný výchozí konstruktor, který je jediný konstruktor, který lze vyvolat prostřednictvím modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e4209-107">Types must have a public default constructor, which is the only constructor that can be invoked through COM.</span></span>  
  
-   <span data-ttu-id="e4209-108">[Použití atributů spolupráce](../../../docs/framework/interop/applying-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="e4209-108">[Applying interop attributes](../../../docs/framework/interop/applying-interop-attributes.md).</span></span>  
  
     <span data-ttu-id="e4209-109">Vlastní atributy v rámci spravovaného kódu můžete zlepšení interakce komponenty.</span><span class="sxs-lookup"><span data-stu-id="e4209-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>  
  
-   <span data-ttu-id="e4209-110">[Balení sestavení pro model COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="e4209-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>  
  
     <span data-ttu-id="e4209-111">Vývojáři COM může vyžadovat, je vytvořit shrnutí jednotlivými kroky při odkazování na a nasazení vaší sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4209-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>  
  
 <span data-ttu-id="e4209-112">Kromě toho tato část popisuje úlohy související s využívání spravovaný typ z modelu COM klienta.</span><span class="sxs-lookup"><span data-stu-id="e4209-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>  
  
#### <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="e4209-113">Chcete-li využívat spravovaný typ z modelu COM</span><span class="sxs-lookup"><span data-stu-id="e4209-113">To consume a managed type from COM</span></span>  
  
1.  <span data-ttu-id="e4209-114">[Zaregistrovat sestavení modelu COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="e4209-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>  
  
     <span data-ttu-id="e4209-115">Typy v sestavení (a knihovny typů) musí být zaregistrován v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="e4209-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="e4209-116">Pokud instalační program nezaregistruje sestavení, požádejte COM vývojářům používat Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="e4209-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>  
  
2.  <span data-ttu-id="e4209-117">[Referenční typy .NET z modelu COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="e4209-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>  
  
     <span data-ttu-id="e4209-118">Vývojáři COM můžete odkazovat typy v sestavení pomocí stejné nástroje a techniky, které používají ještě dnes.</span><span class="sxs-lookup"><span data-stu-id="e4209-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>  
  
3.  <span data-ttu-id="e4209-119">[Volání objektu .NET](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33).</span><span class="sxs-lookup"><span data-stu-id="e4209-119">[Call a .NET object](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33).</span></span>  
  
     <span data-ttu-id="e4209-120">Vývojáři COM můžete volat metody pro objekt .NET stejným způsobem jako volání metody v libovolném nespravované typu.</span><span class="sxs-lookup"><span data-stu-id="e4209-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="e4209-121">Například COM **CoCreateInstance** aktivuje objekty .NET API.</span><span class="sxs-lookup"><span data-stu-id="e4209-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>  
  
4.  <span data-ttu-id="e4209-122">[Nasazení aplikace pro přístup COM](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce).</span><span class="sxs-lookup"><span data-stu-id="e4209-122">[Deploy an application for COM access](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce).</span></span>  
  
     <span data-ttu-id="e4209-123">Sestavení se silným názvem může být nainstalována v globální mezipaměti sestavení a vyžaduje podpis vydavatele.</span><span class="sxs-lookup"><span data-stu-id="e4209-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="e4209-124">Sestavení, které nejsou silné s názvem musí být nainstalován v adresáři aplikace klienta.</span><span class="sxs-lookup"><span data-stu-id="e4209-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4209-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4209-125">See Also</span></span>  
 [<span data-ttu-id="e4209-126">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="e4209-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="e4209-127">Ukázka zprostředkovatele komunikace s objekty COM: Klient COM a .NET serveru</span><span class="sxs-lookup"><span data-stu-id="e4209-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
