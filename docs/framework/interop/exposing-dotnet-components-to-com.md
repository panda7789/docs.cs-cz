---
title: Vystavení součástí .NET pro COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
ms.openlocfilehash: 09045fb455a2163641d6f4af0ba07520ead59f1e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123490"
---
# <a name="exposing-net-components-to-com"></a><span data-ttu-id="fc428-102">Vystavení součástí .NET pro COM</span><span class="sxs-lookup"><span data-stu-id="fc428-102">Exposing .NET components to COM</span></span>

<span data-ttu-id="fc428-103">Zápis typu rozhraní .NET a využití tohoto typu z nespravovaného kódu jsou odlišné aktivity pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="fc428-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="fc428-104">Tato část popisuje několik tipů pro psaní spravovaného kódu, který spolupracuje s klienty modelu COM:</span><span class="sxs-lookup"><span data-stu-id="fc428-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>

- <span data-ttu-id="fc428-105">[Kvalifikování typů .NET pro spoluprovozování](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="fc428-105">[Qualifying .NET types for interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

     <span data-ttu-id="fc428-106">Všechny spravované typy, metody, vlastnosti, pole a události, které chcete zveřejnit pro model COM, musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="fc428-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="fc428-107">Typy musí mít veřejný konstruktor bez parametrů, který je jediným konstruktorem, který lze vyvolat pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="fc428-107">Types must have a public parameterless constructor, which is the only constructor that can be invoked through COM.</span></span>

- <span data-ttu-id="fc428-108">[Použití atributů spolupráce](../../standard/native-interop/apply-interop-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="fc428-108">[Applying interop attributes](../../standard/native-interop/apply-interop-attributes.md).</span></span>

     <span data-ttu-id="fc428-109">Vlastní atributy v rámci spravovaného kódu mohou zlepšit interoperabilitu komponenty.</span><span class="sxs-lookup"><span data-stu-id="fc428-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>

- <span data-ttu-id="fc428-110">[Balení sestavení pro model COM](packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="fc428-110">[Packaging an assembly for COM](packaging-an-assembly-for-com.md).</span></span>

     <span data-ttu-id="fc428-111">Vývojáři modelu COM mohou vyžadovat, aby byly shrnuty kroky při odkazování a nasazení vašich sestavení.</span><span class="sxs-lookup"><span data-stu-id="fc428-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>

 <span data-ttu-id="fc428-112">Kromě toho tato část identifikuje úlohy týkající se využívání spravovaného typu z klienta modelu COM.</span><span class="sxs-lookup"><span data-stu-id="fc428-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>

## <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="fc428-113">Využití spravovaného typu z modelu COM</span><span class="sxs-lookup"><span data-stu-id="fc428-113">To consume a managed type from COM</span></span>

1. <span data-ttu-id="fc428-114">[Registrovat sestavení pomocí modelu COM](registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="fc428-114">[Register assemblies with COM](registering-assemblies-with-com.md).</span></span>

     <span data-ttu-id="fc428-115">Typy v sestavení (a knihovnách typů) musí být registrovány v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="fc428-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="fc428-116">Pokud instalační program neregistruje sestavení, dejte vývojářům modelu COM pokyn, aby používal nástroj Regasm. exe.</span><span class="sxs-lookup"><span data-stu-id="fc428-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>

2. <span data-ttu-id="fc428-117">[Odkazování na typy .NET z modelu COM](how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="fc428-117">[Reference .NET types from COM](how-to-reference-net-types-from-com.md).</span></span>

     <span data-ttu-id="fc428-118">Vývojáři modelu COM mohou odkazovat na typy v sestavení pomocí stejných nástrojů a technik, které dnes používají.</span><span class="sxs-lookup"><span data-stu-id="fc428-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>

3. <span data-ttu-id="fc428-119">[Zavolejte objekt .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fc428-119">[Call a .NET object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>

     <span data-ttu-id="fc428-120">Vývojáři modelu COM mohou volat metody objektu .NET stejným způsobem jako volání metod na jakýkoli nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="fc428-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="fc428-121">Například rozhraní API pro technologii COM **CoCreateInstance** aktivuje objekty .NET.</span><span class="sxs-lookup"><span data-stu-id="fc428-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>

4. <span data-ttu-id="fc428-122">[Nasaďte aplikaci pro přístup k modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fc428-122">[Deploy an application for COM access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>

     <span data-ttu-id="fc428-123">Sestavení se silným názvem může být nainstalováno v globální mezipaměti sestavení (GAC) a vyžaduje podpis od jeho vydavatele.</span><span class="sxs-lookup"><span data-stu-id="fc428-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="fc428-124">Sestavení, která nemají silný název, musí být nainstalována v adresáři aplikace klienta.</span><span class="sxs-lookup"><span data-stu-id="fc428-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc428-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc428-125">See also</span></span>

- [<span data-ttu-id="fc428-126">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="fc428-126">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="fc428-127">Ukázka zprostředkovatele komunikace s objekty COM: klient COM a server .NET</span><span class="sxs-lookup"><span data-stu-id="fc428-127">COM Interop Sample: COM Client and .NET Server</span></span>](com-interop-sample-com-client-and-net-server.md)
