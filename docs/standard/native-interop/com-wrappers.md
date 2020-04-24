---
title: Obálky COM
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
ms.openlocfilehash: d647a8cd73fa714e86454687a25501259f894f6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120715"
---
# <a name="com-wrappers"></a><span data-ttu-id="5ebca-102">Obálky COM</span><span class="sxs-lookup"><span data-stu-id="5ebca-102">COM Wrappers</span></span>
<span data-ttu-id="5ebca-103">Model COM se liší od modelu objektu .NET runtime v několika důležitých způsobech:</span><span class="sxs-lookup"><span data-stu-id="5ebca-103">COM differs from the .NET runtime object model in several important ways:</span></span>  
  
- <span data-ttu-id="5ebca-104">Klienti objektů COM musí spravovat životnost těchto objektů; modul CLR (Common Language Runtime) spravuje životnost objektů ve svém prostředí.</span><span class="sxs-lookup"><span data-stu-id="5ebca-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
- <span data-ttu-id="5ebca-105">Klienti objektů COM zjišťují, zda je služba k dispozici, vyžádáním rozhraní, které poskytuje tuto službu a návratovým ukazatelem rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5ebca-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="5ebca-106">Klienti objektů .NET mohou získat popis funkcionality objektu pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="5ebca-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
- <span data-ttu-id="5ebca-107">Objekty sítě se nacházejí v paměti spravované spouštěcím prostředím modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="5ebca-107">NET objects reside in memory managed by the .NET runtime execution environment.</span></span> <span data-ttu-id="5ebca-108">Spouštěcí prostředí může přesunout objekty z paměti z důvodů výkonu a aktualizovat všechny odkazy na objekty, které přesouvá.</span><span class="sxs-lookup"><span data-stu-id="5ebca-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="5ebca-109">Nespravované klienty, kteří získali ukazatel na objekt, spoléhají na to, že objekt zůstane ve stejném umístění.</span><span class="sxs-lookup"><span data-stu-id="5ebca-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="5ebca-110">Tito klienti nemají žádný mechanismus pro práci s objektem, jehož umístění není opraveno.</span><span class="sxs-lookup"><span data-stu-id="5ebca-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="5ebca-111">Aby bylo možné tyto rozdíly překonat, modul runtime poskytuje obálkové třídy, aby spravované i nespravované klienty považovat za volání objektů v jejich příslušném prostředí.</span><span class="sxs-lookup"><span data-stu-id="5ebca-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="5ebca-112">Pokaždé, když váš spravovaný klient volá metodu na objekt modelu COM, modul runtime vytvoří obálku s voláním [za běhu](runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="5ebca-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="5ebca-113">RCW abstrakce rozdílů mezi spravovanými a nespravovanými referenčními mechanismy mimo jiné.</span><span class="sxs-lookup"><span data-stu-id="5ebca-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="5ebca-114">Modul runtime také vytvoří obálku s voláním [modelu COM](com-callable-wrapper.md) (doleva), aby mohl vrátit proces a povolit klientovi modelu COM bezproblémové volání metody objektu .NET.</span><span class="sxs-lookup"><span data-stu-id="5ebca-114">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="5ebca-115">Jak ukazuje následující obrázek, perspektiva volajícího kódu určuje, která Obálková Třída modul runtime vytvoří.</span><span class="sxs-lookup"><span data-stu-id="5ebca-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 ![Přehled obálky COM](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 <span data-ttu-id="5ebca-117">Ve většině případů standardní RCW nebo doleva generované modulem runtime poskytuje adekvátní zařazování pro volání, která překračují hranice mezi COM a .NET Runtime.</span><span class="sxs-lookup"><span data-stu-id="5ebca-117">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET runtime.</span></span> <span data-ttu-id="5ebca-118">Pomocí vlastních atributů můžete volitelně upravit způsob, jakým modul runtime představuje spravovaný a nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5ebca-118">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ebca-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ebca-119">See also</span></span>

- <span data-ttu-id="5ebca-120">[Pokročilá interoperabilita modelu COM v .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5ebca-120">[Advanced COM Interoperability in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="5ebca-121">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="5ebca-121">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
- [<span data-ttu-id="5ebca-122">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="5ebca-122">COM Callable Wrapper</span></span>](com-callable-wrapper.md)
- <span data-ttu-id="5ebca-123">[Přizpůsobení standardních obálek v .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5ebca-123">[Customizing Standard Wrappers in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="5ebca-124">[Postupy: přizpůsobení obálek za běhu, které lze volat v .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5ebca-124">[How to: Customize Runtime Callable Wrappers in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span></span>
