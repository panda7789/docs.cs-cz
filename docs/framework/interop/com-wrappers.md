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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b633239be85a66c5bba54132c3732357967eb177
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182933"
---
# <a name="com-wrappers"></a><span data-ttu-id="d455b-102">Obálky COM</span><span class="sxs-lookup"><span data-stu-id="d455b-102">COM Wrappers</span></span>
<span data-ttu-id="d455b-103">COM se liší od objektový model rozhraní .NET Framework důležité několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="d455b-103">COM differs from the .NET Framework object model in several important ways:</span></span>  
  
-   <span data-ttu-id="d455b-104">Klienti objektů COM musí spravovat dobu života těchto objektů; modul common language runtime spravuje životnosti objektů ve svém prostředí.</span><span class="sxs-lookup"><span data-stu-id="d455b-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
-   <span data-ttu-id="d455b-105">Klienti modelu COM objekty zjistit, zda je služba k dispozici vyžádáním rozhraní, které poskytuje služby a získat zpět ukazatel rozhraní, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="d455b-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="d455b-106">Klienti objektů .NET můžete získat popis objektu funkcí pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="d455b-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
-   <span data-ttu-id="d455b-107">NET objekty jsou umístěny v paměti spravuje prostředí pro spouštění rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d455b-107">NET objects reside in memory managed by the .NET Framework execution environment.</span></span> <span data-ttu-id="d455b-108">Spouštěcí prostředí můžete přesouvat objekty v paměti kvůli výkonu a aktualizovat všechny odkazy na objekty, které přesunu.</span><span class="sxs-lookup"><span data-stu-id="d455b-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="d455b-109">Nespravovaní klienti, které získaly ukazatel na objekt, spoléhají na objekt, který má zůstat ve stejném umístění.</span><span class="sxs-lookup"><span data-stu-id="d455b-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="d455b-110">Tito klienti mají žádný mechanismus pro práci s objektem, jehož umístění nebyly odstraněny.</span><span class="sxs-lookup"><span data-stu-id="d455b-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="d455b-111">Chcete-li vyřešit tyto rozdíly, modul runtime poskytuje obálkové třídy, aby klienti spravovaných i nespravovaných myslíte, že volání objektů v rámci svých odpovídajících prostředí.</span><span class="sxs-lookup"><span data-stu-id="d455b-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="d455b-112">Pokaždé, když spravovaného klienta volá metodu na objekt modelu COM, modul runtime vytvoří [obálka volatelná za běhu](runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="d455b-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="d455b-113">RCW abstraktní rozdíly mezi spravovanými a nespravovanými odkaz mechanismy mimo jiné.</span><span class="sxs-lookup"><span data-stu-id="d455b-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="d455b-114">Modul runtime vytvoří také [obálka volatelná aplikacemi COM](com-callable-wrapper.md) (CCW) vrátit procesu a umožnit tak klient modelu COM bez problémů volat metodu na objekt .NET.</span><span class="sxs-lookup"><span data-stu-id="d455b-114">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="d455b-115">Jak ukazuje následující obrázek, určuje, které obálkovou třídu modul runtime vytvoří perspektivy volající kód.</span><span class="sxs-lookup"><span data-stu-id="d455b-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 ![Přehled obálky COM](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 <span data-ttu-id="d455b-117">Ve většině případů poskytuje standardní obálky RCW nebo objekt CCW vygenerované modulem runtime odpovídající zařazování pro volání, které překračují hranice mezi modelem COM a rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d455b-117">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET Framework.</span></span> <span data-ttu-id="d455b-118">Pomocí vlastních atributů, můžete volitelně můžete upravit způsob, jakým modul runtime představuje spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="d455b-118">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d455b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d455b-119">See also</span></span>

- <span data-ttu-id="d455b-120">[Rozšířená interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d455b-120">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="d455b-121">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="d455b-121">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
- [<span data-ttu-id="d455b-122">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="d455b-122">COM Callable Wrapper</span></span>](com-callable-wrapper.md)
- <span data-ttu-id="d455b-123">[Přizpůsobení standardních obálek](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d455b-123">[Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="d455b-124">[Postupy: Přizpůsobení obálek Volatelných za běhu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d455b-124">[How to: Customize Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span></span>
