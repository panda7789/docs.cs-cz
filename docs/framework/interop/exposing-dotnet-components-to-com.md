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
ms.openlocfilehash: b5c80ba473b0080a1368c82949c765820239ef25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715735"
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="edab5-102">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="edab5-102">Exposing .NET Framework Components to COM</span></span>
<span data-ttu-id="edab5-103">Zápis typ formátu .NET a použití typu z nespravovaného kódu jsou různé aktivity pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="edab5-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="edab5-104">Tato část popisuje několik tipů pro vytváření spravovaného kódu, který spolupracuje s klienty modelu COM:</span><span class="sxs-lookup"><span data-stu-id="edab5-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>  
  
-   <span data-ttu-id="edab5-105">[Kvalifikace typů .NET pro součinnost](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="edab5-105">[Qualifying .NET types for interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
     <span data-ttu-id="edab5-106">Všechny spravované typy, metody, vlastnosti, pole a události, které chcete vystavit rozhraní COM musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="edab5-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="edab5-107">Typy musí mít veřejný výchozí konstruktor, který je jediný konstruktor, který lze vyvolat pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="edab5-107">Types must have a public default constructor, which is the only constructor that can be invoked through COM.</span></span>  
  
-   <span data-ttu-id="edab5-108">[Použití atributů spolupráce](../../../docs/framework/interop/applying-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="edab5-108">[Applying interop attributes](../../../docs/framework/interop/applying-interop-attributes.md).</span></span>  
  
     <span data-ttu-id="edab5-109">Vlastní atributy v rámci spravovaného kódu můžete vylepšit spolupráci komponenty.</span><span class="sxs-lookup"><span data-stu-id="edab5-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>  
  
-   <span data-ttu-id="edab5-110">[Zabalení sestavení pro model COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="edab5-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>  
  
     <span data-ttu-id="edab5-111">Vývojáři modelu COM může vyžadovat vytvořit souhrn kroky při odkazování na a nasazení vašeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="edab5-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>  
  
 <span data-ttu-id="edab5-112">Kromě toho tato část identifikuje úlohy týkající se používání spravovaného typu z modelu COM klienta.</span><span class="sxs-lookup"><span data-stu-id="edab5-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>  
  
#### <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="edab5-113">Chcete-li využívají spravovaného typu z modelu COM</span><span class="sxs-lookup"><span data-stu-id="edab5-113">To consume a managed type from COM</span></span>  
  
1.  <span data-ttu-id="edab5-114">[Registrace sestavení s modelem COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="edab5-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>  
  
     <span data-ttu-id="edab5-115">Typy v sestavení (a knihovny typů) musí být zaregistrovaný v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="edab5-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="edab5-116">Pokud instalační program nezaregistruje sestavení, dáte pokyn, aby vývojářům modelu COM pomocí Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="edab5-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>  
  
2.  <span data-ttu-id="edab5-117">[Odkazování na typy .NET z modelu COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="edab5-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>  
  
     <span data-ttu-id="edab5-118">Vývojáři modelu COM může odkazovat na typy v sestavení pomocí stejné nástroje a techniky, které jeho tým dnes používá.</span><span class="sxs-lookup"><span data-stu-id="edab5-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>  
  
3.  <span data-ttu-id="edab5-119">[Volání objektu .NET](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="edab5-119">[Call a .NET object](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100)).</span></span>  
  
     <span data-ttu-id="edab5-120">Vývojáři modelu COM může volat metody u objektu rozhraní .NET stejným způsobem jako volání metody v libovolném nespravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="edab5-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="edab5-121">Například COM **CoCreateInstance** API aktivuje objektů .NET.</span><span class="sxs-lookup"><span data-stu-id="edab5-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>  
  
4.  <span data-ttu-id="edab5-122">[Nasazení aplikace pro přístup COM](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="edab5-122">[Deploy an application for COM access](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100)).</span></span>  
  
     <span data-ttu-id="edab5-123">Sestavení se silným názvem může být nainstalována v globální mezipaměti sestavení a vyžaduje podpis od vydavatele.</span><span class="sxs-lookup"><span data-stu-id="edab5-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="edab5-124">Sestavení, která nejsou silný název musí být nainstalována v adresáři aplikace klienta.</span><span class="sxs-lookup"><span data-stu-id="edab5-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edab5-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="edab5-125">See also</span></span>
- [<span data-ttu-id="edab5-126">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="edab5-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="edab5-127">Ukázka zprostředkovatele s objekty COM: Klient COM a .NET Server</span><span class="sxs-lookup"><span data-stu-id="edab5-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
