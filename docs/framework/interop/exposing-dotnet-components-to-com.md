---
title: Vystavení součástí .NET pro COM
description: Zveřejněte součásti .NET pro COM. Kvalifikovat typy rozhraní .NET pro spoluprovozování. Použití atributů spolupráce Zabalit sestavení pro COM Využívání spravovaného typu z modelu COM.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
ms.openlocfilehash: 918c90f6741047f7d3cdf89a9b182700ecb2ed93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617454"
---
# <a name="exposing-net-components-to-com"></a><span data-ttu-id="19b0f-107">Vystavení součástí .NET pro COM</span><span class="sxs-lookup"><span data-stu-id="19b0f-107">Exposing .NET components to COM</span></span>

<span data-ttu-id="19b0f-108">Zápis typu rozhraní .NET a využití tohoto typu z nespravovaného kódu jsou odlišné aktivity pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="19b0f-108">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="19b0f-109">Tato část popisuje několik tipů pro psaní spravovaného kódu, který spolupracuje s klienty modelu COM:</span><span class="sxs-lookup"><span data-stu-id="19b0f-109">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>

- <span data-ttu-id="19b0f-110">[Kvalifikování typů .NET pro spoluprovozování](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="19b0f-110">[Qualifying .NET types for interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

     <span data-ttu-id="19b0f-111">Všechny spravované typy, metody, vlastnosti, pole a události, které chcete zveřejnit pro model COM, musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="19b0f-111">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="19b0f-112">Typy musí mít veřejný konstruktor bez parametrů, který je jediným konstruktorem, který lze vyvolat pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="19b0f-112">Types must have a public parameterless constructor, which is the only constructor that can be invoked through COM.</span></span>

- <span data-ttu-id="19b0f-113">[Použití atributů spolupráce](../../standard/native-interop/apply-interop-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="19b0f-113">[Applying interop attributes](../../standard/native-interop/apply-interop-attributes.md).</span></span>

     <span data-ttu-id="19b0f-114">Vlastní atributy v rámci spravovaného kódu mohou zlepšit interoperabilitu komponenty.</span><span class="sxs-lookup"><span data-stu-id="19b0f-114">Custom attributes within managed code can enhance the interoperability of a component.</span></span>

- <span data-ttu-id="19b0f-115">[Balení sestavení pro model COM](packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="19b0f-115">[Packaging an assembly for COM](packaging-an-assembly-for-com.md).</span></span>

     <span data-ttu-id="19b0f-116">Vývojáři modelu COM mohou vyžadovat, aby byly shrnuty kroky při odkazování a nasazení vašich sestavení.</span><span class="sxs-lookup"><span data-stu-id="19b0f-116">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>

 <span data-ttu-id="19b0f-117">Kromě toho tato část identifikuje úlohy týkající se využívání spravovaného typu z klienta modelu COM.</span><span class="sxs-lookup"><span data-stu-id="19b0f-117">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>

## <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="19b0f-118">Využití spravovaného typu z modelu COM</span><span class="sxs-lookup"><span data-stu-id="19b0f-118">To consume a managed type from COM</span></span>

1. <span data-ttu-id="19b0f-119">[Registrovat sestavení pomocí modelu COM](registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="19b0f-119">[Register assemblies with COM](registering-assemblies-with-com.md).</span></span>

     <span data-ttu-id="19b0f-120">Typy v sestavení (a knihovnách typů) musí být registrovány v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="19b0f-120">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="19b0f-121">Pokud instalační program neregistruje sestavení, sdělte vývojářům modelu COM, aby používali Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="19b0f-121">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>

2. <span data-ttu-id="19b0f-122">[Odkazování na typy .NET z modelu COM](how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="19b0f-122">[Reference .NET types from COM](how-to-reference-net-types-from-com.md).</span></span>

     <span data-ttu-id="19b0f-123">Vývojáři modelu COM mohou odkazovat na typy v sestavení pomocí stejných nástrojů a technik, které dnes používají.</span><span class="sxs-lookup"><span data-stu-id="19b0f-123">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>

3. <span data-ttu-id="19b0f-124">[Zavolejte objekt .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="19b0f-124">[Call a .NET object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>

     <span data-ttu-id="19b0f-125">Vývojáři modelu COM mohou volat metody objektu .NET stejným způsobem jako volání metod na jakýkoli nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="19b0f-125">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="19b0f-126">Například rozhraní API pro technologii COM **CoCreateInstance** aktivuje objekty .NET.</span><span class="sxs-lookup"><span data-stu-id="19b0f-126">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>

4. <span data-ttu-id="19b0f-127">[Nasaďte aplikaci pro přístup k modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="19b0f-127">[Deploy an application for COM access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>

     <span data-ttu-id="19b0f-128">Sestavení se silným názvem může být nainstalováno v globální mezipaměti sestavení (GAC) a vyžaduje podpis od jeho vydavatele.</span><span class="sxs-lookup"><span data-stu-id="19b0f-128">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="19b0f-129">Sestavení, která nemají silný název, musí být nainstalována v adresáři aplikace klienta.</span><span class="sxs-lookup"><span data-stu-id="19b0f-129">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>

## <a name="see-also"></a><span data-ttu-id="19b0f-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19b0f-130">See also</span></span>

- [<span data-ttu-id="19b0f-131">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="19b0f-131">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="19b0f-132">Ukázka zprostředkovatele s objekty COM: klient COM a server .NET</span><span class="sxs-lookup"><span data-stu-id="19b0f-132">COM Interop Sample: COM Client and .NET Server</span></span>](com-interop-sample-com-client-and-net-server.md)
