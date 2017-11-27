---
title: "Obálky COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 733d7f3e56b8ed704003ca9d6c2aa858c713df93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="com-wrappers"></a><span data-ttu-id="8e4c2-102">Obálky COM</span><span class="sxs-lookup"><span data-stu-id="8e4c2-102">COM Wrappers</span></span>
<span data-ttu-id="8e4c2-103">COM se liší od objektový model rozhraní .NET Framework důležité několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="8e4c2-103">COM differs from the .NET Framework object model in several important ways:</span></span>  
  
-   <span data-ttu-id="8e4c2-104">Klienti COM – objekty musí spravovat dobu životnosti těchto objektů; modul common language runtime spravuje životnosti objektů ve svém prostředí.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
-   <span data-ttu-id="8e4c2-105">Klienti COM – objekty zjistit, zda je služba k dispozici vyžádáním rozhraní, které poskytuje služby a získávání zpět ukazatele rozhraní, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="8e4c2-106">Klienti objekty .NET můžete získat popis objektu funkcí pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
-   <span data-ttu-id="8e4c2-107">NET objekty jsou umístěny v paměti spravuje prostředí pro spuštění rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-107">NET objects reside in memory managed by the .NET Framework execution environment.</span></span> <span data-ttu-id="8e4c2-108">Spuštění prostředí můžete pohyb objektů v paměti z důvodů výkonu a aktualizujte všechny odkazy na objekty, které ji přesune.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="8e4c2-109">Nespravované klientů, které získaly ukazatel na objekt, spoléhají na objekt, který má zůstat ve stejném umístění.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="8e4c2-110">Tito klienti měli žádný mechanismus pro práci s objektem, jehož umístění není pevný.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="8e4c2-111">K překonání tyto rozdíly, poskytuje modul runtime obálkové třídy, aby klienti spravovaných i nespravovaných vezměte v úvahu, že volají objektů v rámci příslušnému prostředí.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="8e4c2-112">Vždy, když spravovaného klienta volá metodu na objekt modelu COM, modul runtime vytvoří [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="8e4c2-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="8e4c2-113">RCWs abstraktní rozdíly mezi spravovanými a nespravovanými odkaz mechanismy, mimo jiné.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="8e4c2-114">Modul runtime také vytvoří [obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md) (doleva), chcete-li se vrátit do, povolení klient COM bezproblémově volat metodu na objekt .NET.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-114">The runtime also creates a [COM callable wrapper](../../../docs/framework/interop/com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="8e4c2-115">Jak ukazuje následující obrázek, určuje, které Obálková třída modul runtime vytvoří perspektivy volající kód.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 <span data-ttu-id="8e4c2-116">![Přehled obálky COM](../../../docs/framework/interop/media/bidirectional.gif "obousměrného")</span><span class="sxs-lookup"><span data-stu-id="8e4c2-116">![COM wrapper overview](../../../docs/framework/interop/media/bidirectional.gif "bidirectional")</span></span>  
<span data-ttu-id="8e4c2-117">Přehled obálky COM</span><span class="sxs-lookup"><span data-stu-id="8e4c2-117">COM wrapper overview</span></span>  
  
 <span data-ttu-id="8e4c2-118">Ve většině případů poskytuje standardní RCW nebo doleva generované modulem runtime odpovídající zařazování pro volání, které překračují hranice mezi COM a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-118">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET Framework.</span></span> <span data-ttu-id="8e4c2-119">Pomocí vlastních atributů, můžete volitelně upravit způsob, jakým modul runtime představuje spravovanými a nespravovanými kódu.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-119">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e4c2-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e4c2-120">See Also</span></span>  
 [<span data-ttu-id="8e4c2-121">Interoperabilita modelů COM Upřesnit</span><span class="sxs-lookup"><span data-stu-id="8e4c2-121">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="8e4c2-122">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="8e4c2-122">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [<span data-ttu-id="8e4c2-123">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="8e4c2-123">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)  
 [<span data-ttu-id="8e4c2-124">Přizpůsobení standardních obálek</span><span class="sxs-lookup"><span data-stu-id="8e4c2-124">Customizing Standard Wrappers</span></span>](http://msdn.microsoft.com/en-us/c40d089b-6a3c-41b5-a20d-d760c215e49d)  
 [<span data-ttu-id="8e4c2-125">Postupy: přizpůsobení běhové obálky s možností</span><span class="sxs-lookup"><span data-stu-id="8e4c2-125">How to: Customize Runtime Callable Wrappers</span></span>](http://msdn.microsoft.com/en-us/4a4bb3da-4d60-4517-99f2-78d46a681732)
