---
title: Obálky COM
description: Klienti modelu COM a objekty .NET komunikují pomocí obálky s voláním modelu COM a obálky s voláním za běhu. CLR automaticky vytvoří obálky.
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
ms.openlocfilehash: f1cf84b8f15de1e3bd19a391767f5573f01ff806
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420510"
---
# <a name="com-wrappers"></a><span data-ttu-id="7140b-104">Obálky COM</span><span class="sxs-lookup"><span data-stu-id="7140b-104">COM Wrappers</span></span>
<span data-ttu-id="7140b-105">Model COM se liší od modelu objektu .NET runtime v několika důležitých způsobech:</span><span class="sxs-lookup"><span data-stu-id="7140b-105">COM differs from the .NET runtime object model in several important ways:</span></span>  
  
- <span data-ttu-id="7140b-106">Klienti objektů COM musí spravovat životnost těchto objektů; modul CLR (Common Language Runtime) spravuje životnost objektů ve svém prostředí.</span><span class="sxs-lookup"><span data-stu-id="7140b-106">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
- <span data-ttu-id="7140b-107">Klienti objektů COM zjišťují, zda je služba k dispozici, vyžádáním rozhraní, které poskytuje tuto službu a návratovým ukazatelem rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7140b-107">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="7140b-108">Klienti objektů .NET mohou získat popis funkcionality objektu pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="7140b-108">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
- <span data-ttu-id="7140b-109">Objekty sítě se nacházejí v paměti spravované spouštěcím prostředím modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="7140b-109">NET objects reside in memory managed by the .NET runtime execution environment.</span></span> <span data-ttu-id="7140b-110">Spouštěcí prostředí může přesunout objekty z paměti z důvodů výkonu a aktualizovat všechny odkazy na objekty, které přesouvá.</span><span class="sxs-lookup"><span data-stu-id="7140b-110">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="7140b-111">Nespravované klienty, kteří získali ukazatel na objekt, spoléhají na to, že objekt zůstane ve stejném umístění.</span><span class="sxs-lookup"><span data-stu-id="7140b-111">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="7140b-112">Tito klienti nemají žádný mechanismus pro práci s objektem, jehož umístění není opraveno.</span><span class="sxs-lookup"><span data-stu-id="7140b-112">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="7140b-113">Aby bylo možné tyto rozdíly překonat, modul runtime poskytuje obálkové třídy, aby spravované i nespravované klienty považovat za volání objektů v jejich příslušném prostředí.</span><span class="sxs-lookup"><span data-stu-id="7140b-113">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="7140b-114">Pokaždé, když váš spravovaný klient volá metodu na objekt modelu COM, modul runtime vytvoří obálku s voláním [za běhu](runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="7140b-114">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="7140b-115">RCW abstrakce rozdílů mezi spravovanými a nespravovanými referenčními mechanismy mimo jiné.</span><span class="sxs-lookup"><span data-stu-id="7140b-115">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="7140b-116">Modul runtime také vytvoří obálku s voláním [modelu COM](com-callable-wrapper.md) (doleva), aby mohl vrátit proces a povolit klientovi modelu COM bezproblémové volání metody objektu .NET.</span><span class="sxs-lookup"><span data-stu-id="7140b-116">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="7140b-117">Jak ukazuje následující obrázek, perspektiva volajícího kódu určuje, která Obálková Třída modul runtime vytvoří.</span><span class="sxs-lookup"><span data-stu-id="7140b-117">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 ![Přehled obálky COM](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 <span data-ttu-id="7140b-119">Ve většině případů standardní RCW nebo doleva generované modulem runtime poskytuje adekvátní zařazování pro volání, která překračují hranice mezi COM a .NET Runtime.</span><span class="sxs-lookup"><span data-stu-id="7140b-119">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET runtime.</span></span> <span data-ttu-id="7140b-120">Pomocí vlastních atributů můžete volitelně upravit způsob, jakým modul runtime představuje spravovaný a nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="7140b-120">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7140b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7140b-121">See also</span></span>

- <span data-ttu-id="7140b-122">[Pokročilá interoperabilita modelu COM v .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7140b-122">[Advanced COM Interoperability in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="7140b-123">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="7140b-123">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
- [<span data-ttu-id="7140b-124">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="7140b-124">COM Callable Wrapper</span></span>](com-callable-wrapper.md)
- <span data-ttu-id="7140b-125">[Přizpůsobení standardních obálek v .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7140b-125">[Customizing Standard Wrappers in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="7140b-126">[Postupy: přizpůsobení obálek za běhu, které lze volat v .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7140b-126">[How to: Customize Runtime Callable Wrappers in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span></span>
