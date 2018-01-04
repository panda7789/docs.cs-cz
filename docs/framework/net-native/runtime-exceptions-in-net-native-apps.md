---
title: "Výjimky za běhu v nativní aplikace .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cea4901eca45a4b02e3eeb9fa8a3ac2a9efa3484
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="3736b-102">Výjimky za běhu v nativní aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="3736b-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="3736b-103">Je důležité k testování verze sestavení vaší aplikace pro univerzální platformu Windows na jejich cílových platforem, protože konfigurace debug a release jsou úplně jiné.</span><span class="sxs-lookup"><span data-stu-id="3736b-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="3736b-104">Ve výchozím nastavení konfiguraci ladění používá na .NET Core runtime pro kompilaci aplikace, ale konfigurace verze používá .NET Native pro kompilaci vaší aplikace do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="3736b-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3736b-105">Informace o práci s [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky, které mohou stane se při testování verze aplikace, najdete v části "krok 4: vyřešit ručně chybí metadata: v [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md) tématu, a také [reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) a [ Odkaz na soubor konfigurace modulu runtime direktivy (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="3736b-105">For information on dealing with the [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see  "Step 4: Manually resolve missing metadata: in the [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="3736b-106">Ladění a sestavení pro vydání</span><span class="sxs-lookup"><span data-stu-id="3736b-106">Debug and release builds</span></span>  
 <span data-ttu-id="3736b-107">Při ladění sestavení provede proti na .NET Core runtime, nebyl kompilovaná nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="3736b-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="3736b-108">Díky tomu všechny služby normálně poskytované modul runtime, která je k dispozici pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3736b-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="3736b-109">Na druhé straně sestavení pro vydání zkompiluje do nativního kódu pro jeho cílových platforem, odebere většina závislostí na externí moduly runtime a knihovny a výraznou optimalizuje kód pro maximální výkon.</span><span class="sxs-lookup"><span data-stu-id="3736b-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="3736b-110">Když ladíte verze sestavení, které jsou kompilovaná pomocí .NET Native:</span><span class="sxs-lookup"><span data-stu-id="3736b-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
-   <span data-ttu-id="3736b-111">Použijete .NET nativní modul ladění, který se liší od normální .NET nástroje pro ladění.</span><span class="sxs-lookup"><span data-stu-id="3736b-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
-   <span data-ttu-id="3736b-112">Velikost vaší spustitelný soubor se snižuje co nejvíc.</span><span class="sxs-lookup"><span data-stu-id="3736b-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="3736b-113">Jedním ze způsobů, .NET Native snižuje velikost spustitelný soubor je výrazně ořezávání zprávy o výjimkách runtime, téma větší podrobněji v [zprávy o výjimkách Runtime](#Messages) části.</span><span class="sxs-lookup"><span data-stu-id="3736b-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
-   <span data-ttu-id="3736b-114">Váš kód je výraznou optimalizovaná.</span><span class="sxs-lookup"><span data-stu-id="3736b-114">Your code is heavily optimized.</span></span> <span data-ttu-id="3736b-115">To znamená, že vložené se používá, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="3736b-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="3736b-116">(Vložené přesune kód z externí rutiny do volání rutiny.)   Skutečnost, že .NET Native poskytuje specializované runtime a implementuje ovlivní smělého vložené zásobníku volání, která se zobrazuje při ladění.</span><span class="sxs-lookup"><span data-stu-id="3736b-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="3736b-117">Další informace najdete v tématu [zásobník volání modulu Runtime](#CallStack) části.</span><span class="sxs-lookup"><span data-stu-id="3736b-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3736b-118">Můžete řídit, jestli buildy debug a release jsou kompilovaná s .NET Native řetězu nástroj zaškrtnutí **kompilovat s .NET Native řetězu nástroj** pole.</span><span class="sxs-lookup"><span data-stu-id="3736b-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="3736b-119">Upozorňujeme však, že Windows Store vždy zkompilovat produkční verzi vaší aplikace pomocí .NET Native řetězu nástroj.</span><span class="sxs-lookup"><span data-stu-id="3736b-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a><span data-ttu-id="3736b-120">Zprávy o výjimkách modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3736b-120">Runtime exception messages</span></span>  
 <span data-ttu-id="3736b-121">Chcete-li minimalizovat velikost spustitelný soubor aplikace, .NET Native nezahrnuje celého textu zprávy výjimek.</span><span class="sxs-lookup"><span data-stu-id="3736b-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="3736b-122">V důsledku toho nemusí runtime výjimky vydané v sestavení pro vydání zobrazit celý text zprávy výjimek.</span><span class="sxs-lookup"><span data-stu-id="3736b-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="3736b-123">Místo toho může být podřetězce spolu s odkazem na použijte další informace.</span><span class="sxs-lookup"><span data-stu-id="3736b-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="3736b-124">Například může zobrazit informace o výjimce jako:</span><span class="sxs-lookup"><span data-stu-id="3736b-124">For example, the exception information may appear as:</span></span>  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="3736b-125">Pokud potřebujete zpráva o výjimce dokončení, spusťte ladění sestavení.</span><span class="sxs-lookup"><span data-stu-id="3736b-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="3736b-126">Předchozí informace o výjimce ze sestavení pro vydání může například vypadat takto v sestavení ladicí verze:</span><span class="sxs-lookup"><span data-stu-id="3736b-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a><span data-ttu-id="3736b-127">Zásobník volání modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3736b-127">Runtime call stack</span></span>  
 <span data-ttu-id="3736b-128">Z důvodu optimalizace vložené a dalších zásobníku volání zobrazí aplikací zkompilují řetězu .NET Native nástroj nemusí vám pomohou pro jednoznačnou identifikaci cestu k výjimku modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3736b-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="3736b-129">Pokud chcete získat úplné zásobníku, spusťte ladění sestavení místo.</span><span class="sxs-lookup"><span data-stu-id="3736b-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3736b-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="3736b-130">See Also</span></span>  
 [<span data-ttu-id="3736b-131">Ladění rozhraní .NET nativní univerzálních aplikací pro Windows</span><span class="sxs-lookup"><span data-stu-id="3736b-131">Debugging .NET Native Windows Universal Apps</span></span>](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx)  
 [<span data-ttu-id="3736b-132">Začínáme</span><span class="sxs-lookup"><span data-stu-id="3736b-132">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
