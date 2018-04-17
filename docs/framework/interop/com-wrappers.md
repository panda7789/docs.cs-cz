---
title: Obálky COM
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60f5acf6ed8a7fe0bb2e6293666c33a479d25643
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="com-wrappers"></a><span data-ttu-id="e90b8-102">Obálky COM</span><span class="sxs-lookup"><span data-stu-id="e90b8-102">COM Wrappers</span></span>
<span data-ttu-id="e90b8-103">COM se liší od objektový model rozhraní .NET Framework důležité několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="e90b8-103">COM differs from the .NET Framework object model in several important ways:</span></span>  
  
-   <span data-ttu-id="e90b8-104">Klienti COM – objekty musí spravovat dobu životnosti těchto objektů; modul common language runtime spravuje životnosti objektů ve svém prostředí.</span><span class="sxs-lookup"><span data-stu-id="e90b8-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
-   <span data-ttu-id="e90b8-105">Klienti COM – objekty zjistit, zda je služba k dispozici vyžádáním rozhraní, které poskytuje služby a získávání zpět ukazatele rozhraní, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="e90b8-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="e90b8-106">Klienti objekty .NET můžete získat popis objektu funkcí pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="e90b8-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
-   <span data-ttu-id="e90b8-107">NET objekty jsou umístěny v paměti spravuje prostředí pro spuštění rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e90b8-107">NET objects reside in memory managed by the .NET Framework execution environment.</span></span> <span data-ttu-id="e90b8-108">Spuštění prostředí můžete pohyb objektů v paměti z důvodů výkonu a aktualizujte všechny odkazy na objekty, které ji přesune.</span><span class="sxs-lookup"><span data-stu-id="e90b8-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="e90b8-109">Nespravované klientů, které získaly ukazatel na objekt, spoléhají na objekt, který má zůstat ve stejném umístění.</span><span class="sxs-lookup"><span data-stu-id="e90b8-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="e90b8-110">Tito klienti měli žádný mechanismus pro práci s objektem, jehož umístění není pevný.</span><span class="sxs-lookup"><span data-stu-id="e90b8-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="e90b8-111">K překonání tyto rozdíly, poskytuje modul runtime obálkové třídy, aby klienti spravovaných i nespravovaných vezměte v úvahu, že volají objektů v rámci příslušnému prostředí.</span><span class="sxs-lookup"><span data-stu-id="e90b8-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="e90b8-112">Vždy, když spravovaného klienta volá metodu na objekt modelu COM, modul runtime vytvoří [obálka volatelná za běhu](runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="e90b8-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="e90b8-113">RCWs abstraktní rozdíly mezi spravovanými a nespravovanými odkaz mechanismy, mimo jiné.</span><span class="sxs-lookup"><span data-stu-id="e90b8-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="e90b8-114">Modul runtime také vytvoří [obálka volatelná aplikacemi COM](com-callable-wrapper.md) (doleva), chcete-li se vrátit do, povolení klient COM bezproblémově volat metodu na objekt .NET.</span><span class="sxs-lookup"><span data-stu-id="e90b8-114">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="e90b8-115">Jak ukazuje následující obrázek, určuje, které Obálková třída modul runtime vytvoří perspektivy volající kód.</span><span class="sxs-lookup"><span data-stu-id="e90b8-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 <span data-ttu-id="e90b8-116">![Přehled obálky COM](media/bidirectional.gif "obousměrného")</span><span class="sxs-lookup"><span data-stu-id="e90b8-116">![COM wrapper overview](media/bidirectional.gif "bidirectional")</span></span>  
<span data-ttu-id="e90b8-117">Přehled obálky COM</span><span class="sxs-lookup"><span data-stu-id="e90b8-117">COM wrapper overview</span></span>  
  
 <span data-ttu-id="e90b8-118">Ve většině případů poskytuje standardní RCW nebo doleva generované modulem runtime odpovídající zařazování pro volání, které překračují hranice mezi COM a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e90b8-118">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET Framework.</span></span> <span data-ttu-id="e90b8-119">Pomocí vlastních atributů, můžete volitelně upravit způsob, jakým modul runtime představuje spravovanými a nespravovanými kódu.</span><span class="sxs-lookup"><span data-stu-id="e90b8-119">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e90b8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e90b8-120">See Also</span></span>  
 <span data-ttu-id="e90b8-121">[Interoperabilita modelů COM Upřesnit](https://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e90b8-121">[Advanced COM Interoperability](https://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb(v=vs.100))</span></span>  
 [<span data-ttu-id="e90b8-122">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="e90b8-122">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)  
 [<span data-ttu-id="e90b8-123">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="e90b8-123">COM Callable Wrapper</span></span>](com-callable-wrapper.md)  
 <span data-ttu-id="e90b8-124">[Přizpůsobení standardních obálek](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e90b8-124">[Customizing Standard Wrappers](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100))</span></span>  
 <span data-ttu-id="e90b8-125">[Postupy: přizpůsobení běhové obálky s možností](https://msdn.microsoft.com/library/4a4bb3da-4d60-4517-99f2-78d46a681732(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e90b8-125">[How to: Customize Runtime Callable Wrappers](https://msdn.microsoft.com/library/4a4bb3da-4d60-4517-99f2-78d46a681732(v=vs.100))</span></span>
