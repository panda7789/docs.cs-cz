---
title: Vystavení komponent architektury .NET Framework pro COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a6c2b755b87f6f01f08f54a2f2fc567868dbb55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626351"
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="fa6d4-102">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="fa6d4-102">Exposing .NET Framework Components to COM</span></span>
<span data-ttu-id="fa6d4-103">Zápis typ formátu .NET a použití typu z nespravovaného kódu jsou různé aktivity pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="fa6d4-104">Tato část popisuje několik tipů pro vytváření spravovaného kódu, který spolupracuje s klienty modelu COM:</span><span class="sxs-lookup"><span data-stu-id="fa6d4-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>  
  
- <span data-ttu-id="fa6d4-105">[Kvalifikace typů .NET pro součinnost](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="fa6d4-105">[Qualifying .NET types for interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
     <span data-ttu-id="fa6d4-106">Všechny spravované typy, metody, vlastnosti, pole a události, které chcete vystavit rozhraní COM musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="fa6d4-107">Typy musí mít veřejný výchozí konstruktor, který je jediný konstruktor, který lze vyvolat pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-107">Types must have a public default constructor, which is the only constructor that can be invoked through COM.</span></span>  
  
- <span data-ttu-id="fa6d4-108">[Použití atributů spolupráce](../../../docs/framework/interop/applying-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="fa6d4-108">[Applying interop attributes](../../../docs/framework/interop/applying-interop-attributes.md).</span></span>  
  
     <span data-ttu-id="fa6d4-109">Vlastní atributy v rámci spravovaného kódu můžete vylepšit spolupráci komponenty.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>  
  
- <span data-ttu-id="fa6d4-110">[Zabalení sestavení pro model COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="fa6d4-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>  
  
     <span data-ttu-id="fa6d4-111">Vývojáři modelu COM může vyžadovat vytvořit souhrn kroky při odkazování na a nasazení vašeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>  
  
 <span data-ttu-id="fa6d4-112">Kromě toho tato část identifikuje úlohy týkající se používání spravovaného typu z modelu COM klienta.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>  
  
#### <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="fa6d4-113">Chcete-li využívají spravovaného typu z modelu COM</span><span class="sxs-lookup"><span data-stu-id="fa6d4-113">To consume a managed type from COM</span></span>  
  
1. <span data-ttu-id="fa6d4-114">[Registrace sestavení s modelem COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="fa6d4-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>  
  
     <span data-ttu-id="fa6d4-115">Typy v sestavení (a knihovny typů) musí být zaregistrovaný v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="fa6d4-116">Pokud instalační program nezaregistruje sestavení, dáte pokyn, aby vývojářům modelu COM pomocí Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>  
  
2. <span data-ttu-id="fa6d4-117">[Odkazování na typy .NET z modelu COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="fa6d4-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>  
  
     <span data-ttu-id="fa6d4-118">Vývojáři modelu COM může odkazovat na typy v sestavení pomocí stejné nástroje a techniky, které jeho tým dnes používá.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>  
  
3. <span data-ttu-id="fa6d4-119">[Volání objektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fa6d4-119">[Call a .NET object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>  
  
     <span data-ttu-id="fa6d4-120">Vývojáři modelu COM může volat metody u objektu rozhraní .NET stejným způsobem jako volání metody v libovolném nespravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="fa6d4-121">Například COM **CoCreateInstance** API aktivuje objektů .NET.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>  
  
4. <span data-ttu-id="fa6d4-122">[Nasazení aplikace pro přístup COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fa6d4-122">[Deploy an application for COM access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>  
  
     <span data-ttu-id="fa6d4-123">Sestavení se silným názvem může být nainstalována v globální mezipaměti sestavení a vyžaduje podpis od vydavatele.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="fa6d4-124">Sestavení, která nejsou silný název musí být nainstalována v adresáři aplikace klienta.</span><span class="sxs-lookup"><span data-stu-id="fa6d4-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa6d4-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa6d4-125">See also</span></span>

- [<span data-ttu-id="fa6d4-126">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="fa6d4-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="fa6d4-127">Ukázka zprostředkovatele s objekty COM: Klient COM a .NET Server</span><span class="sxs-lookup"><span data-stu-id="fa6d4-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
